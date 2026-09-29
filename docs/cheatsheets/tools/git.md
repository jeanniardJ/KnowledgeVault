# Git

> Category: Tools
> Scope: Commands and workflows
> Difficulty: Beginner to Imtermediate
> Status: Draft

## Purpose

Référence rapide des commandes Git les plus courantes pour gérer un dépôt local et le synchroniser avec un dépôt distant.

## Configuration

### Configure user identity

Configurer l'identité utilisée pour les commits :

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@exemple.com"
```

### Display configuration

Afficher la configuration Git : 

```bash
git config --list
```

## Repository initialization

### Initialize a repository

Initialiser un nouveau dépôt Git :

```bash
git init
```

### Clone a repository

Cloner un dépôt distant :

```bash
git clone https://github.com/OWNER/REPOSITORY.git
```

### Display repository status

Afficher l'état du dépôt :

```bash
git status
```

## Files and changes

### Display changes

Afficher les modifications non indexées :

```bash
git diff
```

### Stage a file

Ajouter un fichier à la zone de préparation :

```bash
git add path/to/file.md
```

### Stage all changes

Ajouter toutes les modifications à la zone de préparation :

```bash
git add .
```

### Unstage a file

Retirer un fichier de la zone de préparation :

```bash
git restore --staged path/to/file.dm
```

### Discard changes in file

Annuler les modifications locales d'un fichier :

```bach
git restore path/to/file.md
```

> Attention : cette commande supprime les modifications non enregistrées dans un commit.

## Commits 

### Create a commiy

Créer un commit avec message explicite :

```bash
git commit -m "Describe the change"
```

### Display commit history

Afficher l'historique des commits :

```bash
git log --online --decorate --graph
```

### Amend the last commit

Modifier le dernier commit :

```bash
git commit --amend
```

## Branches

### List branches

Lister les branches locales :

```bash
git branch
```

### Create a branch

Créer une nouvelle branche :

```bash
git branch feature/my-feature
```

### Create and switch to a branch

Créer une branche et s'y positionner :

```bash
git switch -c feature/my-feature
```

### Switch to a branch

Changer de branche :

```bash
git switch main
```

### Rename the current branch

Renommer la branch courante :

```bash
git branch -M main
```

### Delete a local branch

Supprimer une branche locale :

```bash
git branch -d feature/my-feature
```

### Delete a remote branch

Supprimere une branche distante :

```bash
git push origin --delete feature/my-feature
```

## Remote repositories

### Display remotes

Afficher les dépôts distants configurés :

```bash
git remote -v
```

### Add a remote

Ajouter un dépôt distant :

```bash
git remote add origin https://github.com/OWNER/REPOSITORY.git
```

### Download changes

Récupérer les modifications distantes sans les intégrer :

```bash
git fetch origin
```

### Download and integrate changes

Récupérer et intégrer les modifications distantes :

```bash
git pull
```

### Pull with rebase

Récupérer les modifications en utilisant un rebase :

```bash
git pull --rebase
```

### Push a branch

Publier une branche distante :

```bash
git push -u origin feature/my-feature
```

### Push the current branch

Envoyer les commits de la branche courante :

```bash
git push
```

## Merge and rebase

### Merge a branch

Fusionner une branche dans `main` :

```bash
git swtich main
git merge feature/my-feature
```

### Continue a rebase after resolving conflicts

Poursuivre un rebase après avoir résolu les conflits :

```bash
git add path/to/resolved-file.md
git rebase --continue
```

### Cancel a rebase

Annuler le rebase en cours :

```bash
git rebase --abort
```

### Cancel a merge

Annuler la fusion en cours :

```bash
git merge --abort
```

## Stash

### Temporarily store changes

Mettre temporairement de côté les modifications locales :

```bash
git stash push -m "Work in progress"
```

### List stashes

Lister les modifications mises de côté :

```bash
git stash list
```

### Restore the lastest stash

Restaurer la dernière sauvegarde temporaire :

```bash
git stash pop
```

### Delete the latest stash

Supprimer la dernière sauvergade temporaire :

```bash
git stash drop
```

## Tags

### Create a tag

Créer un tag :

```bash
git tag v1.0.0
```

### List tags

Lister les tags existants :

```bash
git tag
```

### Push a tag

Publier un tag sur le dépôt distant :

```bash
git push origin v1.0.0
```

### Push all tags

Publier tous les tags :

```bash
git push origin --tags
```

## Undo changes

### Undo the last commit and keep changes staged

Annuler le dernier commit en conservant les modifications indexées :

```bash
git reset --soft HEAD~1
```

### Undo the last commit and keep changes unstaged

Annuler le dernier commit en conservant les modifications dans le répertoire de travail :

```bash
git reset HEAD~1
```

### Reset the working tree to the last commit

Réinitialiser le répertoire de travail sur le dernier commit :

```bash
git reset --hard HEAD
```

> Attention : `git reset --hard` supprime définitivement les modifications non enregistrées.

## Conflict resolution

Afficher les fichers en conflit :

```bash
git status
```

1. Ouvrir les fichiers contenant des conflits.
2. Supprimer les marqueurs de conflit.
3. Conserver la version souhaitée.
4. Ajouter les fichiers résolus.

```bash
git add path/to/resolved-file.md
git commit -m "Resolve merge conflict"
```

## Common workflow

Exemple de workflow courant pour modifier la documentation :

```bash
git switch main
git pull -rebase
git switch -c docs/update-flashcards

# Modifier les fichiers
git status
git diff
git add .
git commit -m "docs: update flashcards"
git push -u origin docs/update-flashcards
```

## Useful aliases

Créer des raccourcis Git utiles :

```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.sw switch
git config --global alias.br branch
git config --global alias.lg "log --oneline --decorate --graph"
```

## Related topics

 - Branching
 - Pull requests
 - Merge conflicts
 - Github Actions
 - Semantic commit messages

## Sources

- [Git Documentation](https://git-scm.com/docs)
- [Github Docs](https://docs.github.com/en/get-started/using-git/about-git)