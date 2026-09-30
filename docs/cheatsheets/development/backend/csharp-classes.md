# C# Classes

> Category: Development
> Scope: Objet-Oriented Programming
> Difficulty: Beginner to Intermediate

## Purpose

Référence rapise pour créer, structurer et utiliser des classes en C#.

## Define a class

Déclarer une classe avec le mot-clé `class` :

```csharp
public class User
{
}
```

Une classe peut contenir :

- des champs
- des propriétés
- des constructeurs
- des méthodes
- des événements
- des constantes
- des type imbriqués

## Create an object

Instancier une classe avec le mot-clé `new` :

```csharp
User user = new User();
```

Version implicite avec `var` :

```csharp
var user = new User();
```

## Fields

Un champ stocke une donnée directement dans la classe :

```csharp
public class User
{
    private string username;
    public int loginCount;
}
```

Il est recommandé de limiter l'accès direct aux champs et de privilégier les propriétés.

## Properties

### Auto-implemented property

Déclarer une propriété automatique :

```csharp
public class User
{
    public string Name {get; set;}
    public int Age {get; set;}
}
```

Utilisation :

```csharp
var user = new User
{ 
    Name = "Alice",
    Age = 30
}
```

### Read-only property

Déclarer une propriété accessible uniquement en lecture :

```csharp
public class User
{
    public string Name { get; }

    public User(string name)
    {
        Name = name;
    }
}
```

### Private setter

Autoriser la lecture publique, mais limiter la modification à la classe :

```csharp
public class BankAccount
{
    publi decimal Balance { get; private set;}

    public BankAccount(decimal initialBalance)
    {
        Balance = initialBalance;
    }

    public void Deposit(decimal amount){
        Balance += amount;
    }
}
```

### Property with validation

Ajouter une validation dans une propriété :

```csharp
public class Product
{
    private string name;

    public String Name
    {
        get => name;
        set{
            if(string.IsNullOrWhiteSpace(value)){
                throw new ArgumentException("Le nom est obligatoire");
            }

            name = value;
        }
    }
}
```

## Constructors

### Default constructor

Créer un constructeur sans paramètre :

```csharp
public class User
{
    public User()
    {

    }
}
```

Si aucun constructeur n'est déclaré, C# fournit automatiquement un constructeur public sans paramètre, selon le context de la classe.

### Parameterized constructor

Créer un constructeur avec des paramètres :

```csharp
public class User
{
    public string Name {get;}

    public User(string name){
        Name = name;
    }
}
```

Utilisation :

```csharp
var user = new User("Alise");
```

### Constructor overloading

Déclarer plusieurs constructeurs :

```csharp
public class Product
{
    public string Name { get; }
    public decimal Price { get; }

    public Product(){
        Name = "Unknown";
        Price = 0;
    }

    public Product(string name, decimal price){
        Name = name;
        Price = price;
    }
}
```

### Constructor chaining

Réutiliser un contructeur depuis un autre :

```csharp
public class User
{
    public string Name { get; }
    public bool IsActive { get; }

    public User(): this("Unknown", true){}

    public User(string name, bool isActive){
        Name = name;
        IsActive = isActive;
    }
}
```

## Methods

Déclarer une méthode dans une classe :

```csharp
public class Calcultor
{
    public int Add(int left, int right){
        return left + right;
    }
}
```

Utilisation :

```csharp
var calculator = new Calculator();
int result = calculator.Add(2, 3);
```

### Expression-bodied method

Écrire une courte méthode :

```csharp
public class Calcultator
{
    public int Add(int left, int right) => left + right;
}
```

### Static method

Déclarer une méthode qui ne dépend pas d'une instance :

```csharp
public class MathHelper
{
    public static int Square(int value) => value * value;
}
```

Utilisation :

```csharp
int result = MathHelper.Square(5);
```

## Access modifiers

| Modifier             | Description                                       |
| -------------------- | ------------------------------------------------- |
| `public`             | Accessible depuis n'importe quel code autorisé    |
| `private`            | Accessible uniquement dans la classe déclarante   |
| `protected`          | Accessible dans la classe et ses classes dérivées |
| `internal`           | Accessible dans le même assembly                  |
| `protected internal` | Accessible dans le même assembly ou par héritage  |
| `private protected`  | Accessible par héritage dans le même assembly     |

Exemple :

```csharp
public class Account
{
    private string password;
    protected decimal balance;
    internal string accountNumbeer;
    public string Owner { get; set; }
}
```

## Encapsulation

L'encapsulation consiste à protéger l'état interne d'un objet et à contrôler son accès par des méthodes ou des propriétés.

```csharp
public class BankAccount
{
    public decimal Balance { get; private set; }

    public void Deposit(decimal amount)
    {
        if(amount <= 0){
            throw new ArgumentException("Le montant doit être superieur à zéro");
        }

        Balance += amount;
    }
}
```

Le code extérieur peut consulter `Balance`, mais ne peut pas le modifier directement.

## Static classes

Une classe `static` ne peut pas être instanciée :

```csharp
public static class StringHelper
{
    public static bool IsEmpty(string value)
    {
        return string.IsNullOrWhiteSpace(value);
    }
}
```

Utilisation :

```csharp
bool result = StringHelp.IsEmpty("");
```

Une classe `sealed` ne peut pas être héritée :

