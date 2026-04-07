---
title: PatGraph framework
layout: math 
nav_order: 2
parent: Chantiers navals
---

# PatGraph framework

## L'idée d'un framework 

J'expliquais dans l'article [Des diagrammes vers le code, une expérience DSL](/Architecture logicielle/Documenter_logiciel/DSL) et [Naviguer à partir des diagrammes](/Architecture logicielle/Documenter_logiciel/CodeVersDiagramme) quelques idées que j’avais eues et que j’avais explorées pendant les semaines d’innovation que l’entreprise nous offrait comme temps de respiration après des sprints complets.

Mais faute de temps, je n’ai pas pu forcément aller jusqu’au bout des choses. Toutes ces idées sont donc restées dans mon petit cimetière, jusqu’à ce que j’aie envie de les ressusciter pendant l’accalmie d’activité professionnelle que je traverse.

Et en commençant par un socle : le moteur de diagrammes ! *Celui que j’aurais aimé trouver il y a quelques années !*


J'entends déjà les *"ça existe déjà…"*, *"c'est pas utile, il y a mieux à faire…"*, *"T'as qu'à demander à GitHub Copilot…*"

**Tout cela est vrai !**

Mais je répondrai comme Marcel Pagnol à qui on attribue, légende ou non, la réponse suivante à son voisin qui s'étonnait de le voir cuisiner ses propres confitures alors que c'est tellement plus simple de les acheter toutes faites :
*"… mais l'odeur, mon bon ami… l'odeur de la confiture en train de cuire…"* 😉


Et puis, c'est un excellent terrain pour illustrer les synthèses que j'aimerais faire, à ma sauce 😉, sur les principes d'architecture SOLID et les Design Patterns !


## Mes requirements

Voici quelques-uns de mes requirements :

**Phase 1 :**

- En C# .NET 10.0 ( finalement 9.0 à cause )
- ViewModel complet
- View pour WPF et Avalonia (et donc WebAssembly)
- Hyper efficace ! Dessin direct dans le GC (contexte graphique)
- Export SVG (c'est que du XML !)
- Éditeur Undo/Redo, gestion de la position et du type de liaison (Bezier, multi-segment)

**Phase 2 : Sous PlantUML positionnable**

- Objets UML les plus standards (components, state machine, …) : utiliser l'IA pour générer le code de dessin à partir d'un .svg de PlantUML
- Grammaire ANTLR pour le sous-PlantUML
- Pattern Visitor sur le modèle
- Extension Visual Studio

**Phase 3 : Un éditeur de Workflow pour illustrer**

- Pattern Visitor sur le modèle
- Stockage dans un langage dédié (inspiré du sous-PlantUML)
- Extension dans Visual Studio



## Showroom  (Phase 1 en cours)

<img src="activity diagram.png"  ALIGN=center/>

<img src="Neuronal network.png"  ALIGN=center/>