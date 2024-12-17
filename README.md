**Cours complet sur la programmation orientée objet (POO) en Python**

---

### 1. Introduction à la Programmation Orientée Objet (POO)

La programmation orientée objet (POO) est un paradigme de programmation qui repose sur le concept d'"objets". Ces objets encapsulent des données (sous forme d'attributs) et des comportements (sous forme de méthodes). La POO facilite la modélisation du monde réel et permet de réutiliser et de maintenir plus facilement le code.

**Concepts clés de la POO :**

1. **Classe** : Modèle ou plan de construction des objets.
2. **Objet** : Instance concrète d'une classe.
3. **Attribut** : Propriété ou donnée d'un objet.
4. **Méthode** : Fonction définie au sein d'une classe.
5. **Encapsulation** : Restriction de l'accès à certaines parties d'un objet.
6. **Héritage** : Capacité d'une classe à hériter les propriétés et méthodes d'une autre classe.
7. **Polymorphisme** : Capacité à redéfinir les méthodes dans des classes dérivées.
8. **Abstraction** : Représentation des aspects essentiels sans entrer dans les détails.

---

### 2. Création d'une Classe et d'Objets en Python

**Exemple simple d'une classe et d'un objet :**

```python
class Personne:
    def __init__(self, nom, age):
        self.nom = nom
        self.age = age

    def se_presenter(self):
        print(f"Bonjour, je m'appelle {self.nom} et j'ai {self.age} ans.")

# Création d'objets
personne1 = Personne("Alice", 25)
personne1.se_presenter()
```

**Détails :**

- Le constructeur `__init__` initialise les attributs.
- Les méthodes sont des fonctions propres à la classe.

---

### 3. Encapsulation

L'encapsulation consiste à cacher les détails internes d'une classe pour protéger ses données. En Python, cela se fait à l'aide d'attributs **privés** (prefixés par `_` ou `__`).

**Exemple :**

```python
class CompteBancaire:
    def __init__(self, titulaire, solde):
        self.titulaire = titulaire
        self.__solde = solde  # Attribut privé

    def afficher_solde(self):
        print(f"Solde : {self.__solde} €")

    def deposer(self, montant):
        self.__solde += montant

    def retirer(self, montant):
        if montant > self.__solde:
            print("Fonds insuffisants !")
        else:
            self.__solde -= montant

# Exemple
compte = CompteBancaire("Jean", 1000)
compte.deposer(500)
compte.afficher_solde()
compte.retirer(2000)  # Fonds insuffisants !
```

---

### 4. Héritage

L'héritage permet à une classe dérivée d'hériter des propriétés et méthodes d'une classe parente.

**Exemple :**

```python
class Animal:
    def __init__(self, nom):
        self.nom = nom

    def parler(self):
        pass  # Méthode abstraite

class Chien(Animal):
    def parler(self):
        print("Wouf Wouf !")

class Chat(Animal):
    def parler(self):
        print("Miaou !")

# Exemple d'utilisation
chien = Chien("Rex")
chat = Chat("Mimi")
chien.parler()  # Wouf Wouf !
chat.parler()   # Miaou !
```

---

### 5. Polymorphisme

Le polymorphisme permet d'utiliser une méthode de la même manière, quelle que soit la classe de l'objet.

**Exemple :**

```python
def faire_parler(animal):
    animal.parler()

faire_parler(chien)  # Wouf Wouf !
faire_parler(chat)   # Miaou !
```

---

### 6. Classes Abstraites

En Python, une classe abstraite est une classe qui ne peut pas être instanciée directement. Elle sert de modèle pour d'autres classes.

**Exemple avec ****`abc`**** (Abstract Base Class) :**

```python
from abc import ABC, abstractmethod

class Vehicule(ABC):
    @abstractmethod
    def demarrer(self):
        pass

class Voiture(Vehicule):
    def demarrer(self):
        print("La voiture démarre.")

# Exemple
voiture = Voiture()
voiture.demarrer()
```

---

