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

### Use Like

Rechercher un motif textuel :

```sql
SELECT * FROM users WHERE username LIKE 'alex%'
```

Motifs courants :

| Pattern    | Description                    |
| ---------- | ------------------------------ |
| `'alex%'`  | Commence par `alex`            |
| `'%alex'`  | Se termine par `alex`          |
| `'%alex%'` | Contient `alex`                |
| `'a_ex'`   | Un caractère entre `a` et `ex` |

### Check NULL values

Tester une valeur `NULL` :

```sql
SELECT * FROM users WHERE deleted_at IS NULL;
```

Tester les valeurs non nulles :

```sql
SELECT * FROM users WHERE deleted_at IS NOT NULL
```

> Attention : utiliser `= NULL` ou `<> NULL` ne fonctionne pas comme un test classique. Utilise `IS NULL` ou `IS NOT NULL`.

## Sort data

### Sort ascending

Trier par ordre croissant :

```sql
SELECT * FROM products ORDER BY price ASC;
```

### Sort descending

Trier par ordre décroissant

```sql
SELECT * FROM products ORDER BY price DESC;
```

### Sort by multiple columns

Trier selon plusieurs colonnes :

```sql
SELECT * FROM users ORDER BY last_name ASC, first_name ASC;
```

## Limit results

Limiter le nombre de résultats :

```sql
SELECT * FROM users LIMIT 10;
```

Avec un décalage :

```sql
SELECT * FROM users LIMIT 10 OFFSET 20;
```

> La syntaxe peut varier selon le sytème de gestion de base de données. 
> Par exemple, SQL Server utilise souvent `TOP` ou `OFFSET ... FETCH`.

## Insert data

### Insert one row

Insérer une ligne :

```sql
INSERT INTO users (username, email, is_active) VALEUS ('alice', 'alice@example.com', TRUE);
```

### Insert multiple rows

Insérer plusieurs lignes :

```sql
INSERT INTO users (username, email, is_active) VALUES   
    ('alice', 'alice@example.com', TRUE),
    ('bob', 'bob@example.com', TRUE),
    ('charlie', 'charlieàexample.com', TRUE);
```

Toujours indiquer explicitement les colonnes ciblées afin d'éviter les erreurs liées à l'ordre ou à l'évolution de la structure de la table.

## Update data

### Update rows

Modifier des lignes :

```sql
UPDATE users SET is_active = FALSE WHERE id = 10;
```

### Update multiple columns

Modifier plusieurs colonnes :

```sql
UPDATE users SET email = 'new-email@example.com', is_active = TRUE WHERE id = 10;
```

> Toujours vérifier la clause `WHERE` avant d'exécuter une requête `UPDATE`.
> Sans `WHERE`, toutes les lignes peuvent être modifiées.

## Delete data

### Delete selected rows

Supprimer des lignes correspondant à une condition :

```sql
DELETE FROM users WHERE id = 10;
```

### Delete all rows

Supprimer toutes les lignes d'une table :

```sql
DELETE FROM users;
```

> Attention : une requête `DELETE` sans `WHERE` supprime toutes les lignes.
> Vérifier la requête avec un `SELECT` avec de l'exécuter.

## Aggregate functions

Fonctions d'agrégation courantes :

| Function  | Description                 |
| --------- | --------------------------- |
| `COUNT()` | Compte les lignes           |
| `SUM()`   | Calcule une somme           |
| `AVG()`   | Calcule une moyenne         |
| `MIN()`   | Retourne la valeur minimale |
| `MAX()`   | Retourne la valeur maximale |

Exemples :

```sql
SELECT COUNT(*) AS user_count FROM users;
```

```sql
SELECT MIN(price) AS minimum_price,
    MAX(price) AS maximum_price,
    AVG(price) AS average_price
FROM products;
```

## Group data

### Use GROUP BY

Regrouper les résultats :

```sql
SELECT role, COUNT(*) AS user_count 
FROM users 
GROUP BY role;
```

`GROUP BY` divise e résultat en groupes, généralement utilisés avec une fonction d'agrégation.

### Use HAVING

Filtrer les groupes après agrégation :

```sql
SELECT role, COUNT(*) AS user_count 
FROM users
GROUP BY role
HAVING COUNT(*) > 5;
```

Différence :

- `WHERE` filtre les lignes avant le regroupement.
- `HAVING` filtre les groupes après le regroupement.

## Joins

Une jointure permet de combiner les données de plusieurs tables à partir d'une relation commune.

