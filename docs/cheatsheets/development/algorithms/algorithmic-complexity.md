# Algorithmic Complexity Cheatsheet

> Category: Development
> Scope: Algorithms
> Difficulty: Beginner to Intermediate
> Last updated: 2026-10-01

## Purpose

Référence rapide des principales complexités temporelles et spatiales utilisées pour analyser les algorithmes.

## Big O notation

La notation Big O décrit la manière dont le temps d'exécution ou la mémoire utilisée évolue selon la taille des données d'entrée.

La taille des données est généralement représentée par `n`.

## Common complexities

| Complexity | Name | Example |
|---|---|---|
| `O(1)` | Constant | Accès à un élément par son index |
| `O(log n)` | Logarithmic | Recherche dichotomique |
| `O(n)` | Linear | Parcours d'un tableau |
| `O(n log n)` | Linearithmic | Tri fusion |
| `O(n²)` | Quadratic | Deux boucles imbriquées |
| `O(2ⁿ)` | Exponential | Recherche exhaustive |
| `O(n!)` | Factorial | Génération de permutations |

## Time complexity

Mesure le nombre d'opérations effectuées par l'algorithme.

```csharp
for (int i = 0; i < numbers.Length; i++)
{
    Console.WriteLine(numbers[i]);
}
```

Complexité :

```text
O(n)
```

## Space complexity

Mesure la mémoire supplémentaire utilisée par l'algorithme.

```csharp
int[] copy = new int[numbers.Length];
```

Complexité spatiale :

```text
O(n)
```

## Simplification rules

Les constantes et les termes secondaires sont ignorés :

```text
O(5n) = O(n)
O(n² + n) = O(n²)
O(100) = O(1)
```

## Complexity ranking

De la plus efficace à la plus coûteuse :

```text
O(1)
O(log n)
O(n)
O(n log n)
O(n²)
O(2ⁿ)
O(n!)
```

## Common mistakes

- Confondre le temps réel d'exécution avec la complexité.
- Oublier de prendre en compte la mémoire utilisée.
- Confondre deux boucles successives avec deux boucles imbriquées.
- Conserver les constantes dans le résultat final.
- Utiliser un algorithme en `O(n²)` sur un grand volume de données sans vérifier ses performances.

## Related topics

- [Dichotomy](dichotomy.md)
- Binary Search
- Sorting Algorithms
- Data Structures
- Recursion
- Performance

## Sources

- [Microsoft Developer Blog - Big O notation](https://devblogs.microsoft.com/oldnewthing/20090612-00/?p=17913)
- [Big-O Cheat Sheet](https://www.bigocheatsheet.com/)
