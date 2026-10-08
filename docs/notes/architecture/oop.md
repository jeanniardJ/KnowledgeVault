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

La programmation Orientée Objet (POO) se base sur quatres principes fondamentaux.

## Encapsulation

Consiste à regrouper dans une même entité (objet), les données et les traitements qui sont spécifiques :

* Attributs (propriétés) : données incluses dans l'objet
* Méthodes (fonctions ou procédure) : les traitements définis dans un objet.
  
### Exemple

Une classe Rectangle qui est un template abstrait de l'entité rectangle, qui comporte des attributs spécifiques à ces caractéristiques. Une méthode de type "procédure", dût à son "type" de retour "void" dans sa signature.

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

Tous les objets créés de la classe "Rectangle", ont tous les mêmes caractéristiques et comportement communs.

```csharp
public class Rectangle{

    //Caractéristique
    private int largeur;
    private int longueur;
    private string name;

    //Comportement
    public void Info(){
    }
}
```

## L'héritage

L'héritage permet à un objet d'obtenir d'un élément parent un ensemble de mécaniques et caractéristiques. 

## Exemple d'héritage

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

## Le polymorphisme

Le polymorphisme permet d'aller plus loin en manipulant un type enfant dans un type parent dont il est descendant.

### Exemple de polymorphisme

```csharp
public class Form{

}

public class Rectangle : Form {

}


Form rectangleA = new Rectangle();

```