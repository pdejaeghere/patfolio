---
title: Différents axes
layout: math 
nav_order: 1
parent: IArmateurs 
---


# Différents axes 


**Il faut donc distinguer les besoins :**
 - multimodal : capable de faire un peu de tout, génération de texte, d'image, de vidéo, de son (ChatGPT, Le Chat, Gemini, Copilot)
 - spécialisé dans le code (GitHub Copilot, Claude)
 - la vision (capable de décortiquer une image)
 - la génération d'images
 - la génération de vidéo
 - la génération de son
 - la génération d'embeddings (pour les RAG)
 - le type d'utilisation ( Frontal Web, intégration dans des applications, developpement d'une application utilisant un modèle LLM)
 

**Il faut distinguer la manière dont les outils sont fournis :**
 - Chatbot sur le web : ChatGPT, Le Chat de Mistral, Gemini dans Google
 - Les chatbots intégrés dans le navigateur : Copilot dans Edge
 - Les chatbots intégrés dans les OS (Gemini sur Android, Copilot dans Windows, panel Edge, Copilot dans Edge ou Office, Gemini sur nos smartphones)
 - Les agents de développement dans les IDE : GitHub Copilot dans VSCode ou Visual Studio
 - Les outils autonomes avec une UI ou en ligne de commande (Claude Desktop)
-  Avec des fonctionnalités embarquées comme la recherche dans le Web 
 - Ou plus généralement, avec la possibilité d'être étendus via des outils (Tools  MCP, ex : [playwright](https://github.com/microsoft/playwright-mcp)). 

 - Via des API REST nécessitant une clé API si l'infra est fournie sur le cloud en B2B ou une infra locale pour intégrer une fonctionnalité LLM au sein d'une application
     - soit en tant que développeur pour une application à fournir à des clients ou des usagers de l'entreprise 
     - soit en tant qu'utilisateur (ex : OnlyOffice permet de personnaliser le correcteur en fournissant un accès vers un modèle)
    

**Concernant les API REST, il faut distinguer l'infra du modèle, sachant que les deux peuvent être proposés par le même fournisseur (éditeur) :**
 - OpenAI fournit ses modèles propriétaires GPT-x et aussi l'infra pour ses services REST  (même s'il s'agit derrière de Azure, AWS, Oracle ...)
 - Mistral fournit le modèle et l'infra, mais l'infra utilise en fait le cloud Azure (ils souhaitent développer leur propre datacenter en Suède pour être complètement indépendants des États-Unis, souverains suivant le terme consacré)
 
 - AWS founit bien évidemment l'infrastructure Cloud mais aussi un service Amazon Bedrock qui peut faire tourner les modèles de differents fournisseurs (OpenAI, Anthropic, Mistral ...) mais aussi ses propres modèles Nova, Titan.
 - Idem, Microsoft fournit l'infra Azure (des VM, du kubernates) mais aussi un service OpenAI Service pour faire tourner les modèles OpenAI ainsi qu'un autre service AI Foundry pour faire tourner des modèles open-weight ou d'autres fournisseurs. 

 - fournisseur d'infrastructures cloud dédiées IA : ex **SiliconFlow**, qui fait tourner des modèles open-weight mais facture au token (à priori moins cher que les modèles propriétaires)
 - En ayant sa propre infra en utilisant LMStudio, ollama, en tant que service tournant sur un serveur, déployée ou non en tant que container Docker, sur le cloud ou on premise, ou même sur son PC local (en tenant compte de la capacité machine suivant la complexité du modèle)
 - Notons aussi qu'on peut embarquer directement un modèle open-weight via des API C++ ou Python au sein du process de son application (besoin développeur : ex llama.cpp, transformers, PyTorch, Tensorflow...)


**Bien entendu, il faut aussi distinguer les modèles :**
- il y a les grands modèles propriétaires des fournisseurs OpenAI, Anthropic, Google, Mistral...
- il y a les modèles open weight des fournisseurs Mistral, Meta...
- On peut distinguer aussi les pays (modèles développés par la Chine ou d'autres pays de l'Asie, les États-Unis, l'Europe, le Canada)
- il y a de nombreux modèles développés par de petites équipes ou des centres de recherche ; parfois, ce sont des modèles fine-tunés à partir de modèles fournis par Meta ou Mistral (voir [Hugging Face](https://huggingface.co/) )
- Et puis chaque éditeur propose une palanquée de modèles plus ou moins récents, plus ou moins gourmands.
-  Les modèles peuvent ou non supporter le tooling (spécification OpenAI). On injecte dans le contexte du prompt des spécifications de fonctions et le LLM est capable de décider si il y a besoin de les appeller en fonction du prompt envoyé. En retour de la réponse du LLM, l'outil ou le framework client intercepte les appels émis de manière non ambigue pour executer le code . Donc ce code peut être un code natif à l'application ou l'appel d'un serveur MCP mais c'est bien effectué par l'application cliente.  Par contre, si c'est supporté par tous grands modèles propriétaires, c'est rarement le cas des modèles open-weight.

**Il faut distinguer le mode de facturation :**
 - Gratuit avec une limite de nombre de requêtes ou de tokens (quand c'est gratuit, c'est que vos données sont le produit )
 - Un mode abonnement quand il s'agit d'utiliser les outils « prêts à l’emploi »
 - Pour le mode API, le modèle de payement n'est jamais fourni sous forme d'abonnement mais aux nombres de token entrant et sortant. Le prix se compte en millions de tokens sachant que:
   - ça dépend du modèle (un modèle d'embeddings sera moins cher qu'un modèle de génération de texte qui lui-même sera plus ou moins cher en fonction de ses capacités en nombre de tokens, raisonnements, etc.)
   - on paye les tokens en entrée (contexte + prompt) et les tokens en sortie (réponse)
   - le nombre de tokens en réponse peut différer d'un modèle à l'autre (ex : un LLM peut être moins cher qu'un autre mais s'il renvoie systématiquement plus de tokens que son concurrent, comment affirmer qu'il est moins cher ?).

Je détaille plus loin le risque avec le mode API.


**Enfin, il faut aussi prendre en compte la gouvernance des données :**
où vont-elles, comment sont-elles protégées, qui peut y accéder, et quelles assurances avons-nous que les informations sensibles ne fuitent pas ? Dans une grande entreprise utilisant Azure OpenAI ou d’autres clouds, les données sont souvent chiffrées et stockées sur des serveurs centralisés, mais il est essentiel de vérifier les politiques de rétention, la conformité RGPD/CCPA et les certifications de sécurité (ISO, SOC2…).

Pour une application personnelle ou B2B exploitant des API REST LLM, la gouvernance devient encore plus critique. Il faut savoir si les prompts et réponses sont conservés par le fournisseur, si les plugins ou extensions transmettent des informations vers d’autres serveurs, et si l’on peut isoler les données confidentielles sur un modèle self‑hosted ou on‑premise.

En somme, la gouvernance ne se limite pas à protéger les données : elle influence directement le choix du modèle et de l’infrastructure, car un LLM peut être certe performant mais peut aussi transformer des informations sensibles en risque juridique et stratégique.







