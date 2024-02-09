---
title: TP Gestion de versions avec Git
author: WASSON Baptiste
---

TP Gestion de versions avec Git - Baptiste WASSON
=

## B1-Git - Partie 1 : Création du dépôt et _commits_

- Ouvrir un terminal (terminal _Git Bash_ à privilégier)

- Créer, en ligne de commande, un répertoire `tp-git`

```bash 
mkdir tp-git 
```

- Se déplacer dans le répertoire

```bash
cd tp-git
```

- Vérifier qu'on est dans le bon répertoire en affichant le chemin du répertoire courant

```bash
pwd
```

- Initialiser un dépôt Git

```
git init
```

- Lister tous les fichiers du répertoire (y compris les fichiers cachés) pour s'assurer que le répertoire `.git` à été créé

```bash
ls -la
```

- Ouvrir ce répertoire sous VS Code

```
code .
```

- Exécuter `git status` et copier/coller la sortie

```
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

- Créer le fichier `fichier1.md` avec un contenu quelconque et l'enregistrer (vous pouvez utiliser VS Code pour créer et éditer des fichiers)

  - Attention, il s'agit bien de créer un nouveau fichier, et non un répertoire. Il en sera de même tout au long de ce TP.

- Créer le fichier `fichier2.md` avec un contenu quelconque et l'enregistrer

- Exécuter `git status` et copier/coller la sortie

```
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        fichier1.md
        fichier2.md

nothing added to commit but untracked files present (use "git add" to track)
```

- Ajouter `fichier1.md` à l'index de Git (zone de _Staging_)

```
git add fichier1.md
```

- Exécuter `git status` et copier/coller la sortie

```
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   fichier1.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        fichier2.md
```

- Créer un _commit_ avec pour message : "Ajout de fichier1.md"

```
git commit -m "Ajout du fichier1.md"
```

- **_VALIDATION PROF01_**

- Exécuter `git status` et copier/coller la sortie

```
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        fichier2.md

nothing added to commit but untracked files present (use "git add" to track)
```

- Modifier `fichier1.md` et enregistrer

- Exécuter `git status` et copier/coller la sortie

```
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   fichier1.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        fichier2.md

