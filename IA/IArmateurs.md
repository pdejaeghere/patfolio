---
title: IArmateurs 
layout: math 
nav_order: 8
parent: à l'IAttaque!
---


# IArmateurs 

Quels sont les IArmateurs détenant les grands navires LLM de pêche d'utilisateur ? pas simple de s'y retrouver, n'est ce pas?  

**Il faut distinguer les besoins :**
 - multimodal : capable de faire un peu de tout, génération de texte, d'image, de vidéo, de son (ChatGPT, Le Chat, Gemini, Copilot)
 - spécialisé dans le code (GitHub Copilot, Claude)
 - la vision (capable de décortiquer une image)
 - la génération d'images
 - la génération de vidéo
 - la génération de son
 - la génération d'embeddings (pour les RAG)
 - certains offrent des fonctionnalités natives comme la recherche dans le Web
 - certains donnent la possibilité d'être étendus via des plugins (code natif, spécification OpenAI ou en communiquant avec des serveurs MCP, ex : [playwright](https://github.com/microsoft/playwright-mcp)). 

**Il faut distinguer la manière dont les outils sont fournis :**
 - Chatbot sur le web : ChatGPT, Le Chat de Mistral, Gemini dans Google
 - Les chatbots intégrés dans le navigateur : Copilot dans Edge
 - Les chatbots intégrés dans les OS (Gemini sur Android, Copilot dans Windows, panel Edge, Copilot dans Edge ou Office, Gemini sur nos smartphones)
 - Les agents de développement dans les IDE : GitHub Copilot dans VSCode ou Visual Studio
 - Les outils autonomes avec une UI ou en ligne de commande (Claude Desktop)
 - Via des API REST nécessitant une clé API si l'infra est fournie sur le cloud en B2B ou une infra locale pour intégrer une fonctionnalité LLM au sein d'une application
     - soit en tant que développeur pour une application à fournir à des clients ou des usagers de l'entreprise
     - soit en tant qu'utilisateur (ex : OnlyOffice permet de personnaliser le correcteur en fournissant un accès vers un modèle)

    
<div>
<a href="configuration IA onlyoffice.png"><img src="configuration IA onlyoffice.png"  width="200"/></a>
</div>

**Concernant les API REST, il faut distinguer l'infra du modèle, sachant que les deux peuvent être proposés par le même fournisseur (éditeur) :**
 - ChatGPT fournit son modèle propriétaire ainsi que l'infra
 - Idem pour AWS
 - Microsoft fournit l'infra pour faire tourner des modèles ChatGPT et Claude
 - Mistral fournit le modèle et l'infra, mais l'infra utilise en fait le cloud Azure (ils souhaitent développer leur propre datacenter en Suède pour être complètement indépendants des États-Unis, souverains suivant le terme consacré)
 - fournisseur d'infrastructures cloud dédiées IA : ex **SiliconFlow**, qui fait tourner des modèles open source mais facture au token (à priori moins cher que les modèles propriétaires)
 - En ayant sa propre infra en utilisant LMStudio, ollama, en tant que service tournant sur un serveur, déployée ou non en tant que container Docker, sur le cloud ou on premise, ou même sur son PC local (en tenant compte de la capacité machine suivant la complexité du modèle)
 - Notons aussi qu'on peut embarquer directement un 'petit' modèle open source via des API C++, Python au sein du process de son application (besoin développeur : ex llama.cpp)