### 7. Gestion des Exceptions dans les Classes

Les classes peuvent inclure des mécanismes pour gérer les erreurs.

**Exemple :**

```python
class Diviseur:
    def __init__(self, numerateur, denominateur):
        self.numerateur = numerateur
        self.denominateur = denominateur

    def diviser(self):
        try:
            return self.numerateur / self.denominateur
        except ZeroDivisionError:
            print("Erreur : Division par zéro !")

# Exemple
operation = Diviseur(10, 0)
operation.diviser()  # Erreur : Division par zéro !
```

---

### 8. Exemple Complet : Gestion d'une Bibliothèque

Voici un exemple plus avancé combinant tous les concepts :

```python
class Livre:
    def __init__(self, titre, auteur):
        self.titre = titre
        self.auteur = auteur

class Bibliotheque:
    def __init__(self):
        self.livres = []

    def ajouter_livre(self, livre):
        self.livres.append(livre)

    def afficher_livres(self):
        if not self.livres:
            print("La bibliothèque est vide.")
        else:
            for livre in self.livres:
                print(f"Titre : {livre.titre}, Auteur : {livre.auteur}")

# Exemple d'utilisation
bibliotheque = Bibliotheque()
livre1 = Livre("1984", "George Orwell")
livre2 = Livre("Le Petit Prince", "Antoine de Saint-Exupéry")

bibliotheque.ajouter_livre(livre1)
bibliotheque.ajouter_livre(livre2)
bibliotheque.afficher_livres()
```

---

### 9. Avantages de la POO

1. **Réutilisation du code** : Héritage et polymorphisme.
2. **Lisibilité** : Le code est organisé en classes et objets.
3. **Maintenance facilitée** : Modifications localisées.
4. **Modélisation du monde réel** : Les objets représentent des entités concrètes.

---

### 10. Conclusion

La POO est un paradigme puissant qui simplifie le développement logiciel. Avec Python, les concepts de base et avancés sont facilement implémentables, ce qui en fait un excellent langage pour apprendre et appliquer la POO.




**Cours complet sur les types de variables en programmation**

---

### 1. Introduction aux types de variables

En programmation, une **variable** est un espace mémoire dans lequel on stocke des données. Les **types de variables** déterminent la nature des données qu’elles peuvent contenir et les opérations qui peuvent être effectuées sur elles.

---

### 2. Catégories principales des types de variables

Les types de variables peuvent être classés en différentes catégories :

1. **Types primitifs**
2. **Types composés**
3. **Types abstraits**
4. **Types spéciaux**

Nous allons explorer chaque catégorie avec des exemples.

---

### 3. Les types primitifs

Ce sont les types les plus simples et fondamentaux. Ils incluent :

#### a) **Nombres entiers (int)**
Représentent des valeurs entiers (positifs ou négatifs).

Exemple en Python :
```python
x = 42  # Variable de type entier
```

#### b) **Nombres réels (float)**
Représentent des nombres à virgule flottante (décimaux).

Exemple :
```python
pi = 3.14159  # Variable de type float
```

#### c) **Booléens (bool)**
Représentent des valeurs logiques : `True` ou `False`.

Exemple :
```python
est_vrai = True  # Variable booléenne
```

#### d) **Caractères et Chaîne de caractères (str)**
Représentent du texte.

Exemple :
```python
nom = "Alice"  # Variable de type string
```

---

### 4. Les types composés

Ces types regroupent plusieurs valeurs en une seule unité.

#### a) **Listes (list)**
Les listes sont des collections ordonnées et modifiables.

**Créer une liste :**
```python
fruits = ["pomme", "banane", "cerise"]
```

**Ajouter un élément :**
```python
fruits.append("orange")
```

**Modifier un élément :**
```python
fruits[0] = "fraise"
```

**Supprimer un élément :**
```python
fruits.remove("banane")
```

**Parcourir une liste :**
```python
for fruit in fruits:
    print(fruit)
```

