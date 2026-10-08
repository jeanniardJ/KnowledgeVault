# OOP

> Category: Architecture

## Overview

Programmation Orienter Object

## Key concepts

* Encapsulation
* Abstraction
* Héritage
* Polymorphisme

### Detailed explanation

La programmation Orientée Objet (POO) se base sur 4 principes fondamentaux.

## Encapsulation

* Les caractéristiques communes
* Les comportements communs à tous les éléments.
  
### Exemple

```csharp
public class Rectangle{
    private int largeur;
    private int longueur;
    private string name;

    public void Info(){
        Console.WriteLine($"Information sur le rectangle largeur : {largeur}, longueur : {longueur} et son nom {name}");
    }
}
```

## Abstraction

* Les caractéristiques communes
* Les comportements communs à tous les éléments.

### Exemple d'abstraction

```csharp
class public Form{
    private string name;

    public void Info(){

    }
}

class public Rectangle : form {
    private int longueur;
    private int largeur;

    public void Info(){
        Console.WriteLin($"Nom du rectangle {name}, longueur : {longeur}, largeur {largeur}");
    }
}
```

## L'héritage

## Le polymorphisme