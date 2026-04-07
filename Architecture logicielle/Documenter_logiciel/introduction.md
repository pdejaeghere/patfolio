---
title: De l'art de documenter les logiciels au long cours
layout: math 
nav_order: 3
parent: Architecture logicielle
---

# De l'art de documenter les logiciels au long cours...
Ou *Pour la maintenance ou contraintes réglementaires et contre la perte de mémoire dans les projets de plus de 10 ans ...*

Lorsqu’on travaille sur un logiciel métier avec un cycle de vie long — parfois 10, 15, 20 , 30, 40  ans — la documentation n’est plus un simple livrable de projet. Elle devient un élément central du système, au même titre que le code lui-même.

Dans certains contextes, comme les dispositifs médicaux soumis à des contraintes réglementaires (ISO, classes B ou C), documenter n’est même pas une option : c’est une **obligation**. Mais au-delà de l’audit ou de la conformité, la documentation joue un rôle bien plus fondamental : elle conditionne la capacité à maintenir, faire évoluer et transmettre le logiciel dans le temps.

Car la réalité est souvent moins idéale. Avec les années, la documentation devient :

- inexistante,
- obsolète,
- illisible,
- trop détaillée pour être utile,
- ou pire, produite uniquement pour répondre à un audit.

Et pourtant, c’est précisément lorsque les équipes changent, que le contexte initial disparaît et que le logiciel continue de vivre, que cette documentation devient critique.

À cela s’ajoute l’évolution des outils pour la documentation : des documents Word et Visio aux référentiels centralisés, puis aux approches versionnées (Markdown, AsciiDoc), aux diagrammes en texte (PlantUML, Mermaid, C4), jusqu’à l’arrivée récente de l’IA capable de générer, analyser ou confronter documentation et code.

Mais une question reste entière :
que faut-il documenter, et comment, pour que cette documentation reste utile dans le temps ? jusqu'à quel niveau pour assurer sa pérenité et son utilité: le fameux *ni trop, ni pas assez*.

Notons en premier lieu que la documentation, ce n'est pas uniquement les *docs de design*. C'est un ensemble de contenu dans lequel il faut savoir naviguer pour une version donnée ou à travers differentes versions (si besoin de l'historique des évolutions) :

- les user-stories, requirements (besoins fonctionnels et techniques),
- la documentation utilisateur ,
- la documentation technique (pré-requis, deployment...),
- l’infrastructure,
- les décisions d’architecture (POC, compte-rendu de refinement)
- les documentations de convention ( coding rules)
- les designs logiciel ( vue d'ensemble, par composant)
- le code même, documenté au niveau de la classe, des méthodes, de l'implementation au sein des méthodes : et là aussi, combien de commentaires inutiles uniquement pour éviter un warning de SonarLint! 
- les tests unitaires ou d'integration qui peuvent être un très bon point d'entrée pour comprendre l'usage d'un framework ou la logique fonctionelle
- Les protocols de vérifications qui sont aussi très interessants pour comprendre l'attendu des differents fonctionnalités.
- Les analyses de risque

Donc vaste sujet. Trop vaste, même, pour être traité de manière exhaustive.
Et quand on s’étonne du temps nécessaire au développement d’un logiciel, c’est aussi parce qu’il y a tous ces aspects qui font un tout, et qui doivent assurer la solidité de l’édifice, **son évolutivité et sa maintenabilité**.