no changes added to commit (use "git add" and/or "git commit -a")
```

- Ajouter `fichier1.md` et `fichier2.md` à la zone de _Staging_

```
git add .
```

- Créer un _commit_ "Ajout de fichier2.md et modification de fichier1.md"

```
git commit -m "Ajout de fichier2.md et modification de fichier1.md"
```

- Exécuter `git status` et copier/coller la sortie

```
On branch master
nothing to commit, working tree clean
```

- Copier/coller l'ID des deux premiers _commits_ (utiliser `log`) :

  - ID _commit_ 1 : **25ab0159f154462c1fda7ce757f505ec442a875e**
  - ID _commit_ 2 : **efe8aa1f38d16b13447a4473b5eb416ce0c72202**

- Que signifie qu'un fichier est "_tracked_" ou "_untracked_" ?

> _tracked_ : Le fichier est suivi par git, il a été ajouté avec la commande `git add`

> _untracked_ : Le fichier n'est pas suivi par git, il n'est pas commit. Il n'y a donc pas d'historique de version.

- Pourquoi doit-on passer les fichiers par la zone de _Staging_ (l'index) avant de les committer ?

>  Pour être sur de commit les bon fichiers

- **_VALIDATION PROF02_**

## B1-Git - Partie 2 : Gestion de branches

_Cette partie est à faire sur le même dépôt que la partie précédente. C'est la suite._

- Créer une branche `fonctionnalite1`

```
git branch fonctinnalite1
```

- Lister les branches

```
git branch
```

- Se déplacer sur la branche `fonctionnalite1`

```
git switch fonctionnalite1
```

- Lister les branches

```
git branch
```

- Que représente l'étoile à côté des noms des branches ?

> ça représente la branche dans laquelle on est

- Créer un nouveau fichier `fichier3.md`

- Modifier le fichier `fichier2.md`

  - Comment utiliser VS Code pour qu'il nous montre les différences entre l'ancienne version de `fichier2.md` et la version courante que l'on vient d'éditer ?

  > utiliser la raccourci clavier : `Ctrl + Shift + G`

- Committer ces deux modifications : "Fonctionnalité 1 - première phase"

```
git add .
git commit -m "Fonctionnalité 1 - première phase"
```

- Créer un nouveau fichier `fichier4.md`

- Modifier de nouveau le fichier `fichier2.md`

- Committer ces deux modifications : "Fonctionnalité 1 - terminée"

```
git add .
git commit -m "Fonctionnalité 1 - terminée"
```

- **_VALIDATION PROF03_**

- Afficher la liste des fichiers du répertoire

```bash
ls
```

- Se déplacer sur la branche `master`

```
git switch master
```

- Afficher la liste des fichiers du répertoire

```
ls
```

- Pourquoi les deux sorties sont-elles différentes ? Les fichiers ont-ils disparus ?

> Les fichiers sont stockés dans 2 branches différentes. ça ressemble à 2 répertoires différents.

- Créer une nouvelle branche `fonctionnalite2`

```
git branch fonctionnalite2
```

  - Cette branche ne va pas avoir toutes les données incluses dans `fonctionnalite1`. Pourquoi ?
  
  > Parce que les fichiers ont été commit dans la branche `fonctionnaite1`. C'est comme ci ils etaient enregistrés dans un autre répertoire.

  - Qu'aurait-il fallu faire si on avait souhaité démarrer la branche `fonctionnalite2` en intégrant les modifications récentes de `fonctionnalite1` ?

  > Creer la branche `fonctionnalite2` en étant dans la branche `fonctionnalite1`

- Se déplacer sur la nouvelle branche `fonctionnalite2`

```
git switch fonctionnalite2
```

- Créer un nouveau fichier `fichier5.md`

- Faire un _commit_ intégrant cette ajout : "Ajout fichier5.md"

```
git add fichier5.md
git commit -m "Ajout fichier5.md"
```

- Entrer la commande `git log --oneline --decorate --graph --all` pour visualiser, sur le terminal, le graphe des _commits_ sur toutes les branches

```
* e4d5c5b (HEAD -> fonctionnalite2) Ajout fichier5.md
| * 61b4532 (fonctionnalite1) Fonctionnalité 1 - terminée
| * fc31870 Fonctionnalité 1 - première phase
|/
* efe8aa1 (master) <U+0096>Ajout de fichier2.md et modification de fichier1.md
* 25ab015 Ajout du fichier1.md
```

  - Noter la « déviation » entre les deux branches, à partir de la branche `master` (schématisée sous forme de traits)
  - l'option `--all` permet de visualiser toutes les branches, pas seulement celle sur laquelle on est
  - l'option `--oneline` affiche les _commits_ sur une seule ligne
  - l'option `--graph` affiche le log sous forme de graphe
  - (utilisez si besoin les touches haut/bas pour naviguer dans la sortie de cette commande et `Q` pour quitter)

- Installer l'extension VS Code _Git Graph_ et visualiser le graphe actuel des _commits_ à l'aide de cette extension

  - Sur cette représentation, que représente les points ?

  > Les commits

  - Comment voit-on sur quelle branche on est actuellement ?

  > Le nom de la branche est en **gras**

- **_VALIDATION PROF04_**

## Partie 3 - Fusionner des branches

_Cette partie est à faire sur le même dépôt que la partie précédente. C'est la suite._

- On considère que la branche originale (`master` ou `main`) est la branche d'intégration, c'est-à-dire celle qui va contenir l'historique de toutes les modifications développées au fur et à mesure dans les branches annexes

- Se déplacer sur la branche `master`

```
git branch master
```

  - Noter le changement dans l'onglet _Git Graph_

- On va maintenant intégrer la branche `fonctionnalite1`, qui est terminée, dans la branche d'intégration (ça s'appelle une _fusion_, ou un _merge_) : fusionner avec la branche `fonctionnalite1`

```
git merge fonctionnalite1
```

- Noter le changement dans l'onglet _Git Graph_. Que signifie la mention _Fast-forward_ indiquée par la sortie de la commande ?

> Au lieu de faire une vraie fusion, git deplace la pointe de la branche actuelle vers celle de la branche cible. Pour cela, il faut qu'il n'y ai pas de nouveaux commit.

- On veut maintenant fusionner `fonctionnalite2` dans la branche d'intégration (`master`). Effectuer cette fusion.

```
git merge fonctionnalite2
```

- Noter le changement dans l'onglet _Git Graph_. Que signifie la mention _Merge made by the ... strategy_ indiquée par la sortie de la commande ?

> la stratégie ort (Ostenably Recursive's Twin) est la stratégie de fusion par défaut. Cette stratégie est capable de prendre en compte de nombrex renommage

- Quelle est la différence fondamentale avec la fusion précédente ?

> 

- Créer une nouvelle branche `fonctionnalite3`, se déplacer dessus, et modifier le fichier `fichier1.md` en y ajoutant une ligne de texte. Committer : "Modification fichier1 pour fonctionnalité 3"

```
git branch fonctionnalite3
git switch fonctionnalite3
git add fichier1.md
git commit -m "Modification fichier1 pour fonctionnalité 3"
```

  - Comment utiliser _Git Graph_ pour qu'il nous montre les différences entre l'ancienne version de `fichier1.md` et la version courante que l'on vient de committer ?

  > il suffit de cliquer sur **Uncommited changes** et sur le fichier pour voir les changements

- Repartir sur `master`, et modifier `fichier1.md` en y ajoutant aussi une ligne (différente de celle qu'on a ajoutée sur l'autre branche) ; ajouter à l'index et _commit_

```
git switch master
git add fichier1.md
git commit -m "update fichier1 pour fonctionnalité 1"
```

- Tenter de fusionner la branche `fonctionnalite3` avec `master`

```
git merge fonctionnalite3
```

```
Auto-merging fichier1.md
CONFLICT (content): Merge conflict in fichier1.md
Automatic merge failed; fix conflicts and then commit the result.
```

  - Que se passe-t-il et pourquoi ?

  > Il y a un conflit dans le fichier1. Des modifications ont etaient faites dans les 2 branches

- Lancer un `git status`

```
On branch master
Your branch is ahead of 'origin/master' by 9 commits.
  (use "git push" to publish your local commits)

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   fichier1.md
```

  - Que doit-on faire si on veut annuler la fusion en cours ? (**ne pas lancer la commande**)

  > Il faut faire `git merge --abort`

- On veut résoudre le conflit. Plusieurs possibilités :

  - Conserver uniquement les modifications faites dans `fonctionnalite3`
  - Conserver uniquement les modifications faites dans `master`
  - Conserver les deux modifications
  - Supprimer les deux modifications ou remanier sensiblement le fichier pour les intégrer correctement

- Git nous laisse totalement la main et ne va pas essayer d'imposer l'un de ces choix pour nous, ni nous assister dans l'application automatique de l'un d'entre eux : il faut examiner le(s) fichier(s) en conflit et éditer nous-mêmes

- Ouvrir le fichier en question sous VS Code

  - La chaîne `<<<<<<<<<<` marque le début du conflit
  - La chaîne `>>>>>>>>>>` marque la fin du conflit
  - La chaîne `==========` sépare les deux versions

- Éditer le fichier pour faire en sorte d'intégrer les deux modifications ; à la fin de l'édition :

  - Il ne doit plus y avoir de marques quelconques en dehors des ajouts fonctionnels originaux, c'est-à-dire pas de `<<<<<<<<<<`, ni de mentions de nom de branche, etc. : vous rendez le fichier tel qu'il doit apparaître dans le _commit_ de fusion, avec les conflits résolus manuellement
  - Sauvegarder

- Ajouter les modification à l'index et committer

```
git add fichier1.md
git commit -m "modification fichier1.md"
```

- NB : parfois, plusieurs fichiers sont en conflit ; le processus est identique, il faut juste résoudre les conflits sur tous les fichiers

- NB : les conflits de fusion sont fréquents lorsqu'on travaille en collaboration (plusieurs personnes vont travailler sur le même fichier pour remplir deux fonctionnalités différentes)

- Les branches créées n'ont plus de raison d'exister

  - Elles avaient pour but de créer une déviation afin de travailler sur des fonctionnalités individuelles, sans interférer avec le travail des autres, avant de les fusionner dans la branche d'intégration
  - On va vouloir nettoyer le dépôt en les supprimant
  - Cela ne va bien sûr pas supprimer tous les _commits_ qui y sont associés
  - Attention cependant d'éviter en général de supprimer une branche qui n'a pas encore été intégrée à la branche d'intégration, sauf on souhaite vraiment abandonner le développement de cette branche
  - Ne pas réutiliser une branche qui a déjà été intégrée pour démarrer une nouvelle piste : toujours utiliser une nouvelle branche
  - Nouvelle tâche ? => nouvelle branche à partir d'un _commit_ de la branche d'intégration (en général le plus récent)
  - Tâche terminée ? => fusion dans la branche d'intégration et suppression de la branche

- Supprimer les trois branches `fonctionnalitex` (attention : on ne peut pas supprimer une branche sur laquelle on est)

```
git branch -D fonctionnalite1
git branch -D fonctionnalite2
git branch -D fonctionnalite3
```

## Partie 4 - Travailler avec un dépôt distant (_remote_)

- Faire un _fork_ du dépôt https://github.com/rose-line/sio1-2024-java-grpa (pas par commande Git, c'est sur l'interface GitHub)

- Cloner localement votre _fork_ (**ne pas cloner le dépôt original**)

```
git clone https://github.com/brvslow/sio1-2024-java-grpb
```

  - Quelle est la différence entre un _fork_ et un clonage ?
  - Indiquer dans quelles circonstances on voudrait _forker_ et/ou cloner un dépôt

  > Un fork crée un 2ème dépot alors qu'un clone copie le dépot original. Il est donc impossible de modifier le dépot distant en cas de clonage si on est pas collaborateur. Il est possible de faire des modifications locales. Avec un fork, le depot nous appartient et il est possible de push les commits sur github.

- Modifier le fichier `README.md` à la racine du dépôt en ajoutant une ligne quelconque

- On veut maintenant envoyer cette modification vers le dépôt distant

  - Il faut d'abord faire un _add/commit_ local

  ```
  git add README.md
  git commit -m "ajout d'une ligne quelconque"
  ```

  - Puis utiliser la commande qui « pousse » les modifs sur le dépôt GitHub (_push_)
  - Vérifier directement sur GitHub que le _push_ a bien fonctionné

- Trouver la commande qui affiche le nom du ou des dépôt(s) distant(s) relié(s) avec le dépôt local : cela permet de savoir si le dépôt courant est synchronisé avec un dépôt en ligne ou non

```
git remote -v

