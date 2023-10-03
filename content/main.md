---
weight: 10
title: API Reference
---

# Introduction

Python est un langage de programmation de haut niveau, interprété et polyvalent.

Créé par Guido van Rossum et lancé pour la première fois en 1991, il est conçu pour être simple à lire et à écrire, grâce à une syntaxe claire et épurée.

Voici quelques-unes de ses particularités :

- Lisible : Python privilégie une syntaxe claire et lisible, rendant le code plus compréhensible.
- Polyvalent : Il est utilisé dans de nombreux domaines, allant du développement web à la science des données, en passant par l'automatisation et le développement de jeux.
- Bibliothèques riches : Python possède une vaste bibliothèque standard, et il existe de nombreux packages tiers disponibles pour presque toutes les applications imaginables.
- Dynamiquement typé : Pas besoin de déclarer le type de variable à l'avance; le type est déterminé au moment de l'exécution.
- Interprété : Python est un langage interprété, ce qui signifie qu'il n'est pas nécessaire de le compiler avant de l'exécuter.
- Communauté active : La communauté Python est vaste et active, offrant une abondance de ressources, de tutoriels et de soutien.

Python est souvent recommandé comme premier langage de programmation pour les débutants en raison de sa simplicité...
mais ne vous y trompez pas: sa puissance et sa flexibilité en font un excellent choix pour les projets professionnels de grande envergure.


# Session 1

## Un langage interprété ?

En quelques mots:

- Interprété : Le code est exécuté ligne par ligne directement par un interpréteur au moment de l'exécution. Pas de phase de compilation séparée. Exemple : Python.

- Compilé : Le code source est transformé en code machine par un compilateur avant l'exécution. Le résultat est un fichier exécutable. Exemple : C, C++.

En bref, les langages compilés sont transformés en code machine avant l'exécution,
tandis que les langages interprétés sont exécutés directement par un interpréteur au moment de l'exécution.
Les premiers sont plus rapide car le code machine n'est créé qu'une fois et compris directement par le processeur,
les seconds sont pus lents car le code source est réinterprété à chaque exécution et doit être traduit en instructions que le processeur comprends.

Il vaut mieux un langage compilé alors ?
Pourquoi on fait du Python ?

Déjà parce que la plupart des langages compilés sont sensiblement complexe en comparaison aux langages interprétés,
et le gain à l'exécution est souvent le résultat d'un cycle de développement plus long.
Ensuite, parce que les performances des langages interprétés sont largement suffisantes dans une écrasante majorité de cas,
tout le monde ne fait pas du trading haute-fréquence ou de l'embarqué temps-réel.
Enfin, parce que la limite entre interprété et compilé était très nette il y a vingt ans, mais beaucoup moins aujourd'hui.

En pratique,
la plupart des langages interprétés aujourd'hui sont compilés pour une machine virtuelle,
Python n'est pas vraiment interprété ligne par ligne mais il est compilé pour la PVM (Python Virtual Machine).

- Lorsque vous exécutez un script Python, le code source .py est d'abord compilé en bytecode,
Ce bytecode est une représentation de bas niveau, condensée, indépendante de la plateforme, du code source.

- Ce bytecode est ensuite écrit dans un fichier .pyc qui est stocké dans un dossier __pycache__.
Cela permet d'accélérer les exécutions ultérieures du script, car le code n'a pas besoin d'être recompilé à moins qu'il n'ait été modifié.

- La machine virtuelle Python (PVM) exécute ensuite ce bytecode, ligne par ligne.

Le bytecode Python n'est pas du code machine natif (comme celui produit pour les langages compilés comme C ou C++).
Au lieu de cela, il est conçu pour être exécuté par l'interpréteur Python, ce qui permet à Python de conserver sa portabilité entre différentes plateformes.

Les performances sont nécessairement en dessous d'un programme compilé en code natif,
puisque le bytecode va ensuite devoir être interprété en instructions natives,
mais une interprétation de bytecode est sensiblement plus rapide qu'une interprétation ligne à ligne.

Notez qu'il y a actuellement un projet en cours de développement,
le projet Mojo,
qui vise à produire un compilateur capable de convertir du Python en code natif:
on aurai alors les performances d'un langage comme C++ mais avec la simplicité de Python.


## Syntaxe

Nous n'allons pas voir tous les détails de la syntaxe d'un coup,
on va pouvoir les découvrir progressivement au fur et à mesure que le cours avance,
mais voici quelques spécificités pour pouvoir commencer à comprendre les premiers exemples.


### Indentation
Contrairement à de nombreux autres langages, Python utilise l'indentation (espaces ou tabulations) pour délimiter les blocs de code.
Cela rend le code Python propre et lisible.
> indentation
```python
if True:
    print("Ceci est vrai.")
else:
    print("Ceci est faux.")
```

