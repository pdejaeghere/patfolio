---
title: Programmation distribuée
layout: math
nav_order: 12
parent: Des tics et des langages
---

## Programmation distribuée

La première fois que j’ai entendu ce mot « programmation distribuée » ou « programmation répartie », c’était avec COM/DCOM, le Distributed Component Object Model. En fait, pas tout à fait : je m’étais intéressé un peu à CORBA. Mais CORBA restait très mystérieux, avec ce nom évoquant le serpent à morsure mortelle. J’en entendais parler, mais pas moyen de l’approcher, jamais vu tourner, ni en démonstration, ni en production dans les entreprises où je pouvais être envoyé en mission.

Avec COM/DCOM, c’était un peu différent. Il se trouve que j’étais très familier avec les ActiveX, OLE, OLE Automation grâce à mon expérience en Visual Basic et la programmation des applications Office, il y a 25 ou 30 ans. Cela paraît loin !  
Windows était déjà pensé, en partie, comme un système « objet », où l’on pouvait manipuler des composants réutilisables (donc les fameux contrôles ActiveX ou les objets OLE) qui s’intégraient à la fois dans les applications et, parfois, dans le système lui-même, permettant ainsi d’étendre Windows. Ils pouvaient être enregistrés, exposés, utilisés par différents logiciels, et communiquer via des interfaces bien définies.  

Ah comment ne pas se souvenir du "shérif des lieux" ? le fameux **IMarshal**, ancêtre du couple proxy/stub, qui permettait la communication inter-processus ou inter-machine. C’était grâce à lui que COM (et DCOM par extension) pouvait gérer  la sérialisation des appels, la transmission des objets, et assurer que les différents composants dialoguent, que ce soit sur une même machine ou à travers le réseau. La manière de charger le composant, dans l'espace du process, dans un process distant sur la machine ou sur une autre machine devait être quasi transparente ! belle ambition!

Mais c'est vrai qu'il y avait là une vraie notion d’abstraction, de modularité et de programmation orientée objet au niveau système, même si tout cela était parfois tellement complexe à mettre en œuvre, notamment en ce qui concerne la gestion des interfaces, des registres, des compatibilités et des versions ! 

Donc **COM/DCOM**, c’était **CORBA** à ma portée, certes absolument pas multiplateforme contrairement à son prestigieux modèle, mais au moins, on avait tous les outils pour le mettre en œuvre, même si, encore une fois, la complexité, au regard des technos d’aujourd’hui, nous ferait sûrement pas revenir en arrière ! 

Il y a eu ensuite **Transaction Server** ou **MTS** et enfin **COM+** (COM plus). Les composants étaient toujours écrits avec Visual Basic ou Visual C++, mais ils étaient plus simples à déployer. La « tringlerie » avait pris un peu de maturité pour construire des applications **multi-tiers** (3-tiers en pratique), déjà avec un frontal web développé en ASP, la partie business fournie sous forme de composants COM et la partie base de données, qui ne pouvait être que **MSSQL Server** dans l’écosystème Windows. C’est à partir de ce moment-là que les principes d’architecture d’objets **Stateless** et de transactions distribuées avec le service **MSDTC** me sont devenus familiers, au moins dans les concepts, car à part quelques démonstrations lors de séminaires Microsoft en tant que speaker, je n’ai jamais eu l’occasion de développer une application d’envergure reposant vraiment là-dessus.
Et surtout, pour des architectures résilientes, Microsoft fournissait déjà un composant fondamental **MSMQ** (Microsoft Message Queue), les messages pouvaient faire partie de la transaction coordonnée par **MSDTC**.  Finalement les problématiques étaient déjà bien identifiées mais on restait avec le paradigme **ACID**, définissant ce que devait être un système transactionnel : *Atomicité, Cohérence, Isolation, Durabilité*.

Avec l’arrivée de **.NET** au début des années 2000, **.NET Remoting** est venu remplacer **DCOM**, mais avec sa propre complexité et ses limitations, et surtout une adhérence totale à .NET. La sérialisation des objets devenait très simple grâce à la réflexion et au BinaryFormatter, et on avait beaucoup moins de difficultés à faire communiquer les composants distants, une fois les firewalls ouverts aux bons ports (encapsulation des sockets), ce qui posait toujours des problèmes avec l’IT : rien de nouveau sous le soleil .

