# Dichotomy

> Category: Development  
> Topic: Algorithms  
> Difficulty: Beginner  
> Last updated: 2026-10-01

## Definition

La dichotomie consiste à diviser un problème ou un ensemble
de données en deux parties.

## Question

Qu'est-ce que la recherche dichotomique ?

## Answer

La recherche dichotomique recherche une valeur dans un tableau trié
en divisant l'espace de recherche par deux à chaque étape.

## Key points

- Le tableau doit être trié.
- La moitié inutile est éliminée après chaque comparaison.
- Sa complexité temporelle est `O(log n)`.
- Elle est généralement plus efficace qu'une recherche linéaire
  sur un grand tableau trié.

## Example

Pour rechercher `29` dans :

```text
[3][8][12][17][21][29][35]
```

On compare d'abord `29` à `17`, puis on conserve uniquement
la moitié droite du tableau.