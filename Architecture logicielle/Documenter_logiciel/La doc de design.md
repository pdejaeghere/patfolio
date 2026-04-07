---
title: La doc de design
layout: math 
nav_order: 1
parent: De l'art de documenter les logiciels au long cours
---

# La doc de design

Évidemment, la documentation de design, c'est celle qui nous occupe principalement en tant qu’architecte logiciel ou développeur. C’est celle dont on doit être persuadé qu’elle servira aux autres, l’autre pouvant être aussi soi-même après quelques mois.

Or, si le développeur aime coder (enfin, j’espère que ça restera vrai avec l’IA qui prémâche tout maintenant), c’est rare qu’il aime documenter. Combien de fois n’a-t-on pas entendu :

- *« La doc ? Bah, c’est dans le code… »* : c’est vrai, il n’y a rien de plus exact que le code lui-même pour dire ce que ça fait.
- *« La doc ? Personne ne la lit »* : c’est un peu vrai aussi. Le premier réflexe des développeurs, c’est d’aller dans le code, de lancer l’application puis de débugger pas à pas pour comprendre le comment.

Et pourtant, indépendamment de ces deux remarques, si je ne devais retenir qu’un seul bénéfice dans la documentation, ce serait pour soi-même, lorsqu’il s’agit de la pondre. On peut citer la fameuse citation de Nicolas Boileau :

***« Ce que l’on conçoit bien s’énonce clairement,
Et les mots pour le dire arrivent aisément. »***

Car oui, c’est souvent en écrivant la documentation de design qu’on se rend compte si notre design tient la route, s’il est suffisamment simple et cohérent pour qu’on puisse l’expliquer facilement. C’est pour cela que je ne suis pas spécialement un adepte de la documentation avant le code. Je pense que les deux doivent se faire dans un processus de micro-itérations intriquées.

Un peu de doc d’analyse (lors du refinement) → code → doc de design → code → doc de design…

Avec les outils d’IA qui génèrent le code, je pense même qu’il faudrait presque imposer aux développeurs d’écrire une documentation de design sur le code généré, et sans la demander à l’IA. Ce serait un moindre mal pour s’assurer qu’ils en gardent la maîtrise.

Alors que doit contenir la doc de design ?

Déjà, il ne faut pas la confondre avec la documentation d’utilisation d’un composant. Lorsqu’on développe des frameworks, des abstractions, il est utile de fournir une documentation “usage” telle que les éditeurs comme Microsoft savent proposer. Par exemple, si on cherche comment utiliser la classe Dictionary, on a accès à des guides pratiques, des descriptions de la classe et de ses méthodes, ainsi que des exemples d’utilisation sur le site officiel Microsoft Learn. C’est évidemment nécessaire (et peut être source d’information pour les LLM actuels). On peut faire la même chose pour peu que notre code soit bien documenté avec des outils tels que DocFX, Sandcastle ou Doxygen, qui permettent d’extraire la description des classes et de générer un site web de documentation. Il ne s’agit pas de comprendre comment les classes sont implémentées, mais comment les utiliser.

````csharp
 /// <summary>
 /// Goal: A WPF control to display and interact with a graph, supporting zooming, panning, selection, and context menus.
 /// Must be binded with a GraphViewModel as DataContext, which provides the graph data and commands.
 /// </summary>
 /// <example>
 ///GraphViewModel graphViewModel = new GraphViewModel();
 ///  
 ///StartNode n0 = new() { Name = "Start", X = 187, Y = 26 };
 ///graphViewModel.AddItem(n0);
 ///....
 ///graphViewModel.SetAutoSize();
 ///this.GraphViewer.RegisterRenderer(new PatGraph.WPF.StartNodeRenderer());
 ///this.GraphViewer.RegisterRenderer(new PatGraph.WPF.ActionNodeRenderer());
 ///this.GraphViewer.RegisterRenderer(new PatGraph.WPF.DecisionNodeRenderer());
 ///this.GraphViewer.RegisterRenderer(new PatGraph.WPF.EdgeRenderer());
 ///this.GraphViewer.RegisterRenderer(new PatGraph.WPF.NeuronalRenderer());
 ///this.GraphViewer.RegisterMouseResponsability(new ContextMenuOnSelectedResponsibility());
 ///this.GraphViewer.RegisterMouseResponsability(new SelectionOrDragResponsibility(true));
 ///this.GraphViewer.RegisterMouseResponsability(new PanMovingOrContextMenuResponsibility());
 ///this.GraphViewer.RegisterMouseResponsability(new MultiSelectionByMouseResponsibility());

 ///this.GraphViewer.DataContext = graphViewModel;
 ///</example>
 public partial class GraphViewer : UserControl, IWeakEventListener, IGraphInteractionContext
````