**Exemple avancé :**
```python
# Filtrer les fruits qui commencent par 'p'
p_fruits = [fruit for fruit in fruits if fruit.startswith('p')]
print(p_fruits)
```

#### b) **Tuples (tuple)**
Les tuples sont des collections ordonnées mais immuables.

Exemple :
```python
coordonnees = (10, 20)
```

#### c) **Ensembles (set)**
Les ensembles sont des collections non ordonnées et uniques.

Exemple :
```python
nombres_uniques = {1, 2, 3, 4}
```

#### d) **Dictionnaires (dict)**
Les dictionnaires stockent des paires clés-valeurs.

**Créer un dictionnaire :**
```python
etudiant = {"nom": "Alice", "age": 21}
```

**Ajouter une clé-valeur :**
```python
etudiant["classe"] = "Terminale"
```

**Modifier une valeur :**
```python
etudiant["age"] = 22
```

**Supprimer une clé :**
```python
del etudiant["classe"]
```

**Parcourir un dictionnaire :**
```python
for cle, valeur in etudiant.items():
    print(f"{cle}: {valeur}")
```

---

### 5. Les types abstraits

Ces types sont utilisés pour modéliser des entités plus complexes.

#### a) **Classes et Objets**
Les classes permettent de définir des types personnalisés. Les objets sont des instances de ces classes.

Exemple :
```python
class Personne:
    def __init__(self, nom, age):
        self.nom = nom
        self.age = age

personne1 = Personne("Alice", 25)  # Création d'un objet
```

#### b) **Structures**
Dans certains langages comme C, les structures sont similaires aux classes mais ne supportent pas l’héritage.

---

### 6. Les types spéciaux

Certains types ne rentrent pas dans les catégories précédentes :

#### a) **NoneType**
Représente une variable sans valeur (ou valeur nulle).

Exemple :
```python
vide = None
```

#### b) **Fonctions (éléments appelables)**
Les fonctions peuvent être assignées à des variables.

Exemple :
```python
def ajouter(a, b):
    return a + b

operation = ajouter
print(operation(3, 4))  # 7
```

#### c) **Types énumérés (enum)**
Les types énumérés permettent de définir des ensembles de valeurs nommées.

Exemple :
```python
from enum import Enum

class Couleur(Enum):
    ROUGE = 1
    VERT = 2
    BLEU = 3

print(Couleur.ROUGE)  # Couleur.ROUGE
```

---

### 7. Typage dynamique vs statique

- **Typage dynamique** : Les variables peuvent changer de type durant l’exécution (ex. Python).
  ```python
  x = 42      # int
  x = "texte" # str
  ```

- **Typage statique** : Les types sont fixés au moment de la compilation (ex. C, Java).

---

### 8. Conversion de types (casting)

#### a) **Conversion implicite**
Certains langages convertissent automatiquement les types.

Exemple :
```python
x = 5
y = 2.0
resultat = x + y  # Conversion de x en float
```

#### b) **Conversion explicite**
L’utilisateur force le changement de type.

Exemple :
```python
nombre = "42"
converti = int(nombre)  # Conversion de string à int
```

---

### 9. Création d’un outil en ligne de commande

Un outil en ligne de commande est un programme qui s’exécute dans un terminal et accepte des entrées via des arguments.

#### a) **Création basique**

Exemple d’un script Python simple :
```python
import sys

def main():
    if len(sys.argv) != 3:
        print("Usage: python mon_script.py <arg1> <arg2>")
        return

    arg1 = sys.argv[1]
    arg2 = sys.argv[2]
    print(f"Arguments reçus : {arg1}, {arg2}")

if __name__ == "__main__":
    main()
```

#### b) **Utilisation d’une bibliothèque comme argparse**

`argparse` facilite la gestion des arguments en ligne de commande.

Exemple :
```python
import argparse

def main():
    parser = argparse.ArgumentParser(description="Mon outil CLI.")
    parser.add_argument("nom", help="Le nom de l'utilisateur.")
    parser.add_argument("--age", type=int, help="L'âge de l'utilisateur.")

    args = parser.parse_args()

    print(f"Bonjour {args.nom}!")
    if args.age:
        print(f"Vous avez {args.age} ans.")

if __name__ == "__main__":
    main()
```

