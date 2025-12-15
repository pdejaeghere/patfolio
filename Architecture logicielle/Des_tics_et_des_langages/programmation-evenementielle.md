---
title: Programmation événementielle
layout: math
nav_order: 11
parent: Des tics et des langages
---

## Programmation événementielle

J’ai une tendresse toute particulière pour la programmation événementielle, sans doute toujours liée à cette représentation quasi anthropomorphique des objets pouvant envoyer des messages et en recevoir.

Mais surtout, c’est associé à une époque où il était vraiment amusant et gratifiant de concevoir des applications GUI, des interfaces Homme-Machine. Et ça a commencé très en douceur pour moi, avec Visual Basic 3 puis 4 ! C’était tellement facile avec l’éditeur permettant de composer le *Form*. On plaçait un bouton, on modifiait directement ses propriétés, son label, on double-cliquait dessus et hop, on se retrouvait dans le code. Un petit : `MsgBox("Coucou")`. On exécutait, on cliquait sur le bouton et le message s'affichait !

Quand je suis passé à la programmation Windows en langage C, évidemment, ça se corsait... Je découvrais les handles de fenêtres, la boucle de message, la structure de message avec ses centaines de constantes rassemblées dans le `windows.h`, sans oublier toutes les API Win16 puis Win32 pour l’allocation de mémoire, la gestion des fichiers, les échanges DDE ou la gestion du presse-papier... Visual Basic était un vrai jeu d’enfant à côté. Mais au moins, comprendre la boucle de message et la manière de « distribuer » (dispatch) les traitements événementiels me confrontait à l’envers du décor, permettait de saisir ce que le multitâche non préemptif signifiait, et ça rappelait la boucle des jeux vidéo.

Pendant les années d'étude, J’ai découvert un environnement au moins aussi complexe avec la programmation X-Windows sur Unix/Solaris, mais on sentait bien que la technologie était quand même d’un autre niveau, avec une vraie séparation client/serveur : le serveur étant le système de fenêtres avec lequel l’application communiquait. Cela permettait d’envoyer l’exécution de l’interface sur la machine du copain, ce qui a permis bien des blagues de potache 😄 !

Avec Visual Basic, la programmation événementielle pouvait nous donner le sentiment de replonger dans les travers du `Goto`, de triste mémoire. Chaque événement était codé séparément, souvent sans structure globale, ce qui pouvait engendrer une logique éclatée et difficile à maintenir.  
Borland C++ ou Visual C++ avec ses MFC (Microsoft Foundation Classes) ont remis de l'ordre grâce à la programmation objet et à une gestion déclarative des messages (le fameux message map), qui dispensait le développeur de gérer explicitement la boucle de messages. Celle-ci devenait quasiment transparente.  
C'était aussi le début de véritables patterns de conception, préfigurant l’approche **MVC**, Model view controller : séparation de la logique métier, de l’affichage et des interactions.

Ensuite, il y a eu une évolution lente et progressive avec .NET : les WinForms ont réconcilié la facilité d’édition des formulaires, telle qu’on la connaissait en Visual Basic, avec l’organisation apportée par la programmation orientée objet.  
Puis est arrivé WPF, encore mieux, car il permet une véritable séparation de la "View" en XAML, dont le look pouvait, en théorie, être confié à de vrais designers (les développeurs ne faisant que des trucs moches, c’est bien connu 😄).  
On y distingue la **V**iew (l’interface), le **V**iew**M**odel (l’abstraction de l’affichage), et le **M**odel (les objets métier) :  **MVVM**.  
Tout cela grâce à une mécanique très puissante, que l’on retrouve désormais dans tous les frameworks d’UI actuels (Web ou non-Web), le **binding** qui permet de relier facilement les propriétés du **ViewModel** aux propriétés des composants graphiques de la **View**.
Aujourd’hui, il faut bien reconnaître qu’avec l’émergence des besoins multi-Plateformes, des applications Mobiles, des déploiements web et ses nombreux frameworks d’UI, avec des logiques différentes suivant l’endroit où s’exécute la gestion du frontal, uniquement dans le browser **SPA** **S**ingle **P**age **A**pplication (avec React ou Angular), ou plutôt côté serveur (ASP.NET MVC, Blazor), les choses ne sont pas forcément simplifiées, même si la notion d’événements pilote toujours les interactions.

Je voudrais finir par ce que j’aurais pu commencer : nous avons évoqué la programmation événementielle pour les GUI, mais finalement, cette notion dépasse largement ce cadre — elle est même au cœur de l’informatique. Une interruption I/O en assembleur n’est-elle pas une sorte d’événement ? Dès l’instant où il y a plusieurs processus ou threads devant se synchroniser, n’utilise-t-on pas des événements, comme le signal ou l’EventHandle de .NET ? Le Pattern Observer, et son extension vers les architectures event-driven que je vais évoquer dans le point suivant, relèvent aussi de la programmation événementielle !  
De même, j’évoquerai la programmation à partir de langages graphiques, ou celle permettant de contrôler des robots dont les différents capteurs envoient des signaux de façon désordonnée, comme autant d’événements…

**Donc oui, l’événement en informatique, c’est le stimulus d’un organisme vivant qui lui permet de réagir et de prendre des décisions.**