**Bien entendu, il faut aussi distinguer les modèles :**
- il y a les grands modèles propriétaires (ChatGPT)
- il y a les modèles open source des éditeurs connus (Mistral, Meta)
- On peut distinguer aussi les pays (modèles développés par la Chine ou d'autres pays de l'Asie, les États-Unis, l'Europe, le Canada)
- il y a de nombreux modèles développés par de petites équipes ou des centres de recherche ; parfois, ce sont des modèles fine-tunés à partir de modèles fournis par Meta ou Mistral.
- Et puis chaque éditeur propose une palanquée de modèles plus ou moins récents, plus ou moins gourmands.

**Enfin, il faut distinguer le mode de facturation :**
 - Gratuit avec une limite de nombre de requêtes ou de tokens
 - Un mode abonnement quand il s'agit d'utiliser les outils « prêts à l’emploi »
 - Pour le mode API, le prix se compte en millions de tokens sachant que:
   - ça dépend du modèle (un modèle d'embeddings sera moins cher qu'un modèle de génération de texte qui lui-même sera plus ou moins cher en fonction de ses capacités en nombre de tokens, raisonnements, etc.)
   - on paye les tokens en entrée (contexte + prompt) et les tokens en sortie (réponse)
   - le nombre de tokens en réponse peut différer d'un modèle à l'autre (ex : un LLM peut être moins cher qu'un autre mais s'il renvoie systématiquement plus de tokens que son concurrent, comment affirmer qu'il est moins cher ?).


Je souhaitais proposer un tableau de synthèse au moins pour les offres des fournisseurs les plus en vue.

***J'ai donc tenté de poser directement la question aux intéressés, les LLMs !***

J'avoue avoir eu quelques difficultés pour obtenir un tableau suffisamment synthétique et contenant des informations exactes. En effet, malgré un prompt que j'ai essayé de rendre plutôt précis, les résultats provenant de ChatGPT, Mistral ou Gemini étaient  bourrés d'imprécisions ou d'erreurs ! Les liens demandés n'étaint pas forcément à jour (obsolètes ou erronés) et les tarifs inexacts voire inventés.

Voilà un cas où les LLM m'ont fait perdre pas mal eu temps (tant que ce n'est pas de l'argent 😄) !

```
Crée un tableau complet en Markdown (.md) des principaux LLM et assistants IA en 2026, incluant ces colonnes :

- Produit
- Propriétaire / éditeur
- Outils finaux (web, IDE, Office…)
- Modèles proposés ou utilisés : Les plus récents seulement et un lien vers la page officielle
- Fournisseur du modèle
- Type de collaboration / partenariat
- Hébergement (cloud, local…)
- Modalité du mode gratuit si existe (quelle est la limite en nombre de requêtes ou de token ?)
- Page officielle concernant la tarification sous forme [tarif] (lien)
- Un point fort et un point faible

Inclue tous les grands acteurs : OpenAI (ChatGPT), Anthropic (Claude), Google (Gemini), Microsoft (Copilot), GitHub Copilot, Mistral (Le Chat), Meta (LLaMA), Perplexity, Grok/X, DeepSeek.
````

Face à ça, s'en est suivi le fameux ping-pong pour essayer d'obtenir ce que je souhaitais. Vous connaissez la programmation... J'ai déjà évoqué la notion de méta-programmation. Eh bien, avec les LLM, c'est un peu la même chose : on peut leur fournir le prompt mais on peut aussi leur demander de rédiger eux-mêmes le prompt qu'ils auraient bien voulu avoir pour éviter les erreurs et autres hallucinations. L'idée aussi est de pourvoir réitérer la demande en une seule passe sans devoir rejouer au ping-pong et que le résultat soit relativement déterministe (un peu utopique quand on sait que les réponses reposent sur des probabilités).

Voici ce que j'ai obtenu :


````
# PROMPT COMPLET – Benchmark LLM 2026 en Markdown

## Objectif
Créer un **tableau comparatif exhaustif en Markdown (.md)** des principaux LLM et assistants IA mondiaux en 2026.

## Portée
Inclure :
- Acteurs USA, Europe et Chine
- Modèles open-weight significatifs
- Assistants grand public et B2B
- Fournisseurs API cloud
- Acteurs spécialisés code, recherche et multimodal

Ne pas limiter la liste aux noms donnés. Ajouter **tout acteur majeur mondial** si :
- Modèle classé SOTA
- Adoption massive en entreprise
- Forte présence géographique
- Impact stratégique (prix, open-weight, intégrations)

## Acteurs minimum à inclure
OpenAI (ChatGPT), Anthropic (Claude), Google (Gemini), Microsoft (Copilot), GitHub Copilot, Mistral (Le Chat), Meta (LLaMA), Perplexity, xAI (Grok), DeepSeek, Alibaba (Qwen)

## Colonnes du tableau (obligatoires)
- Produit  
- Propriétaire / éditeur  
- Pays d’origine  
- Outils finaux (Web, IDE, Office, API…)  
- Modèles les plus récents (avec lien officiel vers documentation)  
- Fournisseur du modèle  
- Type de collaboration / partenariat  
- Hébergement (Cloud, local, hybride)  
- Contexte maximal (tokens)  
- Mode gratuit (limites précises)  
- Mode abonnement (€/mois)  
- Facturation token API (€/1M tokens input/output)  
- Page officielle tarification  
- Point fort  
- Point faible

## Règles strictes
1. Vérifier les modèles sur la **documentation officielle** de chaque fournisseur.
2. Indiquer uniquement les modèles **actifs et récents**.
3. Exclure les modèles dépréciés ou en fin de vie.
4. Fournir le **lien exact vers la documentation officielle**. Le lien doit être de type [page officielle](lien http).
5. Fournir le **lien exact vers la page de tarification officielle**. [tarif](lien http).
6. Ne pas inventer de prix ou de versions.
7. Si une donnée n’est pas confirmée officiellement, écrire **"Non confirmé officiellement"**.
8. Indiquer la date de dernière mise à jour si possible.
9. Si navigation web non disponible, indiquer explicitement que **l’information peut être obsolète**.

## Sortie
- **Format Markdown** uniquement
- Tableau prêt à copier-coller avec toutes les colonnes
- Priorité : exactitude et vérifiabilité

````

ChatGpt, en mode gratuit, n'a pas réussi vraiment à récupérer l'information de differentes sources Web :

*Je n’ai pas accédé (via navigation) à chaque documentation officielle demandée pour tous les modèles et fournisseurs mentionnés. Certaines informations (contextes, prix, modes, limites gratuites, liens directs) proviennent de sources secondaires (comparateurs, blogs), ce qui peut être obsolète ou approximatif par rapport aux pages officielles.
Les champs marqués Non confirmé officiellement doivent être validés avec la documentation officielle du fournisseur.*


Par contre, Mistral s'en est bien sorti ! Cocorico!  
De là à certifier que toutes les informations sont exactes.... en tout cas les liens fonctionnent, c'est déjà ça.

## Réponse du Chat de Mistral

| Produit                | Propriétaire/Éditeur | Pays d’origine | Outils finaux (Web, IDE, Office, API…) | Modèles récents (lien doc) | Fournisseur du modèle | Type de collaboration/partenariat | Hébergement | Contexte maximal (tokens) | Mode gratuit (limites) | Mode abonnement (€/mois) | Facturation token API (€/1M tokens input/output) | Page officielle tarification | Point fort | Point faible |
|------------------------|----------------------|----------------|-----------------------------------------|-----------------------------|-----------------------|-----------------------------------|------------|---------------------------|--------------------------|----------------------------|--------------------------------------------------|-------------------------------|------------|--------------|
| **ChatGPT**           | OpenAI               | USA            | Web, Mobile, API, Plugins, GPT Store    | [GPT-5.2](https://help.openai.com/en/articles/9624314-model-release-notes) | OpenAI | Partenariats avec Microsoft, intégration Azure | Cloud (Azure) | 256k (128k input/128k output) | Oui (modèle de base, limites de requêtes) | Plus: 20$/mois, Pro: 200$/mois | GPT-5.2: ~1.25€/10€ input/output | [Tarifs OpenAI](https://platform.openai.com/docs/pricing) | Raisonnement avancé, intégrations riches | Coût élevé pour usage intensif, dépendance à Azure |
| **Claude**            | Anthropic            | USA            | Web, API, AWS Bedrock, Google Vertex   | [Opus 4.6](https://platform.claude.com/docs/en/release-notes/overview) | Anthropic | Partenariats avec AWS, Google, Microsoft | Cloud (AWS/Google) | 1M | Oui (limites de tokens/jour) | Pro: 20$/mois, Max: 100$/mois | Opus 4.6: 5$/25$ input/output | [Tarifs Claude](https://platform.claude.com/docs/en/about-claude/pricing) | Sécurité, contexte très long | Prix élevé pour les modèles premium |
| **Gemini**            | Google               | USA            | Web, Google Workspace, API, Android     | [Gemini 3 Pro](https://ai.google.dev/gemini-api/docs/gemini-3) | Google | Intégration native avec Google Cloud/Workspace | Cloud (Google) | 1M | Oui (limites sur Gemini 3 Flash) | Pro: 19.99$/mois | Gemini 3 Pro: 2$/12$ input/output | [Tarifs Gemini](https://ai.google.dev/gemini-api/docs/pricing) | Multimodalité, intégration Google | Complexité des tarifs pour les gros volumes |
| **Microsoft Copilot** | Microsoft            | USA            | Office 365, Teams, Edge, API           | [GPT-5.2](https://learn.microsoft.com/en-us/copilot/microsoft-365/release-notes) | OpenAI/Microsoft | Intégration native avec Microsoft 365 | Cloud (Azure) | Selon modèle sous-jacent | Non (essai gratuit limité) | Business: 21$/utilisateur/mois, Enterprise: 30$/utilisateur/mois | Inclus dans abonnement | [Tarifs Copilot](https://www.microsoft.com/en-us/microsoft-365-copilot/pricing) | Intégration Office 365 | Coût par utilisateur élevé, dépendance à l’écosystème Microsoft |
| **GitHub Copilot**    | GitHub (Microsoft)   | USA            | VS Code, JetBrains, CLI, Web            | [GPT-5.2-Codex](https://docs.github.com/en/copilot/concepts/billing/individual-plans) | OpenAI/Microsoft | Intégration native avec GitHub | Cloud (Azure) | Selon modèle | Oui (2000 suggestions/mois) | Pro: 10$/mois, Pro+: 39$/mois | Selon modèle (ex: 0.00001$/token unit) | [Tarifs GitHub Copilot](https://github.com/features/copilot/plans) | Optimisé pour le code, intégration IDE | Coût supplémentaire pour les modèles premium |
| **Le Chat**           | Mistral AI           | France         | Web, Mobile, API                        | [Mistral Large 3](https://mistral.ai/news/mistral-3) | Mistral AI | Partenariats avec Microsoft Azure, Hugging Face | Cloud/On-premise | Jusqu’à 1M | Oui (limites généreuses) | Pro: 14.99$/mois | Mistral Large 3: ~0.28$/0.42$ input/output | [Tarifs Mistral](https://mistral.ai/pricing) | Open-weight, rapidité, respect vie privée | Moins connu hors Europe |
| **LLaMA**             | Meta                 | USA            | API, Hugging Face, Cloud Partners      | [Llama 4 Maverick](https://ai.meta.com/blog/llama-4-multimodal-intelligence/) | Meta | Open-weight, partenariats avec AWS, Azure, Hugging Face | Cloud/On-premise | Jusqu’à 10M | Oui (accès libre aux poids) | Selon hébergeur | Llama 4 Maverick: ~0.19$/1M tokens (blended) | [Tarifs Llama](https://ai.meta.com/blog/meta-llama-3-1/) | Open-source, contexte ultra-long | Support limité pour les petits acteurs |
| **Perplexity**        | Perplexity AI        | USA            | Web, Mobile, API                        | [Sonar Pro](https://docs.perplexity.ai/docs/getting-started/pricing) | Perplexity/Partenaires | Agrégation de modèles (OpenAI, Anthropic, etc.) | Cloud | Selon modèle | Oui (limites de requêtes) | Pro: 20$/mois, Enterprise: 40$/utilisateur/mois | Selon modèle (ex: Sonar Pro: 1$/1M tokens) | [Tarifs Perplexity](https://www.perplexity.ai/enterprise/pricing) | Recherche sourcée, multi-modèles | Moins adapté à la génération créative |
| **Grok**              | xAI                  | USA            | Web, API, X (Twitter)                   | [Grok 4.1 Fast](https://docs.x.ai/developers/models) | xAI | Intégration avec X (Twitter) | Cloud | 2M | Oui (limites sur X Premium) | SuperGrok: 30$/mois | Grok 4.1 Fast: 0.20$/0.50$ input/output | [Tarifs Grok](https://x.ai/api) | Prix très compétitifs, accès aux données X | Moins mature que les leaders |
| **DeepSeek**          | DeepSeek             | Chine           | Web, API, Hugging Face                  | [DeepSeek V3.2](https://api-docs.deepseek.com/quick_start/pricing) | DeepSeek | Open-weight, partenariats avec Azure, Hugging Face | Cloud/On-premise | 128k | Oui (accès libre) | Selon usage API | DeepSeek V3.2: 0.28$/0.42$ input/output | [Tarifs DeepSeek](https://api-docs.deepseek.com/quick_start/pricing-details-usd) | Très économique, open-weight | Moins connu en Occident |


## Utilisation des modèles open sources

Finalement, le plus simple, c'est d'essayer d'utiliser sa propre petite barque: un modèle open source en local.
On peut le faire tourner (inférer) dans Ollama, LM studio (avec ou sans GUI) , ou plus compliqué, llama.cpp. 

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

### Avec Ollama


``` C#
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
````

Pour installer Ollama , depuis WSL ou n’importe quelle console Docker, il suffit d"exécuter :

```bash
docker run -d --name ollama -p 11434:11434 ollama/ollama
```

- -d : lance le conteneur en arrière-plan
- --name ollama : nomme le conteneur « ollama »
- -p 11434:11434 : ouvre le port 11434 pour utiliser l’API Ollama
- ollama/ollama : image officielle sur Docker Hub


Autre possibilité, le docker-compose :

```
version: '3.8'
services:
  ollama:
    image: ollama/ollama
    container_name: ollama
    ports:
      - "11434:11434"
    volumes:
      - /d/ollama:/root/.ollama
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



