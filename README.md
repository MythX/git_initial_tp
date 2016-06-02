# Formation Git Initiale

## Exercice 1 : Commandes de base :
But de l'exercice : Cloner un dépôt et faire ses premiers commits

1. Verifier la configuration de Git (username, mail, mergetool, etc...)
* Cloner le depot (https://github.com/MythX/git_initial_tp)
* Modifier `file3.txt` et ajouter le à l'index
* Commiter
* Modifier `file1.txt` et ajouter le à l'index
* Commiter
* Afficher l'historique et vérifier que vos commits sont présents

## Exercice 2 : Branches/merges
#### Etape 1 :
1. Se positionner sur la branche `master` et créer une branche `develop`
* Créer une branche `feature1` à partir de `develop`
* Modifier `file1.txt`
* Créer un fichier `file4.txt` dans `dir1/` et supprimer `file2.txt`
* Faites vos commits

#### Etape 2:
1. Revenir sur `develop`
* Modifier `file1.txt`
* Modifier `file2.txt`
* Modifier `file3.txt`
* Faites vos commits
* Afficher l'historique

#### Etape 3:
1. Merger la branche `feature1` sur `develop`
* Gérer les conflits potentielle
* Utiliser votre mergetool pour résoudre le conflit
* Commiter le résultat du merge
* Afficher l'historique. L'historique vous parez-t-il "propre" ?

#### Etape 4:
1. Annuler le commit de merge
* Retourner sur `feature1`
* Mettre à jour `feature1` par rapport à `develop`
* Aller sur `develop`
* Merger la branche `feature1` sur `develop` (no fast forward)
* Supprimer la branche `feature1`

## Exercice 3 : Rebase interactif
But de l'exercice est de prendre en main le git rebase interactif

#### Etape 0 : Preparation
1. Modifier `file2.txt` et commiter la modification
* Supprimer `file1.txt`, ajouter `file6.txt` et commiter (1 seul commit)
* Ajouter `file5.txt` à la racine et commiter

#### Etape 1 : Changer l'ordre de 2 commits
On souhaite modifier l'ordre des 3 derniers commits.
1. Entrer dans le mode interactif et specifiant jusqu'où remonter (git rebase -i HEAD~3)
* Inverser l'ordre du 1er et du dernier commit
* Enregistrer la modification

#### Etape 2 : Séparer un commit en plusieurs
On souhaite séparer le commit qui a créé `file6.txt` et supprimer le `file1.txt`.
1. Entrer dans le mode interactif et specifiant jusqu'où remonter (git rebase -i HEAD~2)
* Sur la ligne du commit cible, changer le `pick` en `edit`
* Enregistrer la modification
* Annuler tous les changements effectués depuis le commit parent (HEAD^) (git reset HEAD^)
* Ajouter les modifications que vous voulez commiter, dans un 1er temps la suppresion de file1.txt et commiter
* Ajouter le reste (ajout de `file6.txt`) et commiter
* Terminer en continuant le rebase
* Afficher l'historique et vérifier que vous avez bien le résultat attendu

#### Etape 3 : Supprimer un commit
L'ajout de file6.txt était une erreur, il faut supprimer le commit (il faut préférer un git revert en général pour éviter d'autres problème)
1. Entrer dans le mode interactif et specifiant jusqu'où remonter (git rebase -i HEAD~2)
* Supprimer la ligne qui correspond à l'ajout de file6.txt
* Enregistrer la modification

#### Etape 4 : Fusionner des commits
On a finit notre travail et on voudrait pousser un seul commit. Il faut donc fusionner les 3 commits
1. Entrer dans le mode interactif et specifiant jusqu'où remonter (git rebase -i HEAD~3)
* Remplacer `pick` par `squash` sur les 2 derniers commits
* Enregistrer la modification