### Commentaires
Les commentaires en Python commencent par le symbole #. Tout ce qui suit ce symbole sur la même ligne est considéré comme un commentaire.
> commentaires
```python
# Ceci est un commentaire
print("Ceci n'est pas un commentaire.")  # Mais ceci en est un.
```

### Variables
En Python, les variables n'ont pas besoin d'être déclarées avec un type spécifique. Vous pouvez simplement les assigner à une valeur.
> Variables
```python
a = 10
b = "Bonjour"
c = 3.14
```

Elles peuvent aussi changer de type en cours de route:
> Changement de type en cours de route
```python
a = 10
a = "Bonjour"
```

### Instructions
Les instructions sont exécutées de haut en bas.
Vous pouvez utiliser des points-virgules pour séparer plusieurs instructions sur une seule ligne, bien que cela ne soit pas courant en Python.
> instructions
```python
x = 5
y = 10
z = 20; total = x + y + z
```

### Importation de modules
Python possède une riche bibliothèque standard, et vous pouvez également utiliser des bibliothèques tierces. Pour accéder aux fonctions d'un module, vous devez l'importer.
> import
```python
import math
racine = math.sqrt(16)  # Utilise la fonction sqrt du module math
```



## Les points d'entrées

Un "point d'entrée" désigne le point de départ d'un programme ou d'un script. Il existe plusieurs façons d'exécuter du code Python, et chacune a son propre point d'entrée. Voici une vue d'ensemble des différents points d'entrée en Python :

### Script via `__main__`

Lorsque vous exécutez un fichier Python directement (par exemple, python mon_script.py), le code à l'intérieur de ce fichier est exécuté.
Dans ce contexte, la variable spéciale `__name__` du fichier est définie sur `__main__`.
Cela permet aux développeurs d'ajouter une condition if `__name__` == `__main__`: pour s'assurer que certaines parties du code ne sont exécutées que lorsque le fichier est lancé directement, et non lorsqu'il est importé comme un module.

> script via __main__
```python
#! /usr/bin/env python

if __name__ == "__main__":
    print('hello world !')
```



### REPL (Read-Eval-Print Loop)

Le REPL est un environnement interactif où vous pouvez saisir et exécuter du code Python ligne par ligne. Il est souvent utilisé pour des tests rapides, des débogages ou des expérimentations.
Vous pouvez accéder au REPL simplement en tapant python (ou python3 selon votre installation) dans votre terminal ou console.
Dans le REPL, chaque instruction est immédiatement évaluée et le résultat est affiché.

> le REPL
```sh
$ python 
Python 3.11.4 (main, Jul  5 2023, 08:40:20) [Clang 14.0.6 ] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> print('hello world !')
hello
>>> x = 42
>>> x
42
>>> quit()
$
```


### Module

Un module est un fichier Python contenant des fonctions, des classes et des variables, ainsi que du code exécutable.

Les modules peuvent être importés dans d'autres fichiers Python ou modules à l'aide de l'instruction import.
Par exemple, `import math` importe le module math standard de Python aussi bien dans un script que dans le REPL.

> module importé dans un script __main__
```python
#! /usr/bin/env python

import math

if __name__ == "__main__":
    print(math.floor(1.1))
```

> module importé dans le REPL
```sh
$ python
Python 3.11.4 (main, Jul  5 2023, 08:40:20) [Clang 14.0.6 ] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import math
>>> math.floor(1.1)
1
>>> quit()
$
```

Lorsqu'un module est importé, le code à l'intérieur du module est accessible au script ou au REPL.
Python fourni un grand nombre de modules dans sa librairie standard,
encore plus de modules mis à disposition par la communauté des développeurs Pythons et accessible via des outils d'installation,
et vous pouvez faire vos propres modules qui vous permetteront de réutiliser le même code dans plusieurs projets.






## Commentaires

Les commentaires en programmation sont des annotations ajoutées au code qui ne sont pas exécutées lors de son fonctionnement. Ils sont essentiels pour plusieurs raisons. Tout d'abord, ils permettent au développeur d'expliquer son raisonnement, de décrire la fonction d'un segment de code ou de donner des informations sur la manière dont une partie spécifique du programme fonctionne. Cela est particulièrement utile pour les équipes de développement, car cela facilite la compréhension du code par d'autres membres. De plus, les commentaires peuvent servir à désactiver temporairement certaines parties du code sans les supprimer, ce qui est pratique lors du débogage. En Python, les commentaires sont précédés du caractère # et s'étendent jusqu'à la fin de la ligne. Bien que le code puisse fonctionner sans commentaires, un code bien commenté est toujours plus maintenable, compréhensible et collaboratif.



