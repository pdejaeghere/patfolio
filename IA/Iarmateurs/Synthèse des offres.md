---
title: Synthèse des offres 
layout: math 
nav_order: 2
parent: IArmateurs
---


# Synthèse des offres


## Etablir la synthèse

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
OpenAI (ChatGPT), Anthropic (Claude), Google (Gemini), Microsoft (Copilot),  GitHub Copilot, AWS(Nova, Titan), Mistral (Le Chat), Meta (LLaMA), Perplexity, xAI (Grok), DeepSeek, Alibaba (Qwen)

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
- Gouvernance des données et protection
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


<table>
        <thead>
            <tr>
                <th>Produit</th>
                <th>Propriétaire</th>
                <th>Pays</th>
                <th>Outils finaux</th>
                <th>Modèles récents</th>
                <th>Hébergement</th>
                <th>Contexte max (tokens)</th>
                <th>Gratuit (limites)</th>
                <th>Abonnement (€/mois)</th>
                <th>API (€/1M tokens in/out)</th>
                <th>Tarification</th>
                <th>Gouvernance/Protection</th>
                <th>Point fort</th>
                <th>Point faible</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>ChatGPT</td>
                <td>OpenAI</td>
                <td>USA</td>
                <td>Web, API, VS Code, Office, Slack, Azure</td>
                <td><a href="https://openai.com/index/introducing-gpt-5-2/" target="_blank">GPT-5.2 Instant/Thinking</a></td>
                <td>Cloud/Azure</td>
                <td>2M</td>
                <td>50 messages/jour (GPT-5.1)</td>
                <td>Plus: 20$ ; Enterprise: sur devis</td>
                <td>Input: 1.25€/1M, Output: 3.75€/1M</td>
                <td><a href="https://openai.com/api/pricing/" target="_blank">OpenAI Pricing</a></td>
                <td>Opt-out entraînement, RGPD/CCPA</td>
                <td>Meilleure intelligence générale</td>
                <td>Coût élevé, latence occasionnelle</td>
            </tr>
            <tr>
                <td>Claude</td>
                <td>Anthropic</td>
                <td>USA</td>
                <td>Web, API, AWS Bedrock, Vertex AI, Slack</td>
                <td><a href="https://platform.claude.com/docs/en/about-claude/models/overview" target="_blank">Opus 4.6, Sonnet 4.5</a></td>
                <td>Cloud/AWS/Vertex</td>
                <td>1M</td>
                <td>50 requêtes/jour (Opus 4.5)</td>
                <td>Pro: 17$ ; Max: 100$</td>
                <td>Input: 5€/1M, Output: 25€/1M</td>
                <td><a href="https://platform.claude.com/docs/en/about-claude/pricing" target="_blank">Anthropic Pricing</a></td>
                <td>Constitutional AI, prompt caching</td>
                <td>Sécurité, faible hallucination</td>
                <td>Prix outputs, latence mode "fast"</td>
            </tr>
            <tr>
                <td>Gemini</td>
                <td>Google</td>
                <td>USA</td>
                <td>Web, API, Workspace, Android, Vertex AI</td>
                <td><a href="https://ai.google.dev/gemini-api/docs/models" target="_blank">Gemini 3.1 Pro, Flash-Lite</a></td>
                <td>Cloud/Vertex</td>
                <td>1M</td>
                <td>Flash-Lite gratuit (limites RPM)</td>
                <td>Pro: 19.99$ ; Enterprise: sur devis</td>
                <td>Input: 1.25€/1M, Output: 10€/1M (Pro)</td>
                <td><a href="https://ai.google.dev/gemini-api/docs/pricing" target="_blank">Gemini Pricing</a></td>
                <td>RGPD, résidence données</td>
                <td>Multimodal, recherche web native</td>
                <td>Tarification complexe</td>
            </tr>
            <tr>
                <td>Microsoft Copilot</td>
                <td>Microsoft</td>
                <td>USA</td>
                <td>Office 365, Windows, Teams, Azure</td>
                <td>GPT-5.2 (via Azure OpenAI)</td>
                <td>Cloud/Azure</td>
                <td>2M</td>
                <td>Fonctionnalités limitées sans 365</td>
                <td>Business: 21$ ; Enterprise: 30$/user</td>
                <td>Intégré aux abonnements 365</td>
                <td><a href="https://www.microsoft.com/en-us/microsoft-365-copilot/pricing" target="_blank">Copilot Pricing</a></td>
                <td>ISO 27001, chiffrement</td>
                <td>Intégration Microsoft 365</td>
                <td>Dépendance écosystème Microsoft</td>
            </tr>
            <tr>
                <td>Le Chat</td>
                <td>Mistral AI</td>
                <td>France</td>
                <td>Web, API, Mistral Studio, NVIDIA</td>
                <td><a href="https://mistral.ai/news/mistral-3" target="_blank">Mistral Large 3, Devstral 2</a></td>
                <td>Cloud/On-premise</td>
                <td>1M</td>
                <td>Modèles Small/Medium gratuits</td>
                <td>Pro: 14.99€ ; Team/Enterprise: sur devis</td>
                <td>Input: 2€/1M, Output: 6€/1M</td>
                <td><a href="https://mistral.ai/pricing" target="_blank">Mistral Pricing</a></td>
                <td>Open-weight (Apache 2.0), hébergement EU</td>
                <td>Latence faible, prix compétitifs</td>
                <td>Écosystème partenaire en développement</td>
            </tr>      
            <tr>
                <td>AWS Bedrock (Nova/Titan)</td>
                <td>Amazon Web Services</td>
                <td>USA</td>
                <td>API, AWS Console, SageMaker, Lambda, S3, outils partenaires (LangChain, LlamaIndex)</td>
                <td>
                    <a href="https://aws.amazon.com/bedrock/pricing/" target="_blank">Nova Micro/Lite/Pro</a>,
                    <a href="https://aws.amazon.com/bedrock/pricing/" target="_blank">Titan Text/Embeddings/Image</a>
                </td>
                <td>Cloud (AWS Bedrock)</td>
                <td>2M (Nova Pro), 32K (Titan Text)</td>
                <td>1 000 tokens/jour (Nova Micro), 5 000 tokens/jour (Titan Lite)</td>
                <td>Pay-as-you-go (pas d'abonnement)</td>
                <td>
                    Nova Micro: 0,035€/1M in, 0,14€/1M out
                    <br>Nova Pro: 0,80€/1M in, 2,40€/1M out
                    <br>Titan Text Express: 0,80€/1M in, 1,60€/1M out
                    <br>Titan Image: 0,04–0,06€/image
                </td>
                <td><a href="https://aws.amazon.com/bedrock/pricing/" target="_blank">AWS Bedrock Pricing</a></td>
                <td>
                    Chiffrement AES-256, conformité ISO 27001/SOC 2/RGPD,
                    <br>Pas d'utilisation des prompts pour l'entraînement,
                    <br>Guardrails et Knowledge Bases intégrés
                </td>
                <td>
                    <strong>Nova</strong> : Meilleur rapport performance/prix, contexte long (2M),
                    <br><strong>Titan</strong> : Multimodal, embeddings précis, stable pour l'entreprise,
                    <br>Intégration native avec AWS (S3, Lambda, RAG)
                </td>
                <td>
                    Tarification complexe, courbe d'apprentissage AWS,
                    <br>Limites de quota en on-demand, moins de documentation que OpenAI/Google
                </td>
            </tr>
            <tr>
                <td>Meta AI (Llama)</td>
                <td>Meta</td>
                <td>USA</td>
                <td>meta.ai, Facebook, WhatsApp, API</td>
                <td><a href="https://ai.meta.com/blog/meta-llama-3-1/" target="_blank">Llama 4 Maverick, Llama 3.1 405B</a></td>
                <td>Cloud/On-premise</td>
                <td>10M (Scout)</td>
                <td>Open-weight gratuit (limites API)</td>
                <td>API: pay-as-you-go (ex: 0.19€/1M blended)</td>
                <td>Input: 0.02€/1M, Output: 0.05€/1M (Llama 3.1)</td>
                <td><a href="https://ai.meta.com/blog/meta-llama-3/" target="_blank">Meta Llama Pricing</a></td>
                <td>Open-source, pas de rétention données</td>
                <td>Contexte ultra-long, valeur open-source</td>
                <td>Support entreprise limité</td>
            </tr>
            <tr>
                <td>GitHub Copilot</td>
                <td>GitHub/Microsoft</td>
                <td>USA</td>
                <td>VS Code, JetBrains, CLI, GitHub.com</td>
                <td>GPT-5.2 Codex, Claude Opus 4.5</td>
                <td>Cloud/Azure</td>
                <td>2M</td>
                <td>50 requêtes premium/mois (Free)</td>
                <td>Pro: 10$ ; Pro+: 39$ ; Business: 19$/user</td>
                <td>Intégré aux abonnements GitHub</td>
                <td><a href="https://github.com/features/copilot/plans" target="_blank">GitHub Copilot Pricing</a></td>
                <td>SOC 2, pas d’entraînement sur le code</td>
                <td>Intégration IDE optimale</td>
                <td>Coût cumulé avec GitHub</td>
            </tr>
            <tr>
                <td>Perplexity</td>
                <td>Perplexity AI</td>
                <td>USA</td>
                <td>Web, API, Comet Browser</td>
                <td>Sonar Pro, Sonar Reasoning Pro</td>
                <td>Cloud</td>
                <td>1M</td>
                <td>Recherche basique gratuite</td>
                <td>Pro: 20$ ; Enterprise: 40$/user</td>
                <td>API: 1€/1M input, 5€/1M output</td>
                <td><a href="https://www.perplexity.ai/enterprise/pricing" target="_blank">Perplexity Pricing</a></td>
                <td>Recherche web native, citations transparentes</td>
                <td>Multi-modèles en parallèle</td>
                <td>Moins adapté au coding avancé</td>
            </tr>
            <tr>
                <td>Grok</td>
                <td>xAI</td>
                <td>USA</td>
                <td>grok.com, X (Twitter), API</td>
                <td><a href="https://docs.x.ai/developers/models" target="_blank">Grok 4.1 Fast, Grok 4</a></td>
                <td>Cloud/xAI</td>
                <td>2M</td>
                <td>Accès limité sur X Premium+</td>
                <td>SuperGrok: 30$ ; API: 0.20€/1M input, 0.50€/1M output</td>
                <td><a href="https://x.ai/api" target="_blank">xAI Pricing</a></td>
                <td>Données temps réel via X</td>
                <td>Prix agressifs, modèle "anti-woke"</td>
                <td>Transparence limitée</td>
            </tr>
        </tbody>
</table>




