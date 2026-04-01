---
title: Utilisation gratuite
layout: math 
nav_order: 4
parent: IArmateurs
---


# Utilisation gratuite ?

Vous avez bien compris que, dans le cadre d'une entreprise, les données, quelles qu’elles soient (informations critiques, code, secrets), ne doivent pas être divulguées sur des services de chat gratuits, car rien ne garantit qu'elles ne soient pas utilisées pour entraîner les modèles eux-mêmes. Même si certains, comme Claude, donnent la possibilité de configurer la confidentialité en n’autorisant pas que les discussions servent à améliorer les modèles, cela reste incertain.

À propos de l’utilisation de nos données pour l’amélioration des modèles, il est difficile de savoir à quelle fréquence ces derniers sont réellement réentraînés. Le fine-tuning est probablement effectué de manière régulière, mais ces aspects restent assez opaques. Par ailleurs, le fait que la plupart des IA soient désormais capables d’aller chercher de l’information sur le web ou sur GitHub leur permet d’accéder à des données récentes sans nécessiter de réentraînement complet trop fréquent.

Ce qui est certain, c’est que, pour un usage personnel dont les données envoyées ne sont pas spécialement critiques, on peut aujourd’hui se contenter des versions gratuites en passant d’un outil à l’autre. Dans ce cas, même en admettant que les données ne soient pas utilisées, on peut considérer que cette gratuité constitue une sorte d’investissement sur le futur, en rendant dépendantes nos pauvres âmes à leurs usages.

Je ne vais pas m’étendre davantage sur ce risque bien réel. En avoir conscience est déjà un moindre mal. Utiliser l’IA pour rechercher de l’information plus rapidement que via le web n’est finalement qu’un confort que l’on accepte ou non. 

En tout cas, on peut imaginer que le jour où les robinets vont s’arrêter de couler, ça fera mal au porte-monnaie si on ne peut plus faire sans! 

Peut-être que le modèle économique évoluera plutôt avec la possibilité de recevoir ou non de la publicité, un peu comme sur les sites web ou les vidéos YouTube. On voit bien que le business model se cherche en ce moment, avec des allers-retours et des annonces tatant le terrain.


Toujours est-il qu’avec ces outils, je n’ai pas besoin de payer d’abonnement en switchant vers un autre dès que j’atteins le quota pour l'un (au prix d'un gros copier-coller de la conversation) :

| Outil             | Lien                  | Limite free                 | Usage conseillé                                        |
| ----------------- | --------------------- | --------------------------- | ------------------------------------------------------ |
| ChatGPT           | [chatgpt.com](https://chatgpt.com)           | ~30 msg / 5h                | Usage général, explications, rédaction, aide technique |
| Claude            | [claude.ai](https://claude.ai)             | quota 5h + semaine          | Très bon en **code**, longs textes, analyse, documents |
| Gemini            | [gemini.google.com](https://gemini.google.com)     | quota journalier            | Grosses requêtes, recherche, synthèse                  |
| Le Chat           | [chat.mistral.ai](https://chat.mistral.ai)       | pas clair                   | Secours, questions simples, un peu de code             |
| Microsoft Copilot | [copilot.microsoft.com]([https://copilot.microsoft.com) | limite vitesse              | Recherche web, questions avec sources                  |
| GitHub Copilot    | [github.com/copilot](https://github.com/copilot)    | 2000 complétions + 50 chats | Autocomplétion et aide **code**                        |

Sans compter qu'on pourrait être tenté d'utiliser plusieurs comptes gmail mais ce n'est pas légal. Ils ont sans doute des algorithmes trés puissants à base d'IA pour détecter qu'il s'agit de la même personne derrière le clavier 😁

On verra le temps que ça dure!

## Et pour le code?

La question du code généré par IA et des licences reste encore floue juridiquement. Les modèles ayant été entraînés sur du code open source, il est théoriquement possible que certains morceaux générés soient similaires à du code existant soumis à licence (GPL par exemple), ce qui peut poser problème dans un cadre commercial. En pratique, beaucoup d’entreprises considèrent le code généré par IA comme du code trouvé sur Internet : il doit être relu, compris et parfois réécrit avant d’être utilisé en production.

Pour rappel, toutes les licences ne permettent pas un usage commercial libre.

| Licence    | Usage commercial | Obligation                                    |
| ---------- | ---------------- | --------------------------------------------- |
| MIT        | Oui              | Aucune (juste garder la licence)              |
| Apache 2.0 | Oui              | Mention licence                               |
| BSD        | Oui              | Mention licence                               |
| GPL        | Oui              | Mais on doit **ouvrir le code**              |
| AGPL       | Oui              | Mais on doit **ouvrir le code même en SaaS** |
| MPL        | Oui              | Ouvrir seulement les fichiers modifiés        |

Dans les grosses entreprises, il y a très souvent un bureau spécialisé dans cette question des licences et de la propriété intellectuelle. C'est un risque majeur à ne pas prendre à la légère. Je me souviens avoir dû retirer un morceau complet récupéré à l'époque sur CodeProject. Tout le code source de nos logiciels passait régulièrement à la passoire Synopsys. 

Et donc, qu’en est-il des morceaux de code fournis par l’IA ? La question reste ouverte. Mais à ne pas prendre à la légére, les Vibes codeurs pourraient s'en mordre les doigts !