> Hello world avec commentaire
```python
#! /usr/bin/env python

# Ce programme affiche le message "Hello, world!" à l'écran
print("Hello, world!")
```

## Variables

Dans le monde de la programmation, les variables jouent un rôle central et fondamental. Une variable peut être imaginée comme une boîte dans la mémoire de l'ordinateur, où l'on peut stocker, récupérer ou modifier des informations. Chaque variable possède un nom unique qui permet d'identifier et d'accéder à son contenu. De plus, les variables ont des types, tels que entier, chaîne de caractères ou liste, qui déterminent la nature des données qu'elles peuvent contenir. Comprendre le concept de variables est essentiel, car elles servent de pont entre le code et les données, permettant aux programmes d'interagir dynamiquement avec les informations. En maîtrisant les variables, on acquiert la capacité de manipuler des données de manière flexible et puissante, ouvrant la porte à des applications plus complexes et interactives.


> Hello world avec variable et f-string
```python
#! /usr/bin/env python

# Déclaration d'une variable contenant un nom
nom = "Alice"

# Utilisation de la variable pour personnaliser le message
# attention au f devant le guillemet ouvrant:
# il indique que la chaine contient une variable qui sera subtituée par son contenu
print(f"Hello, {nom}!")
```

## Fonctions

Les fonctions sont des éléments fondamentaux de la programmation en Python, servant à regrouper des blocs de code pour effectuer une tâche spécifique.
Elles permettent de structurer et d'organiser le code, le rendant plus lisible et réutilisable.

Une fonction est définie avec le mot-clé `def``, suivi du nom de la fonction et d'une paire de parenthèses contenant éventuellement des paramètres. Le corps de la fonction est indenté et contient les instructions à exécuter.


> définition d'une fonction et appel
```python
def myprint(arg):
    print(arg)

myprint("Hello, Alice!")
```

Une fois définie, une fonction peut être appelée n'importe où dans le code en utilisant son nom suivi de parenthèses.
Les fonctions peuvent retourner des valeurs à l'aide du mot-clé return.


> définition d'une fonction avec valeur de retour
```python
def myprint2(arg):
    print(arg)
    return 42

x = myprint("Hello, Alice!")

```

En Python, les fonctions peuvent accepter un nombre variable d'arguments, avoir des valeurs par défaut pour certains paramètres et même gérer des arguments sous forme de clés. L'utilisation de fonctions favorise les bonnes pratiques de programmation, comme la modularité et la DRY (Don't Repeat Yourself), en évitant la redondance et en facilitant la maintenance du code.

Il existe deux types de fonctions:

### Fonctions "builtin"
Les fonctions builtin sont des fonctions qui font partie du language lui-même,
comme par exemple `print()`, `len()` ou encore `type()` qui sont immédiatement à disposition.

Dans les exemples précédents,
`myprint()` et `myprint2()` n'existaient pas avant d'être définies,
mais `print()` était accessible sans avoir à importer le moindre module.

Il y a plus d'une soixantaine de fonctions builtins en Python,
nous en verrons quelques unes ensemble au fur et à mesure de l'avancée du cours,
et en général on tombe assez rapidement sur celles dont on a besoin donc elles ne méritent pas qu'on s'attarde trop:
elles reviendront se faire connaitre le moment venu.

> quelques builtins
```python
>>> x = 42
>>> type(x)
<class 'int'>
>>> len("test")
4
>>> min(2, 3)
2
>>> max(2, 3)
3
```


### Fonctions non builtin
Les fonctions non-builtin sont toutes les fonctions qui ne sont pas fournies par le langage lui-même,
mais qui sont définies par vos soins ou exposées par un module que vous importez.



## Paramètres de fonctions
Les fonctions en Python peuvent accepter des arguments, appelés paramètres, qui permettent de passer des informations à la fonction.
Ces paramètres peuvent être de différents types :

### Paramètres Positionnels
Ce sont les paramètres les plus courants. Ils sont définis par leur position dans la définition de la fonction.
> Paramètres positionnels
```python
def ma_fonction(a, b, c):
    return a + b + c
```

### Paramètres par défaut
Ces paramètres ont une valeur par défaut qui est utilisée si aucune valeur n'est fournie lors de l'appel de la fonction.
> Paramètres par défaut
```python
def ma_fonction(a, b=5):
    return a + b
```

### Paramètres mot-clé
Lors de l'appel d'une fonction, vous pouvez spécifier des arguments en utilisant le nom du paramètre, ce qui permet de passer les arguments dans n'importe quel ordre.
> Paramètres mot-clé
```python
def ma_fonction(a, b, c):
    return a + b + c