#### c) **Création d’un outil avancé**

Ajouter des commandes multiples :
```python
import argparse

def ajouter(a, b):
    return a + b

def soustraire(a, b):
    return a - b

def main():
    parser = argparse.ArgumentParser(description="Outil mathématique CLI.")
    subparsers = parser.add_subparsers(dest="commande")

    parser_ajout = subparsers.add_parser("ajouter", help="Addition de deux nombres.")
    parser_ajout.add_argument("a", type=int)
    parser_ajout.add_argument("b", type=int)

    parser_soustraction = subparsers.add_parser("soustraire", help="Soustraction de deux nombres.")
    parser_soustraction.add_argument("a", type=int)
    parser_soustraction.add_argument("b", type=int)

    args = parser.parse_args()

    if args.commande == "ajouter":
        print(ajouter(args.a, args.b))
    elif args.commande == "soustraire":
        print(soustraire(args.a, args.b))

if __name__ == "__main__":
    main()
```

#### d) **Exécution et installation**
Pour rendre l’outil exécutable :
1. Ajoutez un shebang au début du fichier :
   ```python
   #!/usr/bin/env python3
   ```
2. Rendez le script exécutable :
   ```bash
   chmod +x mon_script.py
   ```
3. Ajoutez-le à votre `$PATH` pour l’exécuter depuis n’importe où.

---

### 10. Bonnes pratiques

1. **Commenter le code** pour le rendre compréhensible.
2. **Structurer les outils CLI** pour permettre une extension facile.
3. **Gérer les erreurs** avec des messages clairs.
4. **Documenter l’utilisation** avec des exemples et des descriptions.

---

### 11. Conclusion

Les outils en ligne de commande sont puissants pour automatiser des tâches ou fournir des fonctionnalités pratiques. Avec Python et des bibliothèques comme `argparse`, leur création devient simple et accessible.


Voici comment réaliser une boucle pour parcourir une liste, ainsi que les différentes techniques pour la manipuler efficacement.

---

### **1. Parcourir une liste avec une boucle**
#### **a) Boucle `for` simple**
Permet d'itérer sur chaque élément d'une liste :
```python
fruits = ["pomme", "banane", "cerise"]
for fruit in fruits:
    print(fruit)
```

#### **b) Boucle avec index (fonction `enumerate`)**
Pour accéder à l'index de chaque élément :
```python
fruits = ["pomme", "banane", "cerise"]
for index, fruit in enumerate(fruits):
    print(f"Index {index}: {fruit}")
```

#### **c) Boucle avec `while`**
Pour parcourir une liste avec une condition :
```python
fruits = ["pomme", "banane", "cerise"]
i = 0
while i < len(fruits):
    print(fruits[i])
    i += 1
```

---

### **2. Modifier une liste en boucle**
#### **a) Ajouter des éléments**
Ajout d'un nouvel élément avec `append` :
```python
fruits = ["pomme", "banane"]
for fruit in ["cerise", "orange"]:
    fruits.append(fruit)
print(fruits)  # ["pomme", "banane", "cerise", "orange"]
```

#### **b) Supprimer des éléments**
Suppression d'un élément conditionnellement :
```python
fruits = ["pomme", "banane", "cerise"]
fruits = [fruit for fruit in fruits if fruit != "banane"]
print(fruits)  # ["pomme", "cerise"]
```

#### **c) Remplacer des éléments**
Modification directe via l'index :
```python
fruits = ["pomme", "banane", "cerise"]
for i in range(len(fruits)):
    if fruits[i] == "banane":
        fruits[i] = "fraise"
print(fruits)  # ["pomme", "fraise", "cerise"]
```

---

