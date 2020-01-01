# 7 types de données

Une variable en JS peut contenir plusieurs types. Elle peut être à un moment une chaîne et dans un autre un nombre.

## Le nombre

Les nombres représentent les entiers et les flottants. Il y a plusieurs opérations pour les nombres : multiplication `*`, division `/`, addition `+`, soustraction `-`. Outres les nombres réguliers, ils sont nommés "valeurs numériques spéciale" qui appartient à ce type de données: `Infinity`, `-Infinity` et `NaN`.

## Chaîne de caractères

3 types de quotes:

*   **Double ("")**.
*   **Simple('')**.
*   **Backticks(``)**.

Double et simple sont pareil, 0 différences en js. Backticks est une quote "fonctionnalité étendu". Il permet d'insérer des variables et expressions dans la chaîne en écrivant ${..}.

## Un booléen (type logique)

2 valeurs:

*   **`True`**.
*   **`False`**.

Ce type est utilisé pour stocker das valeurs yes/no , où `true` veut dire "oui, correct" et `false` veut dire "non, incorrect".

## La valeur `null`

C'est une valeur spéciale qui représente "rien", "le vide" ou "valeur inconnu".

## La valeur `undefined`

Elle veut dire que la valeur n'est pas assigner. Si une variable est déclarée mais pas assigner, la valeur est "undefined".

## Objet et Symbol

Le type `object` est spécial. Tout les autres types sont appellés "primitive" parce que leurs valeurs peut contenir qu'une chose. Alors que `object`, est utilisé pour stocker des collections de données et des entités complexe.

Le type `symbol` est utilisé pour créer des identifiants unique pour `object`.

## L'opérateur `typeof`

Il retourne un type d'argument. Utile si l'on veut savoir le type de quelque chose. Il supporte 2 formes de syntaxe:

*   **comme opérateur => typeof x**
*   **comme fonction => typeof (x)**