ma_fonction(b=2, c=3, a=1)
```


### Paramètres arbitraires
Si vous ne savez pas combien d'arguments seront passés à votre fonction, vous pouvez utiliser *args pour les paramètres positionnels et **kwargs pour les paramètres mot-clé.
> Paramètres arbitraires
```python
>>> def ma_fonction(*args, **kwargs):
...     print(args)
...     print(kwargs)
...
>>> ma_fonction(1, 2, 3)
(1, 2, 3)
{}
>>> ma_fonction(a=1, b=2, c=3)
()
{'a': 1, 'b': 2, 'c': 3}
```


## Types

En Python, chaque valeur est associée à un type de données spécifique qui détermine la nature de cette valeur. Les types de données fondamentaux en Python sont :

- Entiers (`int`): Ce sont des nombres entiers, sans partie décimale. Exemple : 5, -3, 42.
- Nombres à virgule flottante (`float`) : Ce sont des nombres qui ont une partie décimale. Exemple : 5.0, -3.14, 2.71.
- Chaînes de caractères (`str`) : Ce sont des séquences de caractères, généralement utilisées pour représenter des mots ou des textes. Exemple : "Hello", 'Python'.
- Listes (`list`) : Collections ordonnées d'éléments qui peuvent être de n'importe quel type. Exemple : [1, 2, 3], ["a", "b", "c"].
- Tuples (`tuple`) : Similaires aux listes, mais immuables, ce qui signifie que leurs éléments ne peuvent pas être modifiés une fois définis. Exemple : (1, 2, 3).
- Dictionnaires (`dict`) : Collections non ordonnées de paires clé-valeur. Exemple : {"nom": "Alice", "âge": 30}.
- Ensembles (`set`) : Collections non ordonnées d'éléments uniques. Ils sont utiles pour stocker des éléments sans doublons. Exemple : {1, 2, 3, 3} donnera {1, 2, 3}.
- Booléens (`bool`) : Représentent les valeurs de vérité, soit `True` (vrai) ou `False` (faux).
- Classes : Elles permettent de définir des objets et représentent la base de la programmation orientée objet en Python, on reviendra dessus.


Ces types de données sont les briques de base de la programmation en Python.
Ils permettent aux développeurs de représenter et de manipuler une grande variété d'informations, des simples nombres aux structures de données complexes.

### Truthiness
À ma connaissance,
tous les langages ont une notion de "truthiness":
toute valeur de tout type est implicitement vraie ou fausse.

Par exemple, en C, la valeur 0 est considérée comme `False` et toute valeur différente de 0 est considérée comme `True`,
donc `if x { ... }` est considéré comme vrai et exécute le bloc à partir du moment ou `x` n'est pas égal à zéro.

Python a une approche intéressante de la truthiness:
toute valeur égale à 0,
ou "vide" pour les types non numériques,
est considérée comme `False`:
un tableau vide est faux,
une chaine vide est fausse,
un dictionnaire vide est faux...

Il est donc possible de tester rapidement si un type est vide en testant sa truthiness comme dans les exemples suivants.
> Truthiness
```python
>>> x = []
>>> x == False
False
>>> if x:
...     print("has data")
... else:
...     print("is empty")
...
is empty
>>>
```


### None
`None` est un type spécial en Python qui représente l'absence de valeur ou la nullité.
Il est souvent utilisé pour signifier qu'une variable existe,
mais qu'elle n'a pas encore été assignée à une valeur spécifique ou pour indiquer qu'une fonction ne renvoie rien.

> None
```python
>>> def foobar():
...     pass
... 
>>> x = foobar()
>>> x is None
True
>>> 
```

## f-string et spécificateurs
Depuis peu,
Python propose une fonctionnalité nommée `f-string` que nous avons utilisé un peu plus haut:
les chaines de caractères préfixées par `f` sont considérées comme contenant des variables à remplacer.
Par exemple,
`f"Salut, {prenom}"` va remplacer `{prenom}` par la valeur actuelle de la variable `prenom` au moment où la `f-string` est évaluée.

Avant,
il fallait avoir recours à un autre mécanisme,
toujours utile selon les cas d'usage:
les spécificateurs.

Les spécificateurs sont des symboles utilisés principalement dans les fonctions de formatage de chaînes,
comme `print()` ou la méthode `.format()` de tous les objets de types `str`,
pour contrôler la manière dont les valeurs sont affichées.

Voici quelques spécificateurs courants :

- %s : Formatage pour les chaînes de caractères.
- %d : Formatage pour les entiers.
- %f : Formatage pour les nombres à virgule flottante.
- %.2f : Formatage pour les nombres à virgule flottante avec deux décimales.

> Spécificateurs
```python
nom = "Alice"
age = 30
taille = 1.75

