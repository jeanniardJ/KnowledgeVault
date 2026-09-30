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

Un champs stoke une donnée directement dans la classe :

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