```csharp
public sealed class SecurityToken
{
    public string Value { get; }

    public SecurityToken(string value){
        Value = value;
    }
}
```

## Abstract classes

Une classe `abstract` sert de base à d'autres classes et ne peut pas être instanciée directement :

```csharp
public abstract class Animal
{
    public string Name { get; }

    protected Animal(String name){
        Name = name;
    }

    public abstract void MakeSound();
}
```

Implémentation :

```csharp
public class Dog : Animal
{
    public Dog(string name) : base(name){}

    public override void MakeSound(){
        Console.WriteLine("Woof");
    }
}
```

## Inheritance

Hériter d'une classe avec le symbole `:` :

```csharp
public class Employee
{
    public string Name { get; set; }
}
```

```csharp
public class Developer : Employee
{
    public string MainLanguage { get; set; }
}
```

La classe `Developer` possède les membres accessibles de `Employee` et ses propres membres.

## Virtual and override

Autoriser la redéfinition d'une méthode :

```csharp
public class Animal
{
    public virtual void MakeSound(){
        Console.WriteLine("Unknow sound");
    }
}

public class Cat : Animal
{
    Public override void MarkeSound(){
        Console.WriteLine("Meow");
    }
}
```

Utilisation polymorphique :

```csharp
Animal animal = new cat();
animal.MakeSound(); // Meow
```

## Interfaces

Une classe peut implémenter une interface :

```csharp
publicc interface IRepository
{
    void Save();
}

public class UserRepository : IRepository
{
    public void Save(){
        Console.WriteLine("Utilisateur sauvegardé.");
    }
}
```

Une interface définit un contrat que la classe doit respecter.

## Records and classes

Une classe est généralement utilisée pour représenter un objet métier mutable ou possédant un cycle de vie.

```csharp
public class User
{
    public string Name { get; set; }
}
```

Un `record` est souvent adapté aux objets principalement définis par leurs valeurs :

```csharp
public record UserDto(string Name, string Email)
```

## Object initializer

Initialiser un objet après sa création :

```csharp
var user = new User
{
    name = "Alice",
    Age = 30
}
```

## Target-typed new

Éviter de répéter le type lorsqu'il est déjà connu :

```csharp
User user = new("Alice");
```

Cette syntaxe nécessite une version compatible de C#.

## Nullability

Déclarer une propriété qui peut contenir `null` :

```csharp
public class User
{
    public string? MiddleName { get; set; }
}
```

Déclarer une propriété obligatoire non nullable :

```csharp
public class User
{
    public required string Name { get; set; }
}
```

La disponibilité de `required` dépend de la version de C# utilisée.

## Equality

Par défaut, les classes comparent généralement les références :

```csharp
var first = new User("Alice");
var second = new User("Alice");

bool same = first == second;
```

Pour comparer les valeurs, il faut redéfinir `Equals` et `GetHashCode`, ou utiliser un `record` lorsque cela correspond au besoin.

## Complete exemple

```csharp
public class BankAccount
{
    public string Owner { get; }
    public decimal Balance { get; private set;}

    public BankAccount(string owner, decimal initialBalance)
    {
        if(string.IsNullOrWhiteSpace(owner)){
            throw new ArgumentException("Le propriétaire est obligatoire.");
        }

        if(initialBalance < 0){
            throw new ArgumentException("Le solde initial ne peut pas être négatif.");
        }

        Owner = owner;
        Balance = initialBalance;
    }

    public void Deposit(decimal amount){
        if(amount <= 0){
            throw new ArgumentException("Le montant doit être supérieur à zéro.").
        }

        Balance += amount;
    }

    public bool Withdraw(decimal amount){
        if(amount <= 0 || amount > Balance){
            return false;
        }

        Balance -= amount;
        return true;
    }
}
```

Utilisation :

```csharp
var account = new BankAccount("Alice", 100);

account.Deposit(50);
bool success = account.Withdraw(25);

Console.WriteLine(account.Balance); //125
```

## Best practices

- Respecter le principe de responsabilité unique.
- Préférer des propriétés contrôlées à des champs publics.
- Garder les champs privés.
- Valider les paramètres dans les constructeurs et les méthodes.
- Utiliser l'injection de dépendances pour les services externes.
- Éviter les classes statiques pour les composants nécessitant un état ou des dépendances remplaçables.
- Préférer la composition à l'héritage lorsque cela simplifie le modèle.
- Utiliser `sealed` lorsque l'héritage n'est pas prévu.
- Donner des noms explicites aux classes, propriétés et méthodes.
- Éviter les classes qui trop de responsabilités.

## Common mistakes

- Rendre tous les champs publics.
- Utiliser une classe statique pour stoker un état global.
- Ajouter une logique métier importante dans les propriétés.
- Créer une classe qui gère plusieurs responsabilités sans rapport.
- Utiliser l'héritage uniquement pour réutiliser quelques méthodes.
- Oublier de valider les arguments du constructeur.
- Comparer deux objets avec `==` en pensant comparer leurs valeurs.

## Related topics

- Object-Oriented Programming
- Encapsulation
- Inheritance
- Polymorphism
- Abstraction
- Interfaces
- Records
- Dependency Injection

## Sources

- [Microsoft Learn - Classes, structs, and records](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/types/classes)
- [Microsoft Learn - Object-oriented programming](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/tutorials/oop)
- [Microsoft Learn - Access modifiers](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)