# Exercices Git supplémentaires

Ces exercices se font **uniquement en local** après clonage du dépôt.

## Règles importantes

- La branche `main` ne sert **pas** à ces exercices.
- Les conflits à résoudre sont déjà préparés sur d'autres branches.
- Vous devez travailler sur une **branche personnelle locale** créée à partir de la branche d'exercice demandée.
- Chaque exercice doit être résolu une première fois avec `merge`, puis une autre fois avec `rebase`.

## Vue d'ensemble des branches

- `ex/merge-depart` : point de départ de l'exercice `merge`
- `ex/merge-a-integrer` : branche à fusionner dans l'exercice `merge`
- `ex/rebase-feature` : point de départ de l'exercice `rebase`
- `ex/rebase-base` : branche sur laquelle rebaser dans l'exercice `rebase`

---

## Exercice 1 — Résoudre un conflit avec `merge`

### Objectif

Fusionner deux versions concurrentes d'un planning de sprint et résoudre le conflit manuellement.

### Fichier concerné

- `docs/planning-sprint.txt`

### Préparation

1. Se placer sur la branche de départ : `git checkout ex/merge-depart`
2. Créer une branche locale de travail : `git checkout -b mon-merge`

### Travail demandé

1. Lancer la fusion : `git merge ex/merge-a-integrer`
2. Ouvrir `docs/planning-sprint.txt`
3. Repérer les marqueurs de conflit Git :
	- `<<<<<<<`
	- `=======`
	- `>>>>>>>`
4. Produire une version finale cohérente du planning
5. Valider la résolution :
	- `git add docs/planning-sprint.txt`
	- `git commit`

### Résultat attendu

- Le dépôt ne contient plus de conflit
- Le fichier `docs/planning-sprint.txt` ne contient plus de marqueurs Git
- L'historique contient un **commit de merge**

### Vérification

- `git status`
- `git log --graph --oneline --decorate -5`

### Annulation si besoin

- `git merge --abort`

---

## Exercice 2 — Résoudre un conflit avec `rebase`

### Objectif

Rejouer une branche de travail au-dessus d'une autre branche mise à jour et résoudre le conflit pendant le rebase.

### Fichier concerné

- `docs/notes-version.txt`

### Préparation

1. Se placer sur la branche de départ : `git checkout ex/rebase-feature`
2. Créer une branche locale de travail : `git checkout -b mon-rebase`

### Travail demandé

1. Lancer le rebase : `git rebase ex/rebase-base`
2. Ouvrir `docs/notes-version.txt`
3. Résoudre le conflit en gardant une version finale cohérente
4. Valider la résolution :
	- `git add docs/notes-version.txt`
	- `git rebase --continue`

### Résultat attendu

- Le dépôt ne contient plus de conflit
- Le fichier `docs/notes-version.txt` ne contient plus de marqueurs Git
- L'historique est **linéaire**
- Il n'y a **pas** de commit de merge pour cet exercice

### Vérification

- `git status`
- `git log --graph --oneline --decorate -5`

### Annulation si besoin

- `git rebase --abort`

---

## Conseils de résolution

- Lire les deux versions avant de supprimer les marqueurs
- Ne pas valider trop vite : vérifier le sens métier du texte final
- Utiliser `git diff` après résolution pour contrôler le résultat
- Pour chaque exercice, repartir d'une branche propre si nécessaire