print("Mon nom est %s, j'ai %d ans et je mesure %.2f mètres." % (nom, age, taille))
```




## Opérateurs

### Opérateurs arithmétiques

Ils sont utilisés pour effectuer des opératins mathématiques.

#### Addition: +
```python
>>> x = 5 + 3
>>> x
8
```

#### Soustraction: -
```python
>>> x = 5 - 3
>>> x
2
```

#### Multiplication: *
```python
>>> x = 5 * 3
>>> x
15
```

#### Division: /
```python
>>> x = 8 / 2
>>> x
4.0
```

#### Modulo: %
```python
>>> x = 13 % 12
>>> x
1
```

#### Exponentiation (puissance): **
```python
>>> x = 2 ** 3
>>> x
8
```

#### Division entière: //
```python
>>> x = 5 // 3
>>> x
1
```

### Opérateurs de comparaison

Ils sont utilisés pour comparer deux valeurs.

#### Égal: ==
```python
>>> x = 5 == 3
>>> x
False
```

#### Différent: !=
```python
>>> x = 5 != 3
>>> x
True
```

#### Supérieur: >
```python
>>> x = 5 > 3
>>> x
True
```

#### Inférieur: <
```python
>>> x = 8 < 2
>>> x
False
```

#### Supérieur ou égal: >=
```python
>>> x = 5 >= 5
>>> x
True
```

#### Inférieur ou égal: <=
```python
>>> x = 2 <= 3
>>> x
True
```


### Opérateurs logiques
Ils sont utilisés pour combiner des expressions conditionnelles.

#### And
```python
>>> x = 5 > 3 and 5 < 10
>>> x
True
```

#### Or
```python
>>> x = 5 > 3 or 5 > 10
>>> x
True
```

#### Not
```python
>>> x = 5 > 3
>>> x
True
>>> not x
False
>>> x = not(5 > 3)
>>> x
False
```


### Opérateurs d'affectation
Ils sont utilisés pour assigner des valeurs aux variables.

#### =
Assigne une valeur.
```python
>>> x = 5
>>> x
5
```

#### +=
Équivaut à ajouter à la valeur existante,
`x += 5` équivaut à `x = x + 5`.
```python
>>> x += 5
>>> x
10
```

#### -=
Équivaut à supprimer à la valeur existante.
```python
>>> x -= 1
>>> x
9
```

#### *=
Équivaut à multiplier la valeur existante.
```python
>>> x *= 2
>>> x
18
```

#### /=
Équivaut à diviser la valeur existante.
```python
>>> x /= 2
>>> x
9.0
```

#### %=
Équivaut à appliquer un modulo à la valeur existante.
```python
>>> x = 10
>>> x %= 3
>>> x
1
```

#### //=
Équivaut à appliquer une division entière à la valeur existante.
```python
>>> x = 10
>>> x //= 3
>>> x
3
```

#### **=
Équivaut à appliquer une puissance  à la valeur existante.
```python
>>> x = 2
>>> x **= 10
>>> x
1024
```

### Opérateurs binaires

Ces opérateurs sont particulièrement utiles dans des domaines tels que la programmation de bas niveau,
la cryptographie,
la compression de données et d'autres domaines où la manipulation directe des bits est nécessaire.

Bien que leur utilisation soit moins courante dans la programmation de haut niveau,
il est toujours bon de les connaître et de comprendre comment ils fonctionnent.


#### ET binaire `&`
Cet opérateur renvoie un nombre dont chaque bit est le résultat de l'opération "ET" bit à bit des opérandes.
> ET binaire
```python
>>> x = 5  # 0101 en binaire
>>> y = 3  # 0011 en binaire
>>> print(x & y)  # 0001 en binaire, soit 1 en décimal
```

#### OU binaire `|`
Renvoie un nombre dont chaque bit est le résultat de l'opération "OU" bit à bit des opérandes.
> OU binaire
```python
>>> x = 5  # 0101 en binaire
>>> y = 3  # 0011 en binaire
>>> print(x | y)  # 0111 en binaire, soit 7 en décimal
```

#### OU exclusif binaire `^`
Renvoie un nombre dont chaque bit est le résultat de l'opération "OU exclusif" bit à bit des opérandes.
> OU binaire
```python
>>> x = 5  # 0101 en binaire
>>> y = 3  # 0011 en binaire
>>> print(x ^ y)  # 0110 en binaire, soit 6 en décimal
```

#### Négation binaire `~`
Inverse tous les bits du nombre.
> Négation binaire
```python
>>> x = 5  # 0101 en binaire
>>> print(~x)  # 1010 en binaire
```

#### Décalage à gauche `<<`
Décale les bits du premier opérande vers la gauche d'un nombre de positions spécifié par le second opérande.
> Décalage à gauche
```python
>>> x = 4  # 0100 en binaire
>>> print(x<<1)  # 1000 en binaire, 8
```

#### Décalage à droite `>>`
Décale les bits du premier opérande vers la gauche d'un nombre de positions spécifié par le second opérande.
> Décalage à droite
```python
>>> x = 4  # 0100 en binaire
>>> print(x >> 1)  # 0010 en binaire, soit 2 en décimal
```


#### Assignations

Tous les opérateurs supportent des versions "avec assignation" comme on a pu voir sur les opérateurs arithmétiques:
`x &= 1`,  `x |= 1`, `x ^= 1`, `x <<= 1` ou encore `x >>= 1`.


#### À quoi ça peut donc bien servir ?

Au delà des cas où les opérations binaires s'imposent à vous,
parce que vous implémentez une specification où il est explicitement écrit "mettre le 13ème bit à 1",
les opérateurs binaires permettent de simplifier certains motifs de code.

Je vais donner un seul exemple pour que vous compreniez leur puissance et pourquoi ils est intéressant de les creuser:

Si je veux stocker des informations concernant un utilisateur,
comme par exemple ses droits sur une application,
je peux le faire en assignant à chaque permission une variable de type `bool`...
mais lorsque je voudrais mettre ça en base de donnée,
ma table aura elle aussi une colonne pour chaque permission.
Donc si j'ai 30 permissions différentes,
j'ai 30 bool et 30 colonnes...
qui débouche sur 30 ensemble de fonctions pour chaque droit,
des test dans tous les sens pour vérifier si des droits sont compatibles (est-ce que c'est ok si j'ai le droit X et le droit Y),
etc...

Ça marche, c'est ce que font la plupart des personnes.

Ou alors...

On prends un `int`,
on considère chacun de ces bits comme un `bool`: si le bit est à 0 c'est faux, s'il est à 1 c'est vrai.
On a une seule valeur qui encode les permissions,
une seule colonne en base de donnée,
un seul set de fonction qui utilise les opérateurs binaires pour savoir si oui ou non un bit est "setté",
et les tests sont plus simples car il est possible de vérifier plusieurs bits d'un coup et de fournir une liste de combinaisons interdites.

```python
user.canExec = False
user.canWrite = True
user.canRead = True
if not user.canExec and user.canWrite and user.canRead:
    print("l'utilisateur peut ecrire et lire mais pas executer")