### **3. Exploitation avancée d'une liste**
#### **a) Trier une liste**
Tri par ordre croissant/décroissant :
```python
nombres = [3, 1, 4, 1, 5]
nombres.sort()
print(nombres)  # [1, 1, 3, 4, 5]

nombres.sort(reverse=True)
print(nombres)  # [5, 4, 3, 1, 1]
```

#### **b) Filtrer les éléments**
Filtrer selon une condition avec les compréhensions :
```python
nombres = [1, 2, 3, 4, 5]
pairs = [n for n in nombres if n % 2 == 0]
print(pairs)  # [2, 4]
```

#### **c) Appliquer une transformation**
Modifier chaque élément avec une compréhension ou `map` :
```python
nombres = [1, 2, 3, 4, 5]
carres = [n ** 2 for n in nombres]
print(carres)  # [1, 4, 9, 16, 25]
```

---

### **4. Copier une liste**
#### **a) Copie superficielle**
Utiliser `copy` ou une tranche :
```python
original = [1, 2, 3]
copie = original.copy()  # ou copie = original[:]
```

#### **b) Copie profonde**
Pour les listes imbriquées, utilisez `deepcopy` :
```python
import copy
original = [[1, 2], [3, 4]]
copie_profonde = copy.deepcopy(original)
```

---

### **5. Fusionner ou diviser une liste**
#### **a) Fusionner deux listes**
Avec `+` ou `extend` :
```python
liste1 = [1, 2]
liste2 = [3, 4]
fusion = liste1 + liste2
print(fusion)  # [1, 2, 3, 4]
```

#### **b) Diviser une liste**
Utilisez des tranches :
```python
nombres = [1, 2, 3, 4, 5]
premiere_moitie = nombres[:3]
seconde_moitie = nombres[3:]
```

---

### **6. Bonnes pratiques pour manipuler les listes**
- Utilisez **des compréhensions** pour des opérations simples.
- Préférez `enumerate` pour gérer les indices dans une boucle.
- Utilisez `set` ou `collections.Counter` pour gérer les doublons ou les fréquences.

---

Créer une interface en ligne de commande (CLI) Python prenant un nombre infini d'arguments peut être réalisé en utilisant la bibliothèque standard `argparse`. Voici comment procéder pour gérer un nombre d'arguments arbitraire :

### Étapes pour une CLI avec un nombre infini d'arguments :
1. Utilisez l'argument `nargs` avec la valeur `'*'` ou `'+'` :
   - `'*'` : zéro ou plus d'arguments.
   - `'+'` : un ou plus d'arguments.

2. Récupérez ces arguments dans une liste pour traitement ultérieur.

---

### Exemple de script CLI avec des arguments illimités

Voici un exemple simple :

```python
import argparse

def main():
    parser = argparse.ArgumentParser(
        description="Une CLI qui accepte un nombre illimité d'arguments."
    )

    # Ajout de l'argument infini
    parser.add_argument(
        'items', 
        nargs='*',  # Accepte zéro ou plus d'arguments
        help="Liste d'éléments à traiter"
    )

    args = parser.parse_args()

    # Affiche les arguments reçus
    print(f"Arguments reçus : {args.items}")

    # Exemple de traitement des arguments
    for i, item in enumerate(args.items, 1):
        print(f"Argument {i} : {item}")

if __name__ == "__main__":
    main()
```

---

### Comment utiliser ce script :
1. Sauvegardez ce code dans un fichier `cli.py`.
2. Exécutez-le en ligne de commande avec divers arguments, par exemple :

```bash
python cli.py arg1 arg2 arg3
```

#### Résultat attendu :
```
Arguments reçus : ['arg1', 'arg2', 'arg3']
Argument 1 : arg1
Argument 2 : arg2
Argument 3 : arg3
```

---

### Extensions possibles :
- **Ajouter des options** (comme `-v` ou `--verbose`).
- **Traiter des types spécifiques** : convertissez les arguments en entiers, flottants, etc.
- **Validation** : ajoutez des contrôles spécifiques sur les arguments.

Besoin de fonctionnalités supplémentaires ? 😊