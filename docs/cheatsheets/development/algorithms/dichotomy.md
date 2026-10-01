# Dichotomy Cheatsheet

> Category: Development
> Scope: Algorithms
> Difficulty: Beginner to Intermediate
> Last updated: 2026-10-01

## Purpose

Référence rapide de la recherche dichotomique, de son fonctionnement et de son implémentation.

## Definition

La recherche dichotomique recherche une valeur dans un tableau trié en divisant l'espace de recherche par deux à chaque étape.

## Requirements

- Le tableau doit être trié.
- Les éléments doivent être comparables.
- L'accès à l'élément central doit être efficace.

## Algorithm

```text
low = 0
high = length(array) - 1

while low <= high:
    middle = (low + high) / 2

    if array[middle] == target:
        return middle

    if array[middle] < target:
        low = middle + 1
    else:
        high = middle - 1

return -1
```

## C# implementation

```csharp
public static int BinarySearch(int[] numbers, int target)
{
    int low = 0;
    int high = numbers.Length - 1;

    while (low <= high)
    {
        int middle = low + (high - low) / 2;

        if (numbers[middle] == target)
        {
            return middle;
        }

        if (numbers[middle] < target)
        {
            low = middle + 1;
        }
        else
        {
            high = middle - 1;
        }
    }

    return -1;
}
```

## Example

Tableau :

```text
[3][8][12][17][21][29][35]
```

Recherche de `29` :

```text
1. Comparer avec 17.
2. Rechercher dans la moitié droite.
3. Comparer avec 29.
4. Retourner l'index trouvé.
```

## Complexity

| Case         | Time       | Space  |
| ------------ | ---------- | ------ |
| Best case    | `O(1)`     | `O(1)` |
| Average case | `O(log n)` | `O(1)` |
| Worst case   | `O(log n)` | `O(1)` |

L'implémentation itérative utilise une mémoire auxiliaire constante. Une version récursive peut utiliser une mémoire supplémentaire liée à la profondeur des appels.

## Dichotomic search versus linear search

| Algorithm     | Requirement              | Time complexity |
| ------------- | ------------------------ | --------------- |
| Linear search | Tableau trié ou non trié | `O(n)`          |
| Binary search | Tableau trié             | `O(log n)`      |

## Common mistakes

- Rechercher dans un tableau non trié.
- Oublier de modifier `low` ou `high`.
- Créer une boucle infinie.
- Confondre l'index central avec la valeur centrale.
- Ne pas gérer la valeur absente du tableau.
- Utiliser une condition incorrecte pour réduire l'intervalle.

## Related topics

- [Algorithmic Complexity](algorithmic-complexity.md)
- Binary Search
- Divide and Conquer
- Sorting Algorithms
- Arrays

## Sources

- [Microsoft Learn - Array.BinarySearch](https://learn.microsoft.com/en-us/dotnet/api/system.array.binarysearch)
- [CS50 - The Binary Search Algorithm](https://cs50.harvard.edu/ap/2020/assets/pdfs/binary_search.pdf)