vs.

user.permissions = WRITE|READ
if user.permissions & EXEC|WRITE|READ == WRITE|READ:
    print("l'utilisateur peut ecrire et lire mais pas executer")

```

C'est un coup à prendre,
un peu de travail en amont pour comprendre la logique des opérateurs &, |, ^ et ~,
mais le bénéfice est immense:
il existe de nombreux cas où le code est grandement simplifié،
où le stockage en base de donnée est simplifié,
où les performances sont améliorées,
et surtout c'est une connaissance qui se transpose à tous les langages.





## Structures de contrôle et boucles

Les structures de contrôle sont essentielles en programmation car elles permettent de diriger le flux d'exécution d'un programme.
En Python, comme dans la plupart des langages de programmation, il existe plusieurs structures de contrôle principales.

### Structures de contrôle conditionnelles

Elles permettent d'exécuter certains blocs de code en fonction de conditions spécifiques.

#### if
Exécute un bloc de code si une condition est vraie.

```python
#! /usr/bin/env python

# Déclaration d'une variable avec la valeur 42
x = 42
if x == 42:
    print("x est égal à 42")
```



#### elif
Vérifie une autre condition si la condition précédente n'est pas vraie.

```python
#! /usr/bin/env python

x = 43
if x == 42:
    print("x est égal à 42")
elif x == 43:
    print("x est égal à 43")
```


#### else
Exécute un bloc de code si aucune des conditions précédentes n'est vraie.

```python
#! /usr/bin/env python

x = 44
if x == 42:
    print("x est égal à 42")
elif x == 43:
    print("x est égal à 43")