origin  https://github.com/brvslow/sio1-2024-java-grpb (fetch)
origin  https://github.com/brvslow/sio1-2024-java-grpb (push)
```

- On va faire un _merge_ en local puis *push* :

  - Créer une branche locale `bugfix1`, se déplacer dessus, créer un nouveau fichier `ok.java` à la racine du dépôt

  ```
  git branch bugfix1
  git switch bugfix1
  ```

  - Ajouter `ok.java` à l'index et faire un _commit_

  ```
  git add ok.java
  git commit -m "ajout du fichier ok.java"
  ```

  - Retourner sur `master`, créer le fichier `ajout.java`, ajouter à l'index et committer

  ```
  git switch master
  git add ajout.java
  git commit -m "ajout du fichier ajout.java"
  ```

  - Fusionner la branche `bugfix1` dans la branche `master`

  ```
  git merge bugfix1
  ```

  - Afficher le log des *commits* ; noter les emplacements des trois branches différentes, en local et en remote

  ```
  $ git log
  commit 75877b9ff4fd57e005cf5fc5bd5bee60492bbe2a (HEAD -> master)
  Merge: cf198ee 5ebda2c
  Author: Baptiste Wasson <baptiste.wasson@gmail.com>
  Date:   Fri Feb 9 09:21:21 2024 +0100

      Merge branch 'bugfix1'

  commit cf198eeade882718c1a0cb3be85fffae53df1e90
  Author: Baptiste Wasson <baptiste.wasson@gmail.com>
  Date:   Fri Feb 9 09:20:17 2024 +0100

      ajout du fichier ajout.java

  commit 5ebda2ce6f51053386c9d56cf8298d9b13bb6f45 (bugfix1)
  Author: Baptiste Wasson <baptiste.wasson@gmail.com>
  Date:   Fri Feb 9 09:17:16 2024 +0100

      ajout du fichier ok.java

  commit 7c61999a31a3bee224e2074738e10f4411194bfa (origin/master, origin/HEAD)
  Author: Baptiste Wasson <baptiste.wasson@gmail.com>
  Date:   Fri Feb 9 09:07:55 2024 +0100

      ajout d'une ligne quelconque

  commit 34f22029a8e568d5ecb71811bb590b8bbbd059a1
  Author: pgahide <patrice.gahide@gmail.com>
  Date:   Tue Oct 11 12:20:50 2022 +0200

      fin cours 11/10

  commit 23a5036be535f3d0be6eed6f42d7e26f9ade6ea9
  Author: pgahide <patrice.gahide@gmail.com>
  Date:   Thu Sep 29 10:36:13 2022 +0200

      comm bidon

  commit 20195439f43a792f0eb43b9d927fd8c08f39d40c
  Author: pgahide <patrice.gahide@gmail.com>
  Date:   Tue Sep 27 12:15:32 2022 +0200

      fin de cours 27/09

  commit 368ce64181df39fbd135f885a7831199ae2b4213
  Author: pgahide <patrice.gahide@gmail.com>
  Date:   Tue Sep 27 08:48:23 2022 +0200

      first commit
  ```

  ```
  $ git log origin/master
  commit 7c61999a31a3bee224e2074738e10f4411194bfa (origin/master, origin/HEAD)
  Author: Baptiste Wasson <baptiste.wasson@gmail.com>
  Date:   Fri Feb 9 09:07:55 2024 +0100

      ajout d'une ligne quelconque

  commit 34f22029a8e568d5ecb71811bb590b8bbbd059a1
  Author: pgahide <patrice.gahide@gmail.com>
  Date:   Tue Oct 11 12:20:50 2022 +0200

      fin cours 11/10

  commit 23a5036be535f3d0be6eed6f42d7e26f9ade6ea9
  Author: pgahide <patrice.gahide@gmail.com>
  Date:   Thu Sep 29 10:36:13 2022 +0200

      comm bidon

  commit 20195439f43a792f0eb43b9d927fd8c08f39d40c
  Author: pgahide <patrice.gahide@gmail.com>
  Date:   Tue Sep 27 12:15:32 2022 +0200

      fin de cours 27/09

  commit 368ce64181df39fbd135f885a7831199ae2b4213
  Author: pgahide <patrice.gahide@gmail.com>
  Date:   Tue Sep 27 08:48:23 2022 +0200

      first commit
  ```

  - Faire un _push_
  
  ```
  git push
  ```

  - Refaire un affichage du log ; `origin/master` a bougé : que représente cette branche ?

  ```
  $ git log origin/master
  commit 75877b9ff4fd57e005cf5fc5bd5bee60492bbe2a (HEAD -> master, origin/master, origin/HEAD)
  Merge: cf198ee 5ebda2c
  Author: Baptiste Wasson <baptiste.wasson@gmail.com>
  Date:   Fri Feb 9 09:21:21 2024 +0100

      Merge branch 'bugfix1'

  commit cf198eeade882718c1a0cb3be85fffae53df1e90
  Author: Baptiste Wasson <baptiste.wasson@gmail.com>
  Date:   Fri Feb 9 09:20:17 2024 +0100

      ajout du fichier ajout.java

  commit 5ebda2ce6f51053386c9d56cf8298d9b13bb6f45 (bugfix1)
  Author: Baptiste Wasson <baptiste.wasson@gmail.com>
  Date:   Fri Feb 9 09:17:16 2024 +0100

      ajout du fichier ok.java

  commit 7c61999a31a3bee224e2074738e10f4411194bfa
  Author: Baptiste Wasson <baptiste.wasson@gmail.com>
  Date:   Fri Feb 9 09:07:55 2024 +0100

      ajout d'une ligne quelconque

  commit 34f22029a8e568d5ecb71811bb590b8bbbd059a1
  Author: pgahide <patrice.gahide@gmail.com>
  Date:   Tue Oct 11 12:20:50 2022 +0200

      fin cours 11/10

  commit 23a5036be535f3d0be6eed6f42d7e26f9ade6ea9
  Author: pgahide <patrice.gahide@gmail.com>
  Date:   Thu Sep 29 10:36:13 2022 +0200

      comm bidon

  commit 20195439f43a792f0eb43b9d927fd8c08f39d40c
  Author: pgahide <patrice.gahide@gmail.com>
  Date:   Tue Sep 27 12:15:32 2022 +0200

      fin de cours 27/09

  commit 368ce64181df39fbd135f885a7831199ae2b4213
  Author: pgahide <patrice.gahide@gmail.com>
  Date:   Tue Sep 27 08:48:23 2022 +0200

      first commit
  ```


- Étudier le résultat sur GitHub, en examinant _commits_ et branches (bouton _drop-down_ sur la page du dépôt pour voir les branches) : qu'est-ce qui est différent de la version locale ?

> La branch **bugfix1** n'a pas était push

- Le bug est corrigé et intégré ; que doit-on faire de la branche `bugfix1` maintenant ?

> On peut maintenant supprimer la branch **bugfix1**

- **_VALIDATION PROF06_**

- Supposons que l'on veuille effectivement publier sur le _remote_ une branche sur laquelle on travaille (pour sauvegarde ou pour que d'autres puissent l'utiliser)

  - Créer une nouvelle branche `partage`
  - Aller sur la branche
  - Ajouter un fichier `partage.md`
  - L'inclure dans l'index
  - Faire un _commit_
  - _Push_
  - Que se passe-t-il ?
  - Exécuter la bonne commande pour sauvegarder la branche sur le remote
  - Vérifier sur GitHub que la branche apparaît bien

- La branche `partage` n'a pas été fusionnée avant le *push* ; on va utiliser un autre moyen offert par GitHub pour fusionner une branche en *remote* : la **_Pull Request_**

  - La _Pull Request_ est très utilisée en collaboration : elle permet à l'intégrateur du projet d'examiner les demandes de _merge_ au niveau du _remote_ avant de les accepter (ou non)

- Sur GitHub, cliquer sur le bouton _Compare & pull request_, qui apparaît directement sur la page du dépôt depuis le dernier _push_ qui a ajouté la branche (voir ci-dessus).

- À gauche, la branche d'intégration (« *base* », qui reçoit le _merge_) ; à droite, la branche à fusionner (« *compare* »)

  - On doit fusionner `partage` dans `master`
  - Attention, il faut bien choisir le repo de base qui est sur votre propre compte (pas le compte du dépôt d'origine que vous avez _forké_)
  - On peut ajouter d'autres informations : titre et commentaire de la _pull request_, et même upload de fichiers annexes, liens éventuels... Également, on peut ajouter des labels pour étiquetter la _pull request_ et lui affecter un _reviewer_, qui va officiellement être en charge
  - Valider en cliquant sur le bouton _Create pull request_

- La page résultante informe sur les branches source et cible, sur les _commits_ concernés, les fichiers qui ont été modifiés...

- On peut aussi y démarrer une conversation notamment entre l'émetteur de la _pull request_ et l'intégrateur

- On voit que l'intégrateur (possesseur du compte cible) peut accepter la _pull request_ en cliquant sur le bouton _Merge pull request_ (ou refuser en cliquant sur _Close pull request_).

- En discutant de la _pull request_, on se rend compte que certaines choses devraient être modifiées

  - Repartir en local pour effectuer une modification sur `partage.md` et ajouter `precision.md`
  - _Commit_ des deux modifs
  - _Push_
  - Observer la *pull request* : que s'est-il passé ?
  - Finalement, faire le _merge_ sur la page de la _pull request_
  - Noter que l'interface nous propose alors de supprimer la branche devenue inutile ; supprimer la branche

- Dans un contexte de travail en collaboration sur un même dépôt, donner un _workflow_ (façon de travailler) possible qui va permettre à tous les intervenants de viser des ajouts à la branche d'intégration, d'en discuter, et ceci sans danger pour la branche d'intégration, avant que finalement l'intégrateur (probablement propriétaire du dépot) accepte les changements.

- **_VALIDATION PROF07_**