---
title: IArmateurs 
layout: math 
nav_order: 8
parent: à l'IAttaque!
---


# IArmateurs 


## Problématique

Quels sont les IArmateurs qui détiennent les grands navires LLM pour la pêche aux utilisateurs ?
Entre modèles propriétaires, offres cloud, API REST et modèles open-weight, il n’est pas toujours simple de s’y retrouver, n'est-ce pas?

Lorsqu’on travaille dans une grande entreprise et que l’on utilise Azure OpenAI avec un modèle comme GPT-4.1, la question du coût est souvent peu visible pour l’utilisateur final. Les dépenses sont mutualisées, budgétées et intégrées dans une stratégie globale IT, surtout lorsque le service est mis à disposition comme un outil stratégique à exploiter.

En revanche, dans un contexte personnel, startup ou B2B — notamment lorsqu’il s’agit de développer une application reposant sur des API REST LLM — la maîtrise du coût au token devient essentielle. Il faut l’anticiper, le modéliser et le surveiller afin d’éviter des dérives budgétaires et garantir un véritable retour sur investissement.

Si l’on envisage des modèles open-weight, il faut s’assurer qu’ils répondent aux besoins fonctionnels (taille de contexte, tool calling, multimodalité : texte, image, audio…) et que l’infrastructure soit dimensionnée en conséquence (CPU, GPU, mémoire, stockage), en tenant compte du volume et du débit des requêtes attendues.


**Il faut donc distinguer les besoins :**
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

**Il faut distinguer le mode de facturation :**
 - Gratuit avec une limite de nombre de requêtes ou de tokens
 - Un mode abonnement quand il s'agit d'utiliser les outils « prêts à l’emploi »
 - Pour le mode API, le prix se compte en millions de tokens sachant que:
   - ça dépend du modèle (un modèle d'embeddings sera moins cher qu'un modèle de génération de texte qui lui-même sera plus ou moins cher en fonction de ses capacités en nombre de tokens, raisonnements, etc.)
   - on paye les tokens en entrée (contexte + prompt) et les tokens en sortie (réponse)
   - le nombre de tokens en réponse peut différer d'un modèle à l'autre (ex : un LLM peut être moins cher qu'un autre mais s'il renvoie systématiquement plus de tokens que son concurrent, comment affirmer qu'il est moins cher ?).

**Enfin, il faut aussi prendre en compte la gouvernance des données :**
où vont-elles, comment sont-elles protégées, qui peut y accéder, et quelles assurances avons-nous que les informations sensibles ne fuitent pas ? Dans une grande entreprise utilisant Azure OpenAI ou d’autres clouds, les données sont souvent chiffrées et stockées sur des serveurs centralisés, mais il est essentiel de vérifier les politiques de rétention, la conformité RGPD/CCPA et les certifications de sécurité (ISO, SOC2…).

Pour une application personnelle ou B2B exploitant des API REST LLM, la gouvernance devient encore plus critique. Il faut savoir si les prompts et réponses sont conservés par le fournisseur, si les plugins ou extensions transmettent des informations vers d’autres serveurs, et si l’on peut isoler les données confidentielles sur un modèle self‑hosted ou on‑premise.

En somme, la gouvernance ne se limite pas à protéger les données : elle influence directement le choix du modèle et de l’infrastructure, car un LLM peut être certe performant mais peut aussi transformer des informations sensibles en risque juridique et stratégique.


## Etablir une synthèse

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

Face à ça, s'en est suivi le fameux ping-pong pour essayer d'obtenir ce que je souhaitais. Vous connaissez la programmation... J'ai déjà évoqué la notion de méta-programmation. Eh bien, avec les LLM, c'est un peu la même chose : on peut leur fournir le prompt mais on peut aussi leur demander de corriger le prompt qu'ils auraient bien voulu avoir pour éviter les erreurs et autres hallucinations, du meta-prompting. L'idée est de pourvoir réitérer la demande en une seule passe sans devoir rejouer au ping-pong et que le résultat soit relativement déterministe (un peu utopique quand on sait que les réponses reposent sur des probabilités).

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

## Synthèse du Chat de Mistral

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




## Estimation du coût 

Sauf erreur de ma part, si l'on compare l'abonnement qui n'est pas trop cher pour une personne au coût de l'usage de l'API REST, il n'y a pas photo !

Imaginons un chatbot développé pour un usage personnel qui envoie l'historique complet à chaque question de l'utilisateur afin de donner le contexte complet au LLM.
J'ai écrit un petit programme en Python afin d'évaluer le coût de ce chatbot. Même si le prix à l'input est moins important que le prix à l'output, plus la conversation ping‑pong dure, plus l'historique grossit, l'input cumulé devient conséquent et, comme dit l'adage, les petites gouttes font les grandes rivières ; le prix s'envole.

```
Tour 1 :
(input1) + (output1)

Tour 2 :
(input1 + output1 + input2) + (output2)

Tour 3 :
(input1 + output1 + input2 + output2 + input3) + (output3)
````

La somme croît quadratiquement :  𝑂(𝑛^2)

Ainsi, pour une conversation de 35 tours, avec un prix de 1.6 en input et de 6.67 en output, 1374 tokens en input et 50679 tokens en output induisent 2 468 564 tokens en input cumulés.

=== Résultat Simulation ===
{'total_input_tokens': 1374, 'total_input_tokens_cumulated': 1243445, 'total_output_tokens': 50679, 'total_tokens': 1294124, 'total_pingpong': 35, 'estimated_cost': 2.453406}

Évidemment 2 euros, ça ne semble pas énorme pris dans le budget d'une entreprise, mais imaginons cela plusieurs fois par jour, multiplié par le nombre d'utilisateurs, ça grossit très vite.
2.45 * 20 jours * 20 utilisateurs = 980 euros pour le mois

[Source llm_cost_simulation](https://github.com/pdejaeghere/ForLearningMachineLearning/blob/master/Python/llm_cost_simulation.py)

Évidemment, il y a des stratégies à mettre en place. On peut éviter d'envoyer l'historique complet, ou bien envoyer un résumé de l'historique. Mais quand c'est combiné à un RAG, le résumé peut faire perdre des informations contenues dans les « chunks ».

Bref, je ne sais pas trop si j'ai loupé quelque chose, mais, pour un usage personnel, il vaut mieux considérer l'usage d'un modèle open weight sur sa propre infra, ou alors d'utiliser les outils proposés en mode gratuit, mais surtout pas le mode API REST !
Il y a quand même un gros problème. Les modèles open weight sont limités sur une machine moyenne, intel i9, 32 Go, GPU 4 Go. D'autre part, il semble, d'après mes premiers tests, que les modèles open weight ne supportent pas la possibilité d'appeler des fonctions (code interne ou MCP).
Je proposerai une étude plus complète dans le prochain article...