else:
    print("x n'est égal ni à 42, ni à 43)
```

#### pass
Permet de remplacer un bloc de code pour... ne rien faire.
La plupart du temps,
il sert à ce que la syntaxe du langage soit respectée "le temps de" finir une implémentation,
mais nous verrons par la suite qu'il s'imposera de lui-même dans certains cas.

> pass
```python
#! /usr/bin/env python

def mafonction():
    pass

x = 42
if x == 42:
    print("x est égal à 42")
else:
    pass # TODO: à implémenter plus tard
```

#### match

Le mot-clé `match` a été introduit dans Python 3.10 comme une extension de la capacité de correspondance de motifs (ou "pattern matching") du langage.
Il offre une manière plus expressive et lisible de traiter les structures de données et de prendre des décisions basées sur la forme et le contenu de ces structures.

La correspondance de motifs avec match peut être vue comme une version généralisée et améliorée de l'instruction switch/case présente dans d'autres langages,
mais avec des capacités beaucoup plus puissantes.

> match
```python
def http_status(code):
    match code:
        case 200:
            return "OK"
        case 403:
            return "Forbidden"
        case 404:
            return "Not Found"
        case 500:
            return "Internal Server Error"
        case _:
            return "Autre"

vs

def http_status(code):
    if code == 200:
        return "OK"
    elif code == 403:
        return "Forbidden"
    elif code == 404:
        return "Not Found"
    elif code == 500:
        return "Internal Server Error"
    else:
        return "Autre"
```

La structure de contrôle match est extrêmement puissante et flexible,
elle peut être utilisée avec des motifs de "matching" plus complexes.
Nous ne les verrons pas tous tout de suite,
certains repointeront le bout de leur nez plus tard,
mais nous allons voir encore un exemple qui exploite les variables de capture.



##### Variables de capture
Dans l'exemple de match plus complexe,
les variables `x` et `y` prennent a valeur de leur position dans la variable `point`.

> match plus complexe
```python
point = (2, 3)

match point:
    case (0, 0):
        print("Origine")
    case (0, y):
        print(f"Sur l'axe des Y, à la position {y}")
    case (x, 0):
        print(f"Sur l'axe des X, à la position {x}")
    case (x, y):
        print(f"Position ({x}, {y})")
    case _:
        print("Autre")
```


### Structures de contrôle de boucle

Elles permettent d'exécuter un bloc de code plusieurs fois.

#### for
Parcourt une séquence et exécute un bloc de code pour chaque élément de cette séquence.

```python
#! /usr/bin/env python

for i in range(0, 10):
    print(f"tour de boucle {i}")
```


#### while
Exécute un bloc de code tant qu'une condition est vraie.

```python
#! /usr/bin/env python

i = 0
while i < 10:
    print(f"tour de boucle {i}")
    i = i + 1
```

### Structures de contrôle de boucle
Elles permettent d'altérer le comportement d'une boucle.

#### break
Termine la boucle en cours et passe à la suite du programme.

```python
#! /usr/bin/env python

for i in range(0, 10):
    if i == 3:
        break
    print(f"tour de boucle {i}")
```

#### continue
Termine la boucle en cours et passe à la suite du programme.

```python
#! /usr/bin/env python

for i in range(0, 10):
    if i == 3:
        continue
    print(f"tour de boucle {i}")
```

## Pointeurs et références

En Python, les concepts de pointeurs et de références sont gérés de manière différente par rapport à des langages comme C ou C++.

> références
```python
>>> a = [1, 2, 3]
>>> b = a
>>> a
[1, 2, 3]
>>> b
[1, 2, 3]
>>> a.append(4)
>>> b
[1, 2, 3, 4]
>>>
```

Dans l'exemple ci-joint,
`a` et `b` font référence au même objet liste en mémoire.
Si vous modifiez la liste via la variable `a`, les modifications seront également visibles via la variable `b`, car elles pointent vers le même objet.

Il faut imaginer que le tableau a été alloué quelque part en mémoire,
et que `a` et `b` sont des étiquettes collées sur cet emplacement mémoire.
Les deux étiquttes sont sur la même case,
si le contenu change,
peu importe que l'on demande ce qu'il y a derrière l'étiquette `a` ou `b`,
c'est le même contenu modifié.


### Absence de pointeurs et passage par référence

Contrairement à des langages comme C ou C++,
Python n'a pas de pointeurs explicites.

C'est-à-dire que vous ne pouvez pas accéder directement à la mémoire ou manipuler des adresses mémoire comme vous le feriez avec des pointeurs.
Cela rend Python plus sûr et plus facile à utiliser, car il évite de nombreux pièges et erreurs courants associés à la manipulation directe de la mémoire.

Lorsque vous passez un objet mutable (comme une liste ou un dictionnaire) à une fonction,
vous passez en réalité une référence à cet objet.
Cela signifie que si la fonction modifie l'objet,
ces modifications seront reflétées à l'extérieur de la fonction.

> Passage par référence
```python
def ajouter_element(lst):
    lst.append(4)

a = [1, 2, 3]
ajouter_element(a)
print(a)  # Affiche [1, 2, 3, 4]
```

Dans l'exemple du passage par référence,
la liste a est modifiée à l'intérieur de la fonction `ajouter_element()` car une référence à la liste est passée à la fonction.


En Python, il est essentiel de comprendre que les variables sont des références à des objets et que la manipulation de ces références peut avoir des effets sur les objets sous-jacents. Bien que Python n'ait pas de pointeurs explicites, la manière dont il gère les références offre une grande flexibilité tout en évitant les complications associées à la gestion directe de la mémoire.


## Allocation et désallocation dynamique

L'allocation et la désallocation dynamiques sont des concepts essentiels en programmation, permettant de gérer la mémoire utilisée par les applications.
En Python, ces concepts sont traités de manière quelque peu différente par rapport à des langages de bas niveau comme C ou C++.

### Allocation Dynamique

En Python, l'allocation de mémoire est gérée automatiquement.
Lorsque vous créez un nouvel objet, Python alloue automatiquement la mémoire nécessaire pour cet objet.
Par exemple, lorsque vous créez une nouvelle liste ou un nouveau dictionnaire, Python s'occupe de l'allocation de mémoire pour ces structures.

> allocation dynamique
```python
# Allocation de mémoire pour une liste
ma_liste = [1, 2, 3, 4, 5]

# Allocation de mémoire pour un dictionnaire
mon_dict = {"clé": "valeur"}
```

### Désallocation dynamique et garbage collection

La désallocation de mémoire est également gérée automatiquement en Python grâce à un mécanisme appelé "garbage collection" (collecte des déchets).
Le garbage collector de Python détecte les objets qui ne sont plus référencés par le programme et libère la mémoire qu'ils occupent.

Lorsqu'une variable n'est plus utilisée ou qu'elle sort de la portée, elle n'est pas immédiatement désallouée.
Au lieu de cela, Python marque cette mémoire comme étant récupérable.
Le garbage collector intervient périodiquement pour récupérer cette mémoire.

> garbage collection
```python
def ma_fonction():
    temp_liste = [10, 20, 30]  # Allocation de mémoire pour une liste
    # À la fin de cette fonction, temp_liste sort de la portée

# Après l'appel de cette fonction,
# la mémoire utilisée par temp_liste est marquée comme récupérable
ma_fonction()
```

### Références circulaires
Une référence circulaire se produit lorsque deux objets (ou plus) se réfèrent mutuellement, créant ainsi un cycle.
Le garbage collector de Python est capable de détecter et de gérer les références circulaires, évitant ainsi les fuites de mémoire.

> Références circulaires
```python
>>> a = {}
>>> b = {}
>>> a['b'] = b
>>> b['a'] = a
>>> a
{'b': {'a': {...}}}
>>> b
{'a': {'b': {...}}}
>>> 
```

### Un dernier mot sur la mémoire

En Python, les développeurs n'ont généralement pas à se soucier de l'allocation et de la désallocation manuelles de la mémoire, car le langage s'en occupe automatiquement.

Cela simplifie le développement et réduit le risque d'erreurs liées à la mémoire...
mais, il est toujours bon de comprendre comment la gestion de la mémoire fonctionne en coulisse,
en particulier pour les applications à forte consommation de ressources ou pour le débogage.

Python ne vous force pas à faire des allocations et désallocations vous-même,
il les fait à votre place,
c'est à double tranchant:
le développement est simplifié et les bugs de gestion mémoire sont quasi inexistants...
mais vous ne pouvez pas gérer la mémoire aussi finement que vous le voulez.


## Exercices

### exo01.py - input et print
À l'aide des fonctions builtin `input()` et `print()`,
écrire un programme qui demande à l'utilisateur d'entrer son prénom et son nombre préféré,
puis afficher les informations.

> exo01.py
```sh
$ python exo01.py
Quel est ton prénom ? Gilles
Quel est ton nombre préféré ? 42
Tu t'appelles Gilles et ton nombre préféré est 42.
$ 
```

### exo02.py - boucle for
Créer une boucle `for` qui affiche les nombres de 1 à 10.

> exo02.py
```sh
$ python exo02.py
1
2
3
4
5
6
7
8
9
10
$ 
```

### exo03.py - boucle while
Créer une boucle `while` qui affiche les nombres de 1 à 10,
sans afficher le chiffre 3.

> exo03.py
```sh
$ python exo03.py
1
2
4
5
6
7
8
9
10
$ 
```

### exo04.py - puissance de 2
En important le module `sys`,
vous aurez accès aux paramètres passés à votre programme au travers du tableau `sys.argv`.
La fonction builtin `int()` permet de convertir une chaine en nombre,
donc `int("10")` retourne `10`.
Créer une fonction `puissance(n)` qui retourne 2 à la puissance de `n`.

> exo04.py
```sh
$ python exo04.py
1024
$ 
```
