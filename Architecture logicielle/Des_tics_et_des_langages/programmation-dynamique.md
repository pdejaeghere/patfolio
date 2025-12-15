---
title: Programmation dynamique
layout: math
nav_order: 8
parent: Des tics et des langages
---

## Programmation dynamique

Toujours avec **Smalltalk**, j’ai découvert la Métaprogrammation. La classe d’un objet est elle-même un objet pouvant s’autodécrire et à qui on peut ajouter des méthodes et des propriétés de façon dynamique.

.Net propose la même chose avec la réflexion, et aussi le CLR ou mieux le DLR (dynamic language runtime) permettant de créer du code à la volée pour l’exécuter ensuite dans le même processus (très pratique pour faire piloter son logiciel via un langage de script ‘maison’, ce que nous avons fait dans le logiciel de laboratoire d’analyse développé chez **Normand Info** : un langage de script, nommé **Labscript**,  offrant aux biologistes la possibilité d’automatiser la validation des résultats de tests en ‘codant’ leur expertise).

Bien entendu, les langages dynamiques (souvent reposant sur une machine virtuelle ou sur un interpréteur) ne sont pas à confondre avec les langages objets (ex. Lisp, Javascript le permettent, C++ non), mais quand même, je trouve que ça reste très couplé à l’univers de la programmation objet. Remarquons que Javascript est devenu un langage objet sans mot-clé dédié, grâce à cette possibilité de créer des fonctions attachées à une fonction ‘mère’.