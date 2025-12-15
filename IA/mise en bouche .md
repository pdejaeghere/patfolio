---
title: Mise en bouche 
layout: default 
nav_order: 1
parent: IA
---

J’ai commencé à développer assez tôt, en classe de 4ᵉ. J’avais réussi à convaincre mes parents de nous offrir, à mon frérot Vincent et à moi-même, un ordinateur. J’avais déjà un jeu d’échecs électronique avec lequel je jouais des heures. Mes parents, mon père, pédagogue et ma mère, prof de français, à force d’arguments et d’enquêtes auprès de leurs collègues - surtout profs de maths😉 -, ont fini par céder. Après tout, c’était mis en avant par l’Éducation nationale — il s’agissait du TO7 😄 — les programmes étaient à visée pédagogique, un peu ludiques, mais rien à voir avec le côté peu créatif des consoles Atari ou des jeux à cristaux liquides que nos cousins possédaient et qui semblaient bien abrutissants.

Je me souviens avoir passé des heures à restituer les lignes de code contenues dans des livres ou des revues d’informatique (Hebdogiciel). Et déjà, écrire ces lignes de code que l’ordinateur était capable de comprendre et auxquelles il obéissait, c’était comme un dialogue qui s’opérait avec une entité presque vivante, capable de râler “SYNTAX ERROR”, d’éructer avec cette voix stridente lors de la lecture des cassettes, de s’éteindre à la moindre coupure de courant, nous faisant perdre les quelques heures passées à lui donner patiemment des instructions.

Mais je me souviens tout particulièrement d’un article ; c’était dans la revue “Science & Vie”, peut-être en 1985 ou 1986, et ça parlait du fameux test de Turing en donnant un exemple basique de comment programmer une sorte de dialogue avec la machine qui puisse “bluffer” à partir de quelques réponses à des questions toutes faites, préalablement posées par la machine. (Elle nous posait des questions, retenait les réponses puis nous demandait de l’interroger sur ce même champ de questions.) Pas hyper difficile à coder, mais facile à mettre en défaut, facile à déceler la supercherie… en tout cas, ça m’avait bien amusé de coder ça en BASIC sur le TO7 qui commençait déjà à montrer de sérieuses limites.

Un peu plus tard, lors de mes études, il y a eu la programmation d’un moteur de système expert en projet de maîtrise, d’un mini-compilateur Pascal, l’apprentissage du Prolog, du LISP, des algos minimax, la recherche d’optimum, la théorie des graphes et le fameux problème du voyageur de commerce. Concernant les réseaux de neurones, c’était un peu plus tard, lors de mon DESS à Lille. Mais ça ne faisait qu’effleurer la théorie (en 1995) : perceptron, réseaux multicouches. Le seul TP réalisé a consisté à coder une reconnaissance de caractère via un réseau de Hopfield… rigolo, intéressant, mais très limité.

Ensuite, dans le cadre du travail, un système de règles pour la validation des résultats, s’apparentant, en poussant un peu, à une sorte de système expert puis une étude pour utiliser les algorithmes de machine learning (ml.net) afin d'essayer de valider automatiquement des résultats de laboratoire à partir de critères (sexe, âge, résultat du test biologique) en s'affranchissant des bornes de normalité qu'un laboratoire définit en fonction des tests et des populations (enfant, adulte homme, adulte femme et tout les sous ensembles liés à l'âge ). Plus ambitieux, j'ai tenté d'entrainer le model avec des graphes de résultats afin de pouvoir les valider automatiquement. 

C’était dans le cadre d’un hackathon interne, et c’est resté dans les cartons, sacrifié sur l’autel des priorités. Il faut dire que les résultats n’étaient pas non plus hyper concluants : les fameuses règles du système expert étaient bien suffisantes pour arriver au même résultat, les types de variables d’entrée étant plutôt limités. J'avais remarqué d'ailleurs que c'etaient les algorithmes à base d’arbres de décision qui avaient fourni le modèle le plus concluant étant donné que je les avais entraînés sur des données déjà classées en amont…. En clair, le modèle de machine learning n’a fait que "retrouver" ce qu’on lui avait déjà appris : on tourne un peu en rond, dans un cercle fermé où l’IA ne fait finalement que valider le travail du système expert initial.

eg. if sexe= homme and if age <10y then population=Child

J’étais donc un peu resté sur ma faim, avec l’idée de reprendre un jour ce sujet et de trouver un domaine d’application plus pertinent. C’est toujours un peu ça la difficulté : il y a plein d’exemples qui tournent parfaitement dans les tutos, mais dès qu’on veut appliquer à nos problématiques métier, ça devient tout de suite beaucoup moins trivial ou moins conluant!



