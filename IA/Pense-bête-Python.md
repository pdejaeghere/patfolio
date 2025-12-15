---
title: Pense-bête-Python!
layout: default 
nav_order:  5
parent: IA
---

# Pense-bête-Python!

Lors de ma carrière, j'ai travaillé essentiellement avec les langages C,C++ (principalement en utilisant l'ecosystème MFC de microsoft mais aussi les stl ), et surtout .Net avec C# (framework 3->4.8  ainsi que la version multiplateforme et open sources Net core -> Net 10.0 ).  Bien entendu, pendant les études, de nombreux langages ont été très formateurs: Basic,Pascal, Ada, SmallTalk, Lisp, Prolog. 
Je n'oublie pas non plus les langages 'systèmes', ruby (via le devops Chef) et Powershell( que je n'aime pas trop mais qui est un peu obligé sous Windows car bien intégré) ni les langages Web, JavaScript, Typescript et leurs quantités impressionnantes de framework graphique (D3.js, mxgraph pour avoir joué avec). Java est un peu à part car on aurait pu l'adopter complètement dans l'entreprise mais le choix a été supplanté par C#, cohérence autours des outils Microsoft oblige. 

Par contre, je n’avais jamais eu l’occasion de pratiquer Python ; voilà donc l’opportunité, d’autant plus qu’il s’impose clairement comme le langage de référence pour l’IA.

Côté .NET, il existait il y a quelques années Accord.NET, mais le projet ne semble plus réellement maintenu. Aujourd’hui, si l’on souhaite travailler en .NET, il faut plutôt se tourner vers ML.NET, éventuellement combiné à Math.NET pour la manipulation de matrices et le calcul numérique. On aurait pu imaginer aussi que couplé à F#, orienté scientifique, on avait là le trio gagnant sur lequel miser notre effort (Cela dépend aussi du cœur de métier et de la culture d'entreprise).
Mais c'est toujours Python qui reste au devant de la scène. Est-ce une question de timing — un peu comme JavaScript, qui peine à être totalement supplanté par TypeScript — ou bien une image trop fortement associée à Microsoft ?

Bref, Maîtriser Python semble donc aujourd’hui incontournable, et il n’est de toute façon jamais inutile de se former à un nouveau langage. D’autres mériteraient aussi que je m’y intéresse à l’occasion — Rust, Go — mais évitons de trop nous disperser : c’est bien souvent le danger.

## Installation


:~/miniforge3/envs/sage
conda activate sage
conda install numpy pandas matplotlib seaborn scikit-learn

pip install torch tensorflow

 ./sage -n jupyter


conda env: sage (Python 3.11)

1️⃣ Installer l’extension Remote - WSL

Dans VS Code (Windows) :

Extensions → cherche “Remote - WSL”

Installe-la

C’est tout pour Windows.

2️⃣ Ouvrir VS Code depuis WSL

Dans ton terminal WSL :

cd ton_projet
code .

➡️ La première fois :

VS Code va installer automatiquement un petit serveur dans WSL

tu verras en bas à gauche :
WSL: Ubuntu (ou autre)

👉 À partir de là, tu travailles réellement dans WSL.

3️⃣ Sélectionner ton Python conda

Dans VS Code (connecté à WSL) :

Ctrl + Shift + P

Python: Select Interpreter

choisis :

conda env: sage (Python 3.11)

✅ Terminé.

Et Jupyter dans tout ça ?

Deux options, au choix :

Option A — Notebooks directement dans VS Code (recommandé)

Installe l’extension Jupyter

Ouvre un .ipynb

Sélectionne le kernel :

Python (sage)

👉 Tu n’as même plus besoin de lancer ./sage -n jupyter à la main.

Option B — Continuer ton Jupyter “classique”

Tu peux aussi :

./sage -n jupyter

et ouvrir le navigateur comme avant.

VS Code est optionnel, pas obligatoire.


# Environnement Python / Machine Learning – Résumé

Ce document résume les outils et concepts que tu utilises (ou peux utiliser) autour de Python, du machine learning et du calcul scientifique, dans un contexte **WSL + conda**.

---

## 1. Miniforge

### Qu’est-ce que c’est ?

**Miniforge** est une distribution minimale de **conda**, basée sur **conda-forge**.

