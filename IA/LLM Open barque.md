---
title: LLM Open barque 
layout: math 
nav_order: 9
parent: à l'IAttaque!
---


# LLM Open barque

Dans l'article précédent [IArmateurs](/IA/IArmateurs), j'expliquais les problématiques de coût. Utiliser le mode gratuit ne peut se faire qu'à travers les applications Web ou intégrées fournis par les IArmateurs mais aux prix d'accepter que nos données soient utilisées pour entraîner les modèles.

Donc, j'ai voulu essayer d'utiliser ma propre petite barque: des modèles open-weight sur des machines locales. Mais est ce que c'est utilisable? quelle puissance de machine faut-il? peut-on l'utiliser "à la place de" dans les outils de dev ? si non, faut-il developper ses propres clients (chatbot, visual studio extension)?  est-ce raisonnable?
Dans tous les cas, l'exercice est au moins interessant pour l'aspect pédagogique. 

## Les librairies ou frameworks

On peut faire tourner un modèle open-weight (le terme d'usage est 'inférer' à la place de 'faire tourner') dans Ollama, LM studio (avec ou sans GUI) , ou plus compliqué, llama.cpp. 

llama.cpp est une librairie c++ qui peut être chargée dans une application (à condition que le langage de l'application permette de charger la librairie C++ statique ou dll sous windows).
En c# et python, c'est le cas. Notons qu'avec Python, il existe d'autres librairies pour ça.

| Solution      | Usage "in-process" | Modèles supportés        | 
|---------------|-------------------|---------------------------|
| llama.cpp     | Oui               | Llama, autres GGML        |
| TensorFlow    | Oui               | Tous formats TF/Keras     |
| PyTorch       | Oui               | Tous formats Torch        |
| ONNX          | Oui               | Tous formats onnx         |

Chaque librairie a son format mais Il existe des outils pour convertir de nombreux modèles entre formats TensorFlow, PyTorch, ONNX, GGML, etc. :
- [ONNX model zoo/conversion docs](https://onnx.ai/)
- [llama.cpp conversion scripts](https://github.com/ggml-org/llama.cpp/tree/master/scripts)
- [TensorFlow TFLite conversion guide](https://www.tensorflow.org/lite/convert?hl=fr)

En dotnet, si on utilise Semantic kernel, le plus simple est d'installer **Ollama** en local sous docker. Evidemment, s'il s'agit d'une application desktop qu'on veut fournir aux collégues, le déploiment via un installateur ne s'en trouvera pas facilité. Mais dans un premier temps, pour mon usage personel, surtout pour experimenter les limites des 'petits' modèles, c'est plus simple. En fait, Ollama encapsule Llama.cpp en fournissant un service REST, comme celui pour OpenAI azure. Malheureusement, ce n'est pas le même protocol mais Semantic Kernel fournit plusieurs providers dont un pour Ollama. J'ai vu que le github contenant les sources llama.cpp fournissait aussi un serveur REST. Mais pas sur que ça soit très avancé.
Il y a aussi **LocalAI** à tester.

## Avec Ollama


```csharp
private bool ConfigureAzureOpenAI(IKernelBuilder kernelBuilder)
{
    var azureConfig = _options.AzureOpenAI;
    if (azureConfig != null)
    {
        kernelBuilder.AddAzureOpenAIChatCompletion(
            azureConfig.DeploymentName,
            azureConfig.Endpoint,
            azureConfig.ApiKey
          );
    }
    return azureConfig != null;
}
private bool ConfigureLocalOllamaLLM(IKernelBuilder kernelBuilder)
{
    kernelBuilder.Services.AddHttpClient();
    var localConfig = _options.LocalOllama;
    if (localConfig != null)
    {
        try
        {                           
            _logger.LogInformation("Configuring Ollama LLM at {Endpoint} with model {ModelId}",localConfig.Endpoint, localConfig.ModelId);
            var httpClient = new HttpClient(new MyHttpMessageHandler(_logger)) { Timeout = TimeSpan.FromSeconds(1000) };
            httpClient.BaseAddress = new Uri(_options.LocalOllama.Endpoint+"/v1");

            kernelBuilder.AddOpenAIChatCompletion(
                modelId: localConfig.ModelId,
                apiKey: "not-needed",                        
                httpClient: httpClient
            );
            return true;
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, "Failed to configure Ollama LLM");
            return false;
        }
    }
    else
    {
      return false;
    }
}
```

J'avais tenté lors d'une première approche d'utiliser le package *Microsoft.SemanticKernel.Connectors.Olama*. Erreur! les pluggins ( spécification OpenAI) ne sont pas du tout envoyés dans le contexte avec le prompt. J'ai cru à un problème avec le modèle testé (mistral-small3.2) alors qu'il fonctionne très bien (Ce qui n'empèche que peux de modèle supporte le tooling).



```csharp
private bool ConfigureLocalOllamaLLM_2(IKernelBuilder kernelBuilder)
{
    kernelBuilder.Services.AddHttpClient();
    var localConfig = _options.LocalOllama;
    if (localConfig != null )
    {      
        kernelBuilder.AddOllamaChatCompletion(
            modelId:localConfig.ModelId,                
            baseUrl: new Uri(localConfig.Endpoint)
        );
        return true;
    }
    else
    {
        return false;
    }                
}
```

Pour installer Ollama , depuis WSL ou n’importe quelle console Docker, il suffit d"exécuter :

```bash
docker run -d --name ollama -p 11434:11434 ollama/ollama
```

- -d : lance le conteneur en arrière-plan
- --name ollama : nomme le conteneur « ollama »
- -p 11434:11434 : ouvre le port 11434 pour utiliser l’API Ollama
- ollama/ollama : image officielle sur Docker Hub


Autre possibilité, le docker-compose (sous wsl):

```
version: '3.8'
services:
  ollama:
    image: ollama/ollama
    container_name: ollama
    ports:
      - "11434:11434"
    volumes:
      - /mnt/d/ollama:/root/.ollama
    restart: unless-stopped

```



```bash
docker ps
```
 "ollama"  doit apparaitre dans la liste.

---

Il faut rentrer dans le conteneur pour utiliser la CLI :

```bash
docker exec -it ollama bash
```

Et ensuite utiliser les commandes fourni par l'utilitaire ollama qui est présent dans l'image docker.

Pour afficher la liste des commandes:

```bash
 ollama -h
```


````
Large language model runner

Usage:
  ollama [flags]
  ollama [command]

Available Commands:
  serve       Start ollama
  create      Create a model
  show        Show information for a model
  run         Run a model
  stop        Stop a running model
  pull        Pull a model from a registry
  push        Push a model to a registry
  signin      Sign in to ollama.com
  signout     Sign out from ollama.com
  list        List models
  ps          List running models
  cp          Copy a model
  rm          Remove a model
  help        Help about any command

Flags:
  -h, --help      help for ollama
  -v, --version   Show version information
````



Ollama fournit differents modèles que l'on peut consulter sur le lien suivant [https://ollama.com/library](https://ollama.com/library).


Pour installer un model:
```bash
ollama pull llama3.2
```
Il est possible d'installer plusieurs modèles .



La commande suivante permet de voir l'ensemble des modèles installés en local.

```bash
 ollama list
```
 Et celle ci permet d'avoir des infos sur l'un des modèles installés
 ```bash
  ollama show llama3.2
```

L’API Ollama est accessible de l'exterieur du containeur via http://localhost:11434 (port par défault mais changeable au moment de créer le containeur en changeant le docker-compose.yml ou le paramètre -p 11434:11434 du docker run)

Quand on fait un appel à l’API, il suffit de spécifier le modèle via le champ model dans la requête.

Exemple avec curl  :

```bash
curl http://localhost:11434/api/generate -d '{
  "model": "mixtral",
  "prompt": "Comment se positionner en mer ?"
}'
```

Pour utiliser Llama :
```bash
curl http://localhost:11434/api/generate -d '{
  "model": "llama3.2",
  "prompt": "Comment se positionner en mer?"
}'
```