Mais quand il s’agit de nos sources, ce n’est pas forcément le plus utile, puisqu’il suffit de naviguer directement vers le fichier code de la classe pour avoir sa description complète. 

Non, la doc de design a un autre objectif : donner suffisamment d’informations pour qu’un développeur puisse comprendre la logique interne, dans quel contexte, pour quel usage, comment l’implémentation a évolué… Cette doc doit contenir le “petit chapeau” permettant d’appréhender le code, qui restera par définition la source de vérité.
Sur tous les sites de code opensource, Github en tête, un projet sans un readme solide passe vite aux oubliettes et la doc est indispensable si on veut trouver des contributeurs sérieux.

Mais quand on veut répondre aux exigences de la norme IEC 62304 pour les logiciels dispositifs médicaux classe B et C, il y a des obligations très structurantes. Finalement, cette obligation est loin d’être inutile, à condition d’être appliquée intelligemment. Il ne s’agit pas d’écrire les docs uniquement pour avoir le label ISO.

La norme demande notamment :

- Définir les software requirements
- Définir une software architecture
- Décomposer l’architecture en software units
- Définir les interfaces entre ces units
- Faire un "detailed design" pour chaque software unit
- Implémenter chaque unit
- Faire les tests unitaires
- Faire les tests d’intégration
- Faire les tests système
- Et documenter tout ça (et le relier par traçabilité)

L’architecture doit être raffinée jusqu’à être représentée par des software units (classes B et C). En gros, dans la hiérarchie :

- Software System → le logiciel complet
- Software Items → sous-systèmes / composants
- Software Units → plus petite unité testable (module, classe, composant, service…)

La granularité n’est pas imposée : c’est le fabricant qui décide, tant qu’il peut décrire, tester et tracer ces unités.

La difficulté est plus grande lorsqu’il s’agit de rattrapage documentaire sur un logiciel qui a subi les affres du temps. Il nous est arrivé de définir des Software Units dont les noms ne correspondaient pas trop à des classes ou des modules existants. Les concepts étaient présents bien entendu, mais la bijection n’était pas nécessairement immédiate. Et si on avait voulu assurer cette bijection, ça aurait complexifié inutilement la documentation. Tout est question de compromis. 

Un point important est de définir un template ou canevas avec l’ensemble des éléments attendus afin de trouver une certaine homogénéité dans toutes les docs de design.

Pour chaque point, ce template contient des questions auxquelles il faut répondre. Souvent, ça peut paraître un peu tiré par les cheveux ou non applicable, mais ça permet aussi de penser à des points qu’on aurait vite fait d’oublier. Par exemple, forcer à décrire les interactions avec les autres software units permet aussi de vérifier les principes élémentaires d’architecture comme le low coupling et le single responsibility. De même, s’obliger à justifier que le P&S (privacy and security) a été couvert, idem pour les performances, permet d’instaurer des réflexes de conception qui ne peuvent aller que dans le sens de la qualité du logiciel.

Malheureusement, il est difficile de donner une recette exacte, cela dépend de tellement de facteurs, par exemple de la granularité des software units. Dans tous les cas, c’est une démarche dont le résultat appartient à l’entreprise, mais qui devrait devenir une bonne pratique quel que soit le domaine, même si le logiciel en question n’est pas un dispositif médical.

On devrait par exemple y trouver :

- Vue d’ensemble de l’architecture de la software unit
    - Son objectif
    - Ses interactions avec les autres software units (diagramme de composants UML et description textuelle des interactions)
    - Ses interactions avec les SOUP (les composants externes, l’infrastructure sur laquelle la solution repose, par exemple : navigateur, base de données, broker de messages…)
- Le design
    - Le type d’interface pour être utilisé par les autres software units : tout dépend de la nature du composant, mais ça peut être une façade, des interfaces objet, une API REST, une UI, un outil en ligne de commande…
    - La cuisine interne :
        - Les sous-composants ou classes utilisés (les plus représentatifs)
        - Les structures de données et la manière de les stocker quand elles sont persistantes
        - Des diagrammes de séquence pour illustrer l’implémentation de certains cas d’utilisation
        - Des points techniques, algorithmes
        - Les cas d’erreur, la tolérance aux pannes
        - etc.
- Des aspects de configuration
- Des aspects P&S
- Des preuves de performance
- Une analyse de risque et les solutions apportées pour y remédier


Ce qui est certain, c’est que comme pour tout, quand c’est fait au fur et à mesure, l’effort est bien moindre que lorsqu’il faut rétro-pédaler avec du reverse engineering.

Dans la boîte où je bossais, le code review incluait la revue de la documentation et devait surtout vérifier si la documentation de design existante ne nécessitait pas une mise à jour.
 
 ***Peu mais tout le temps*, voila le secret pour la pérénité de la doc!**


