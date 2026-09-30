# C# Classes
 
> Category: Software Design
> Topic: Object-Oriented Programming
> Difficulty: Beginner

## Definition

Une classe C# est modèle permettant de définir la structure et le comportement d'un objet.

Elle peut contenir des propriétés, des champs, des constructeurs, des méthodes et des événements.

## Question

Qu'est-ce qu'une classe en C# ?

## Answer

Une classe en C# est un type de référence qui regroupe des données et des comportements au sein d'une même structure.

## Key points

- Une classe se déclare avec le mot-clé `class`.
- Un objet est une instance d'une classe.
- Les propriétés représentent généralement les données de l'objet.
- Les méthodes représentent les actions possibles de l'objet.
- Le constructeur initialise l'objet lors de sa création.
- L'encapsulation permet de protéger l'état interne de l'objet.
- Une classe peut hériter d'une autre classe.
- Une classe peut implémenter une ou plusieurs interfaces.
  
## Example

```csharp
public class User
{
    public string Name { get; private set; }

    public User(string name){
        Name = name;
    }

    public void Intraduce(){
        Console.WriteLine($"Bonjour, je suis {Name}.")
    }
}
```

Création et utilisation d'un objet :

```csharp
var user = new User("Alice");
user.Introduce();
```

Résultat :

```text
Bonjour, je suis Alice.
```

## Object structure

Une classe peut être représentée ainsi :

```text
Class
├── Properties
├── Fields
├── Constructor
├── Methods
└── Events
```

## Common mistakes

## Common mistakes

- Confondre une classe avec un objet.
- Rendre tous les champs publics.
- Ajouter plusieurs responsabilités sans rapport dans la même classe.
- Oublier de valider les paramètres du constructeur.
- Utiliser l’héritage uniquement pour réutiliser quelques méthodes.
- Modifier directement l’état interne depuis l’extérieur.

## Related concepts

- [Object-Oriented Programming](poo.md)
- [Encapsulation](encapsulation.md)
- [Inheritance](inheritance.md)
- [Polymorphism](polymorphism.md)
- [Interfaces](interfaces.md)
- [C# Classes Cheatsheet](../../cheatsheets/development/backend/csharp-classes.md)

## Sources

- [Microsoft Learn - Classes, structs, and records](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/types/classes)
- [Microsoft Learn - Object-oriented programming](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/tutorials/oop)