Plus simple encore, il y a eu **WCF** et le fameux standard **SOAP**. Poussé par la montée de Linux et des technos open sources, Microsoft commençait à intégrer les problématiques multi-plateformes et le besoin de communiquer en échangeant des données non binaires. **WCF** a continué le lien avec **MSMQ** pour la fault tolerance/message durability, mais le protocole naturel était HTTP (comme REST aujourd’hui). Les services WCF étaient alors déployés sous forme de DLL chargées dans **IIS** (**I**nternet **I**nformation **S**erver).

Je dois encore faire un aveu : à part quelques POC internes pour étudier ces technologies, aucune de nos applications n’a jamais utilisé WCF.  
Nous avions considéré que les technologies changeaient trop vite. Un peu avant la sortie de WCF pour remplacer .NET Remoting, nous avons préféré avoir notre propre implémentation de SOA, qui serait un mixte entre .NET Remoting et la garantie de persistance des messages.  
Nous ne voulions pas utiliser MSMQ afin de rester aussi autonomes que possible vis-à-vis des systèmes Windows. La première implémentation encapsulait **.NET Remoting**, puis a été réécrite plus simplement en utilisant directement les bons vieux **sockets**, et enfin, plus tard, en encapsulant une superbe technologie qui reste incontournable aujourd'hui : **RabbitMQ** le plus célèbre broker de message !

Grâce à **RabbitMQ**, on peut implémenter tous les patterns d’échanges : le RPC ou Proxy/Stub, le Publish/Subscribe (sorte de multicast), ou le simple Worker (Push and Forget), qui est à la base de la scalabilité horizontale (il suffit d’ajouter un consommateur pour traiter plus de messages entrants). 

C’est aussi grâce à **RabbitMQ** qu’on peut aujourd’hui implémenter des architectures suivant le pattern **event-driven**, remettant au cœur de l’architecture un principe essentiel évoqué avec la POO : **low coupling** (faible couplage).  
On revient en plein dans l’actualité avec cette nouvelle famille d’architectures nommées **microservices**, se basant essentiellement sur le successeur de SOAP : les **API REST** (XML détrôné par JSON).  
Bien entendu, elles reposent plus que jamais sur la nécessité de ne plus être dépendant d’un système d’exploitation particulier — il faut être "multi-plateforme".

Il y a quelques années, les mondes Microsoft et Unix (Linux) étaient assez hermétiques. Aujourd’hui, les frontières sont bien plus poreuses : Linux peut tourner sous Windows, Windows peut être exécuté dans Linux...  
Et surtout, les composants tournent sous **Docker** ou **Kubernetes**, dans le **Cloud** ou **On-Premise**, qu’il s’agisse d’applications écrites en C# ou dans d’autres langages !

C’est l’avènement des architectures microservices qui pose beaucoup de questions dès qu’il s’agit de faire évoluer une application existante.  
Mais elles sont là, comme la synthèse ultime pour apporter des solutions aux problématiques de tolérance de panne, toujours construites sur le principe éculé d’avoir des services stateless. Elles relèguent la notion de transaction à une mauvaise pratique, incompatible avec la scalabilité horizontale et l’émergence des bases de données NoSQL. 

Mais rien n’est simple dans ce bas monde : cette évolution se paye par une complexification, avec l’introduction de services non stateless par nature (il faut bien que les données soient quelque part), tels que **Redis**, ou même **RabbitMQ**, qui peuvent devoir être doublés ou triplés pour assurer la disponibilité des données. De nouveaux patterns sont apparus comme **Saga** ou **Circuit Breaker**, qui ne simplifient pas vraiment les solutions… D'autre part, il ne suffit plus de surveiller une application globale, mais de mettre en place une visibilité, des alertes et une traçabilité sur chaque composant, chaque file de messages (eg **Prometheus/Graphana**) et la possibilité à chaque service d'indiquer sa santé avec des critères pertinents (par exemple, surveiller la consommation des messages Rabbitmq). C’est le seul moyen de garantir la résilience, la scalabilité et la maintenabilité du système.

Donc, avant de se lancer là-dedans, il est crucial de bien s’assurer de la nécessité de telles architectures et surtout de procéder par itération, pour ne pas se noyer, selon l’adage bien connu : *"le mieux est l’ennemi du bien"*.