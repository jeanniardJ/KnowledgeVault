# SQL

> Category: Databases
> Scope: Queries, data manipulation and database operations
> Difficulty: Beginner to Intermediate

## Purpose

Référence rapide des principales commandes SQL utilisées pour consulter, ajouter, modifier et supprimer des données dans une base de données relationnelle.

## Database terminology

| English term | Traduction française   | Description                                    |
| ------------ | ---------------------- | ---------------------------------------------- |
| Database     | Base de données        | Ensemble organisé de données                   |
| Table        | Table                  | Structure contenant des lignes et des colonnes |
| Row          | Ligne / enregistrement | Élément stocké dans une table                  |
| Column       | Colonne                | Propriété d’une table                          |
| Primary key  | Clé primaire           | Identifie chaque ligne de manière unique       |
| Foreign key  | Clé étrangère          | Référence une autre table                      |
| Query        | Requête                | Instruction envoyée à la base de données       |
| Constraint   | Contrainte             | Règle appliquée aux données                    |

## Query structure

Structure générale d'une requête de lecture :

```sql
SELECT column1, column2 FROM table_name WHERE condition ORDER BY column1 LIMIT 10;
```

L'ordre logique habituel des clauses est :

```text
SELECT
FROM
JOIN
WHERE
GROUP BY
HAVING
ORDER BY
LIMIT
```

## Select data

### Select all columns

Sélectionner toutes les colonnes :

```sql
SELECT * FROM users;
```

### Select specific columns

Sélectionner certainers colonnes :

```sql
SELECT id, username, email FROM users;
```

### Use aliases

Utiliser un alias pour une colonne :

```sql
SELECT username AS user_name, email AS user_email FROM users;
```

utiliser un alias pour une table :

```sql
SELECT u.username FROM users AS u;
```

### Remove duplicate values

Supprimer les doublons dans le résultat :

```sql
SELECT DISTINCT country FROM users;
```

## Filter data

### Use WHERE

Filtrer les résultats :

```sql
SELECT * FROM users WHERE is_active = TRUE;
```

### Compare values

Utiliser des opérateurs de comparaison :

```sql
SELECT * FROM products WHERE price > 100 ;
```

Opérateurs courants :

| Operator | Description         |
| -------- | ------------------- |
| `=`      | Égal à              |
| `<>`     | Différent de        |
| `>`      | Supérieur à         |
| `<`      | Inférieur à         |
| `>=`     | Supérieur ou égal à |
| `<=`     | Inférieur ou égal à |

### Combine conditions

Combiner plusieurs conditions :

```sql
SELECT * FROM prodcuts WHERE price >= 50 AND stock > 0;
```

Utiliser `OR` :

```sql
SELECT * FROM users WHERE role = 'admin' OR role = 'moderateur';
```

Inverser une condition avec `NOT` :

```sql
SELECT * FROM users WHERE NOT is_active;
```

### Use IN

Tester plusieurs valeurs :

```SQL
SELECT * FROM users WHERE role IN ('admin', 'moderator');
```

### Use BETWEEN

Rechercher une valeur dans un intervalle :

```sql
SELECT * FROM products WHERE price BETWEEN 10 AND 50;
```