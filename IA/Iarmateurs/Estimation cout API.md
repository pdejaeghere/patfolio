---
title: Estimation du coût de l'usage des APIs
layout: math 
nav_order: 3
parent: IArmateurs
---


# Estimation du coût de l'usage des APIs

Pour résumer, quand on intègre une fonctionnalité utilisant un LLM propriétaire au sein d'une application, on a deux choix possibles :

- un LLM sur une infra SaaS (OpenAI, Microsoft Azure...)
- un LLM open-weights sur sa propre infrastructure

L'intérêt du premier choix réside dans la simplicité de la mise en œuvre et dans le fait de pouvoir utiliser les meilleurs modèles. Par contre, ce n'est pas gratuit ! Comme mentionné précédemment, le modèle de paiement n'est généralement pas fourni sous forme d'abonnement mais au nombre de tokens entrants et sortants.

On comprend bien la logique de business model qu'il y a derrière. Si l'accès aux APIs avait un mode gratuit, on pourrait développer des applications s'amusant à picorer sur les différents ports des armateurs de l’IA.

Ce n'est pas le cas, et on peut tomber dans un sacré piège si on n'y prend pas garde !

Imaginons un chatbot développé pour un usage personnel qui envoie l'historique complet à chaque question de l'utilisateur afin de donner le contexte complet au LLM.

J'ai écrit un petit programme en Python afin d'évaluer le coût de ce chatbot. Même si le prix à l'input est moins important que le prix à l'output, plus la conversation ping-pong dure, plus l'historique grossit. L'input cumulé devient conséquent et, comme dit l'adage, les petites gouttes font les grandes rivières ; le prix s'envole.

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

Bref, je ne sais pas trop si j'ai loupé quelque chose, si les grandes entreprises arrivent à négocier un usage des APIs dans un mode abonnement mais, pour un usage personnel, il vaut mieux considérer l'usage d'un modèle open weight sur sa propre infra, ou alors d'utiliser les outils proposés en mode gratuit ou abonnement mais pas à travers son propre chatbot.

Cependant Il y a quand même un gros problème avec les modèles open weight. Ils sont limités sur une machine moyenne. J'ai deux portables : intel i9, 32 Go, GPU 4 Go et un intel i7, 32 Go, GPU 8 Go , et la plupart des modèles, quand ils peuvent tourner, tournent assez lentement.

 D'autre part, les modèles open weight ne supportent pas tous la possibilité d'injecter des spécifications de fonction (pour des appels de code interne ou MCP).
Je proposerai une étude plus complète dans le prochain article...