### INNER JOIN

Retourner uniquement les lignes possédant une correspondance dans les deux tables :

```sql
SELECT
    users.username,
    orders.total_amount
FROM users
INNER JOIN orders
    ON orders.user_id = users.id;
```

### LEFT JOIN

Retourner toutes les lignes de la table de gauche,
même sans correspondance dans la table de droite :

```sql
SELECT users.username,
    orders.total_amount
FROM users
LEFT JOIN orders
    ON orders.user_id = users.id
```

### RIGHT JOIN

Retourner toutes les lignes de la table de droite :

```sql
SELECT
    users.username,
    orders.total_amount
FROM users
RIGHT JOIN orders
    ON orders.user_id = users.id
```

### FULL OUTER JOIN

Retourner toutes les lignes des deux tables, qu'elles aient ou non une correspondance :

```sql
SELECT
    users.username,
    orders.total_amount
FROM users
FULL OUTER JOIN orders
    ON orders.user_id = users.id
```

> La disponibilité de `FULL OUTER JOIN` dépend du système de gestion de base de données utilisé.

### CROSS JOIN

Créer le produit cartésien des deux tables :

```sql
SELECT
    colors.name,
    sizes.name
FROM colors
CROSS JOIN sizes;
```

Cette opération peut produire un grand nombre de lignes.

### Self join

Joindre une table avec elle-même :

```sql
SELECT
    employee.name AS employee_name,
    manager.name AS manager_name
FROM employees AS manager
    ON employee.manager_id = manager.id;
```

## Subqueries

### Use a subquery with IN

Utiliser une sous-requête :

```sql
SELECT * FROM users WHERE id IN (
    SELECT user_id
    FROM orders
    WHERE total_amount > 100
);
```

### Use EXISTS

Vérifier l'existence d'un résultat associé :

```sql
SELECT * FROM users AS u WHERE EXISTS (
    SELECT 1
    FROM orders AS o
    WHERE o.user_id = u.id
);
```

## Common table expressions

Utiliser une CTE avec `WITH` :

```sql
WITH active_users AS (
    SELECT *
    FROM users
    WHERE is_active = TRUE
)
SELECT * FROM active_users;
```

Une CTE permet de donner un nom temporaire à une sous-requête et de la réutiliser dans la requête principale.

## Create a table

Créer une table :

```sql
CREATE TABLE user (
    id INTEGER PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## Alter a table

### Add a column

Ajouter une colonne :

```sql
ALTER TABLE users ADD COLUMN last_login TIMESTAMP;
```

### Rename a column

Renommer une colonne :

```sql
ALTER TABLE users RENAME COLUMN username TO login;
```

### Drop a column

Supprimer une colonne :

```sql
ALTER TABLE users DROP COLUMN last_login;
```

> Vérifier les dépendances avant de supprimer une colonne.

## Constraints

### Primary key

Définir une clé primaire :

```sql
CREATE TABLE users (
    id INTEGER PRIMARY KEY,
    username VARCHAR(50) NOT NULL
);
```

### Foreign key

Définir une clé étrangère :

```sql
CREATE TABLE orders (
    id INTEGER PRIMARY KEY,
    user_id INTEGER NOT NULL,
    CONSTRAINT fk_orders_user
        FOREIGN KEY (user_id)
        REFERENCES users(id)
);
```

### Unique contraint

Garantir l'unicité d'une valeur :

```sql
CREATE TABLE users (
    id INTEGER PRIMARY KEY,
    email VARCHAR(255) UNIQUE
);
```

### Check constraint

Applique une condition :

```sql
CREATE TABLE products (
    id INTEGER PRIMARY KEY,
    price DECIMAL(10, 2),
    CONTRAINT positive_price
        CHECK (price >= 0)
);
```

## Transactions

### Start a transaction

Démarrer une transaction :

```sql
BEGIN;
```

Selon le système de gestion utilisé, on peut aussi rencontrer :

```sql
START TRANSACTION;
```

### Commit a transaction

Valider les modifications :

```sql
COMMIT;
```

### Roll back a transaction

Annuler les modifications :

```sql
ROLLBACK;
```

Exemple :

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 100
WHERE id = 1;

UPDATE accounts
SET balance = balance + 100
WHERE id = 2;

COMMIT;
```

Si une erreur survient :

```sql
ROLLBACK;
```

## Indexes

### Create an index

Créer un index :

```sql
CREATE INDEX idx_users_email
ON users(email);
```

### Create a unique index

Créer un index unique :

