---
title: Les outils et la logique de repository
layout: math 
nav_order: 2
parent: De l'art de documenter les logiciels au long cours
---

# Les outils et la logique de repository

Au début, il y a un temps que les moins de 30 ans... les outils étaient très classiques : Word, Visio, avec des documents stockés sur un serveur partagé (et en utilisant Source safe quand même!).
Simple, mais avec tous les problèmes que l’on connaît :

- difficile de maintenir à jour,
- duplication,
- documents qui divergent,
- impossible de faire du versioning propre,
- et surtout, documentation complètement décorrélée du code.

Nous sommes ensuite passés à Enterprise Architect avec l’idée de tout centraliser :
- requirements
- use cases
- test cases
- design
- classes
- diagrammes
- etc.

L’idée était séduisante : avoir toute la documentation et la modélisation au même endroit, organisée dans une arborescence, stockée sous plusieurs fichiers XMI dans un repository SVN avant de passer sous Git, avec une base locale sur chaque poste.

J’expliquerai dans le point suivant que nous avions mis en place un système de génération de code à partir du modèle métier pour le stockage en base de données (ORM), mais aussi à partir des diagrammes de state machine et d’activité pour gérer la dynamique métier et les différentes interactions entre les composants !

Puis nous avons migré vers une base centralisée pour des raisons de performance et de partage.

Mais nous avons alors rencontré un autre problème : l’intégration avec Git.
Les modèles, stockés en XMI ou en base, ne se versionnent pas bien :

- conflits difficiles à résoudre,
- diff illisibles,
- merges compliqués,
- dépendance forte à l’outil.

Pour y remedier, on a acheté des licences pour une solution tierce "LemonTree" conçu par un éditeur Allemand. Trés brillant mais on s'est heurté quand même avec des difficultés de compatibilité de version. Il aurait fallu qu'on mette à jour régulièrement les versions d'Entreprise Architecte, or nous avions developpé un ensemble d'outil pour adapter EA à nos besoins de tracabilité ainsi que les fameux outils de génération de code qui avaient parfois quelques difficultés à s'adapter à chaque nouvelle version EA(breaking changes). Ca devenait un peu lourd dingue. 

On s'est retrouvé alors avec un effet contre productif:
on veut versionner la documentation comme le code, mais les outils de modélisation ne sont pas faits pour fonctionner avec la même logique simple qu'on a avec le code dans des fichiers textes. Ouvrir l'outil devenait pesant. Aller modifier la doc à l'interieur ne se faisait plus avec la même motivation et le même enthousiasme que les promesses de départ. 

C’est à ce moment-là que nous avons évolué vers une approche différente, comme certainement beaucoup d’entreprises :

- documentation en AsciiDoc
- diagrammes en PlantUML
- le tout stocké dans Git, avec le code : **DOC as CODE**
- génération de documentation (HTML/PDF) via une chaîne de build

Même les requirements ont migré pour devenir des fichiers Markdown rangés dans une arborescence du repository.

Cette approche a plusieurs avantages :

- versioning propre
- diff lisibles
- revue de documentation dans les merge requests
- documentation proche du code
- possibilité d’industrialiser la génération de documentation

Finalement, on a suivi le sens de l’histoire que l’on retrouve aussi avec ADO que nous utilisons pour gérer les user stories à réaliser par Sprint (méthode Scrum), ou GitHub qui permet de stocker le code, la documentation ainsi que les scripts CI/CD, l’ensemble parfaitement versionné.

Puis sont arrivés les outils LLM (ChatGpt, GitHub Copilot, Claude code) qui peuvent exprimer leur redoutable efficassité sur du texte à tous les étages.

Aujourd’hui, nous les utilisons pour  générer des diagrammes PlantUML à partir du code, générer des trames de documentation, résumer certains modules et aider au reverse engineering.

Mais il faut rester prudent, car la documentation générée par IA est souvent très verbeuse, assez générique et parfois creuse, paraphrasant simplement le code sans apporter de réelle compréhension du design.

L’IA reste donc un assistant : elle permet de produire un premier jet à affiner et à étoffer, mais ce n’est pas un auteur de documentation de design!


