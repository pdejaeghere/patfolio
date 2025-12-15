---
title: Programmation système, Unix et parallélisme
layout: math
nav_order: 4
parent: Des tics et des langages
---

### Programmation système, Unix et parallélisme

Au-delà des fondements de la programmation structurée, je le disais, le **langage C** est la pierre angulaire de la programmation système sur Unix.
Il y avait bien entendu le système multitâche d’Ada, mais c’est avec la programmation système sous Unix que j’ai appris tous les concepts et les problématiques du multiprocessus (le fameux fork) avec la synchronisation concurrente, sémaphore, mutex, sections critiques, deadlock, la communication inter-processus, pipes, fichiers partagés, sockets, signaux, sans parler de la programmation X-Windows où tous les concepts des UI modernes y étaient avec leur lot de difficultés (API complexe, ergonomie, latence).
Bien entendu, je me souviens plus particulièrement du problème emblématique : le dîner des philosophes que j’ai dû écrire en Ada, mais aussi en programmation Unix !

De quoi adopter de nouveaux tics (je m'accroche à mon jeu de mot 😉) qui m’ont souvent servi pour la programmation multithread en **.Net** : Lock (Monitor), Mutex, EventWaitHandle, Semaphore, Collection threadSafe, ReaderWriter, tous ces éléments de l’écosystème .Net soutenant les paradigmes du parallélisme, où il faut anticiper les conflits et les blocages, protéger les ressources critiques et utiliser les mécanismes de synchronisation ou de rendez-vous.

La programmation multithread est certainement la plus piégeuse et la plus compliquée à déboguer, surtout quand le deadlock ne se produit jamais sur nos machines de dev mais sur les IC ou pire, sur le terrain. On pense qu’elle permet d’optimiser nos programmes en répartissant les charges sur les différents CPU, mais elle peut aussi créer des goulots d’étranglement sur une classe trop 'thread safe' abusant de lock. Et si les CPU ne sont pas entièrement voués au programme, trop de threads utilisant le même CPU ne font que du "context switching" avec un coût non négligeable. Tous finissent peut-être en même temps mais bien plus tard !
Des langages tels que Javascript ne le proposent même pas, en reposant plutôt sur un pattern d’empilement des fonctions (les promesses), un peu comme les messages UI s’empilant dans les queues de messages et se dépilant via une boucle de messages qui les disperse vers les composants destinataires (le multitâche non préemptif des premiers systèmes Windows se reposant complètement sur ça), j’y reviendrai dans la programmation événementielle.

Face à cette difficulté, notons aussi que .Net a tenté de simplifier en introduisant une nouvelle couche Task et les mots-clés await, async, qui permettent d’unifier l’écriture de code asynchrone qu’il soit exécuté de manière concurrente par thread (parallélisme selon le nombre de cœurs), ou de façon asynchrone par empilement de fonctions/callbacks (notamment sur des runtimes mono-thread comme WebAssembly). En théorie, ce modèle abstrait les différences d’exécution. En pratique, j’ai mis pas mal de temps à comprendre certains comportements où l’UI semblait un peu gelée, notamment avec WPF : le problème s’est souvent résolu en utilisant Task.Run pour forcer l’exécution sur un autre thread !