---
title: Programmation déclarative
layout: math
nav_order: 10
parent: Des tics et des langages
---

## Programmation déclarative

Étrange ce terme, n’est-ce pas ? Mais quand il s’agit de gérer un système d’information stocké dans une base de données, c’est probablement ce qu’on utilise le plus.  
En effet, le langage **SQL** est l’archétype même du langage déclaratif !

Le principe est simple : on écrit du code qui définit le "quoi" (le but ou la condition recherchée) et on délègue au système le "comment" (l’algorithme ou la manière de réaliser l’objectif).  
Mais attention ! Si **SQL** paraît simple et élégant, il faut tout de même parfaitement maîtriser la gestion de la base de données relationnelle en amont : bien penser l’organisation des tables, choisir les bons index selon les données (inutile d’indexer un champ qui n’a que deux ou trois valeurs différentes...), et surtout, comprendre comment fonctionne le moteur de base de données.  
Je me souviens tout particulièrement d'une mauvaise expérience avec le changement de moteur **MSSQL server** vers **Postgresql** pour notre logiciel : chaque modification de record ajoute un nouveau record, contrairement à MSSQL Server. C'est très malin, ça évite beaucoup de cas de deadlock. Mais ne l'ayant compris que tardivement, on s’est exposé à bien des déconvenues dans un contexte où les modifications de record étaient à flux très très tendus.

Un autre exemple emblématique, qui ne passe toujours pas de mode, ce sont les langages de description pour les interfaces graphiques : le **HTML** et son incontournable **CSS**, sans oublier le plus rigoureux **XAML** pour les applications non Web, à base de **WPF**, **Xamarin**, **MAUI**, **Avalonia**... On le réévoquera, mais séparer la problématique d'affichage de la problématique métier est une illustration parlante, voyante plutôt, du principe de *low coupling* même si ça reste utopique de ne pas les concevoir en même temps ou de penser que l'un pourra être modifié sans tenir compte de l'autre. **En tout cas, ça permet de rendre le code beaucoup plus lisible et ça, c’est l'essentiel !**

Quoique pas toujours 😉 car s'ils sont déclaratifs pour le rendu, ils sont loin d’être séparés de la logique impérative, surtout avec les applications Web (**ASP**, **Razor**, **Blazor**, mais aussi **Angular**, **Vue.js**, **React**), où le code HTML, pur ou *templatisé*, se retrouve inséré dans des balises `#if`, `#for`, pour générer le contenu final.

Parlons aussi de la configuration du logiciel à partir d’un fichier texte éditable, généralement lu au démarrage. Lorsque les possibilités offertes permettent de réellement personnaliser le logiciel, et que l’utilisateur final peut modifier ce fichier pour adapter le comportement à ses besoins, on considère ce fichier comme un langage de programmation à part entière.  
Il y a quelques années, tout passait par le bon vieux fichier .ini (certains les utilisent encore ! si, si j'en connais). Après, on est passé au XML, puis au JSON avec les fichiers .config en .NET, et aujourd’hui, Yaml pour les configurations systèmes.

Mais, derrière la simplicité de ces formats, il y a toujours un développeur pour définir les paramètres et adapter le comportement du logiciel en fonction des valeurs de ces paramètres. Parfois, on pousse le concept jusqu’à permettre les modifications « à chaud », sans avoir à redémarrer le logiciel. Puissant, mais pas forcément trivial à gérer ! 

D’ailleurs, les architectures modernes s’embarrassent de moins en moins de cette souplesse, surtout avec **Docker** ou **Kubernetes**. Justement, voici un autre exemple de programmation déclarative lorsqu'il s'agit de mettre en place une architecture Docker avec le fichier **docker-compose.yml** ou Kubernetes et ses multiples manifestes toujours en **yaml**. 

On y décrit l'infra qu'on souhaite, et on l'obtient.

Une bonne architecture Docker ou Kubernetes doit permettre qu'on puisse stopper l'ensemble en cas de changement de configuration sans perte de données ni de traitements. Il y a des patterns de conception à mettre en place, ce n'est pas trivial, les services doivent être stateless, rapides à démarrer et s'appuyer sur un broker de messages assurant la conservation des messages non traités. Mais il peut arriver que le message ait été traité mais n'a pas eu le temps d'être supprimé avant la coupure. Donc il faut aussi que les traitements soient 'idempotents'! Vaste sujet et belles usines! 

Évoquons rapidement la logique des **pipelines d’intégration continue**, **CI/CD**  sur Azure ou Github qui là aussi s’appuient sur des fichiers de configuration demandant tout de même un travail non négligeable ! il faut personnaliser chaque étape du pipeline : définir les environnements, les variables, paramétrer les triggers, gérer les secrets, spécifier les tests ou les déploiements selon le contexte…  

Plus généralement, la logique **DevOps** « *Infra as code* » repose le plus souvent sur la programmation déclarative. Pas besoin d’algorithmique ! Nous avons utilisé Chef pour installer automatiquement un logiciel sur une machine virtuelle (EC2) sous Windows dans AWS. Ce n’est pas trivial, car il y a des fichiers à déployer, de la sécurité à mettre en place, des certificats à déployer, le système de base de données à installer, etc.  

La philosophie de Chef est plutôt pertinente. On décrit les ressources de différentes natures (File, Directory, Group NT, User, scripts à exécuter, installateur à lancer...), ainsi que les actions à effectuer pour que la ressource soit dans un état donné.  
Toutes ces ressources sont dans des fichiers nommés « Recipe », regroupés dans un « CookBook ». Il est amusant de remarquer que la sémantique emprunte au monde de la cuisine (comme celui de l’architecture pour les *Gof* ). Ça correspond bien à l'idée. On applique une recette et on peut la refaire autant de fois qu'on veut (ça n'empêche pas que le gâteau ne soit pas toujours réussi 😄 ). L’outil permettant de lancer les scripts se nomme « Knife », le couteau suisse qui fait tout.

```ruby
directory node["installationpath"] do
  action :create
end
```
Quand on rejoue plusieurs fois le script d’installation, il n’y a pas à se préoccuper si l’action a besoin ou non d’être faite : le runtime Chef le vérifie pour nous en fonction de l’état de la ressource. Donc chaque description est idempotente par nature.  

La réalité, c’est qu’on a dû implémenter des « ressources custom » en Ruby, souvent consistant à appeler un script PowerShell, et que l’idempotence, quand elle doit être gérée par le développeur, nécessite pas mal de code itératif !

**Bref, la programmation déclarative permet la concision, elle est élégante, mais derrière elle, que de choses à maîtriser !**