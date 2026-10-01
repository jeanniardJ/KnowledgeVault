# backtracking

> Categoty: Delevopment
> Topic: Algorithms
> Difficulty: Intermediate

## Definition

Le backtracking est une technique algorithmique qui construit une solution progressivement et revient en arrière lorsqu'une possibilité ne peut mener à une solution valide.

## Question

Qu'est-ce que le backtracking ?

## Answer

Le backtracking explore différentes possibilités de manière récursive.

Lorsque'une possibilité viole une contrainte ou mène à une impasse, l'algorithme annule le dernier choix et essaie une autre possibilité.

## Key points

- La solution est contruite étape par étape.
- Chaque choix est vérifié avant de poursuivre.
- Une branche invalide est abandonnée rapidement.
- L'algorithme revient au choix précédent.
- Il est adapté aux problèmes de contraintes et de combinaisons.

## Example

Dans le problème des huit reines :

```text
1. Placer une reine.
2. Vérifier si sa position est valide.
3. Passer à la ligne suivant.
4. Revenir en arrière si aucune position ne convient pas.
```

## Common uses

- Sudoku
- Labyrinthes.
- Problème des N-Queens.
- Génération de combinaisons.
- Génération de permutations.
- Recherche de chemins.

## Complexity

La complexité dépend du nombre de choix possibles.

Dans le pire cas, elle est souvent exponentielle :

```text
O(b^d)
```

où :

- `b` représente le nombre de choix possibles.
- `d` représente la profondeur de recherche.

La mémoire utilisée par la récursion est généralement liée à la profondeur de l'arbre de recherche.

## Related topics

- [Algorithmic Complexity](algorithmic-complexity.md)
- [Dichotomy](dichotomy.md)
- Recursion
- Depth-First Search
- Divide and Conquer
- Constraint Satisfaction