```sql
CREATE UNIQUE INDEX idx_users_username
ON users(username);
```

### Remove an index

Supprimer un index :

```sql
DROP INDEX idx_users_email;
```

Les index peuvent accélérer les recherches, mais ils augmentent
l’espace utilisé et peuvent ralentir certaines opérations d’écriture.

## Query analysis

### Explain a query

Analyser le plan d’exécution :

```sql
EXPLAIN
SELECT *
FROM users
WHERE email = 'alice@example.com';
```

Selon le système de gestion :

```sql
EXPLAIN ANALYZE
SELECT *
FROM users
WHERE email = 'alice@example.com';
```

> `EXPLAIN ANALYZE` peut réellement exécuter la requête.
> L’utiliser avec prudence pour les requêtes qui modifient les données.

## NULL handling

### Replace NULL values

Remplacer une valeur `NULL` :

```sql
SELECT
    username,
    COALESCE(display_name, username) AS visible_name
FROM users;
```

### Conditional values

Utiliser une expression conditionnelle :

```sql
SELECT
    username,
    CASE
        WHEN is_active = TRUE THEN 'Active'
        ELSE 'Inactive'
    END AS account_status
FROM users;
```

## Date and time

### Current date and time

Obtenir la date et l’heure actuelles :

```sql
SELECT CURRENT_TIMESTAMP;
```

### Filter by date

Filtrer les données à partir d’une date :

```sql
SELECT *
FROM orders
WHERE created_at >= '2026-01-01';
```

Pour les requêtes dépendantes du fuseau horaire,
vérifier la syntaxe propre au SGBD utilisé.

## Safe update workflow

Avant un `UPDATE` ou un `DELETE` :

```sql
SELECT *
FROM users
WHERE id = 10;
```

Puis exécuter l’opération :

```sql
UPDATE users
SET is_active = FALSE
WHERE id = 10;
```

Pour plusieurs modifications :

```sql
BEGIN;

UPDATE users
SET is_active = FALSE
WHERE last_login < '2025-01-01';

-- Vérifier le résultat avant validation
SELECT *
FROM users
WHERE is_active = FALSE;

COMMIT;
```

En cas de problème :

```sql
ROLLBACK;
```

## Common mistakes

- Oublier la clause `WHERE` dans une requête `UPDATE`.
- Oublier la clause `WHERE` dans une requête `DELETE`.
- Utiliser `= NULL` au lieu de `IS NULL`.
- Créer un `JOIN` sans condition correcte.
- Utiliser `SELECT *` dans du code applicatif sans nécessité.
- Ajouter trop d’index sur une table fortement modifiée.
- Confondre `WHERE` et `HAVING`.
- Utiliser une transaction sans prévoir de `COMMIT` ou de `ROLLBACK`.
- Construire une requête avec des chaînes concaténées non sécurisées.

## Security notes

- Utiliser des requêtes préparées ou des paramètres liés.
- Ne jamais concaténer directement des entrées utilisateur dans une requête.
- Limiter les droits du compte utilisé par l’application.
- Éviter de stocker les mots de passe en clair.
- Ne pas afficher les erreurs SQL détaillées aux utilisateurs.
- Vérifier les données avant les opérations de modification.
- Utiliser des transactions pour les opérations qui doivent être atomiques.

Exemple avec une requête paramétrée en C# :

```csharp
using var command = new SqlCommand(
    "SELECT * FROM users WHERE email = @email",
    connection
);

command.Parameters.AddWithValue("@email", email);
```

## Related topics

- [Database Administration](../../flashcards/databases/dba.md)
- [SQL Flashcard](../../flashcards/databases/sql.md)
- [NoSQL](../../flashcards/databases/nosql.md)
- [SGBDR](../../flashcards/databases/sgbdr.md)
- [ORM](../../flashcards/architecture/orm.md)

## Sources

- [PostgreSQL SELECT documentation](https://www.postgresql.org/docs/current/sql-select.html)
- [PostgreSQL UPDATE documentation](https://www.postgresql.org/docs/current/sql-update.html)
- [Microsoft Learn - SQL Server joins](https://learn.microsoft.com/en-us/sql/relational-databases/performance/joins)
- [Microsoft Learn - GROUP BY](https://learn.microsoft.com/en-us/sql/t-sql/queries/select-group-by-transact-sql)
- [Microsoft Learn - Aggregate functions](https://learn.microsoft.com/en-us/sql/t-sql/functions/aggregate-functions-transact-sql)