* Alternative légère à Anaconda
* Ne contient que le strict nécessaire
* Pas de packages préinstallés inutiles

### À quoi ça sert ?

* Installer et gérer des environnements Python isolés
* Installer des bibliothèques scientifiques sans casser le système

### Avantages

* Léger
* Prévisible
* Idéal pour WSL, Docker, serveurs

---

## 2. conda

### Qu’est-ce que c’est ?

**conda** est un gestionnaire :

* d’environnements
* de packages (Python *et* non-Python)

### Environnement conda

Un environnement conda est :

* un Python isolé
* avec ses propres bibliothèques
* indépendant du reste du système

### Commandes essentielles

```bash
conda create -n mon_env python=3.11
conda activate mon_env
conda deactivate
conda env list
```

---

## 3. Python

### Rôle

Python est le langage principal pour :

* machine learning
* data science
* calcul scientifique

### Dans ton setup

* Python est installé **via conda**
* Chaque environnement a sa propre version de Python

---

## 4. SageMath

### Qu’est-ce que c’est ?

**SageMath** est un système de calcul mathématique (CAS).

Il combine :

* Python
* NumPy / SciPy
* outils de calcul symbolique

### Installation (idée générale)

Sage est souvent installé séparément, puis utilisé avec Python/Jupyter.

### Particularité

Sage peut lancer son propre serveur Jupyter :

```bash
./sage -n jupyter
```

Cela permet d’utiliser :

* Python
* Sage
* dans des notebooks

---

## 5. Jupyter

### Qu’est-ce que c’est ?

**Jupyter Notebook** est une interface interactive basée sur le navigateur.

Elle permet de mélanger :

* code
* texte
* équations
* graphiques

### Les cellules

Un notebook est composé de **cellules**.

#### Cellules de code

* Contiennent du Python (ou Sage)
* S’exécutent avec `Shift + Enter`

#### Cellules Markdown

* Contiennent du texte formaté
* Servent à expliquer le raisonnement

### Pourquoi c’est très utilisé en ML

* Raisonnement pas à pas
* Visualisation immédiate
* Idéal pour l’apprentissage

---

## 6. Spyder

### Qu’est-ce que c’est ?

**Spyder** est un IDE scientifique, proche de MATLAB.

Il propose :

* éditeur de code
* console interactive
* explorateur de variables

### Lancement dans WSL

Spyder doit être :

* installé dans l’environnement conda
* lancé depuis WSL

```bash
conda activate sage
spyder
```

Avec WSLg :

* l’interface graphique s’affiche sous Windows
* le code s’exécute dans WSL

---

## 7. Visual Studio Code (VS Code)

### Qu’est-ce que c’est ?

VS Code est un éditeur / IDE généraliste, très extensible.

### Avec WSL

VS Code Windows peut :

* se connecter à WSL
* éditer les fichiers Linux
* exécuter Python dans WSL

Extension clé :

* **Remote – WSL**

### Avantages

* Très bon pour les projets longs
* Support des notebooks Jupyter
* Debugging puissant

---

## 8. WSL (Windows Subsystem for Linux)

### Qu’est-ce que c’est ?

WSL permet d’exécuter Linux directement sous Windows.

### Rôle dans ton setup

* Linux réel (Ubuntu, Debian…)
* Meilleure compatibilité avec Python scientifique
* Environnement propre et isolé de Windows

### Architecture simplifiée

```
Windows
  └── VS Code / Navigateur
        └── WSL (Linux)
              └── conda
                    └── Python / Sage / ML
```

---

## 9. Comparaison rapide des outils

| Outil     | Rôle principal                   |
| --------- | -------------------------------- |
| Miniforge | Installer conda minimal          |
| conda     | Gérer environnements & packages  |
| Python    | Langage principal                |
| Sage      | Calcul mathématique              |
| Jupyter   | Notebooks interactifs            |
| Spyder    | IDE scientifique                 |
| VS Code   | IDE généraliste                  |
| WSL       | Environnement Linux sous Windows |

---

## 10. Philosophie générale

* **WSL + conda** : apprendre, expérimenter
* **Jupyter** : comprendre et explorer
* **VS Code** : structurer et faire évoluer
* **Docker** : plus tard, pour la reproductibilité

👉 Ton setup actuel est **cohérent, moderne et suffisant** pour apprendre le machine learning.
