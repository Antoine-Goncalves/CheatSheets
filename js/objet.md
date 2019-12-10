# Objet en JS : `Object`

Pour rappel, il y a **7 types de données en JS**. 6 sont appellés _primitives_, car leurs valeurs contiennent seulement une seule chose. (cela peut être une chaîne de caractère, ou un nombre). Au contraire, **les objets sont utilisés pour stockés des collections de différentes données et des entités plus complexe**. En JS, les objets pénetrent presque tout les aspect du langage.

Un objet peut être **créer avec les acolades {...}** avec une liste optionnel de propriétés, **une propriété** est une **paire "clé: valeur"**, où _"clé" est une chaine de caractère (appellé aussi nom de propriété)_, et _"valeur" peut être n'importe quoi_. On peut imaginer un objet dans un tiroir avec plusieurs dossiers. Chaque morceau de données est stocké dans son fichier par une définition.

Un objet vide _("tiroir vide")_

2 syntaxes possibles :

`let user = new Object(); // "object constructor" syntaxe`
`let user = {}; // "object literal" syntaxe`

Litéral et propriétés : On peut **immédiatemment ajouter plusieurs propriétés dans {..} comme "clé:valeur"**.

```
let user = {                // un objet.
    name: "Antoine",        // clé name avec "Antoine".
    age: 23,                // clé age avec 23.
};
```

Une propriété a une clé (connu comme "name" ou "identifier") après les ":" et une valeur à droite. Dans l'objet user, il y a 2 propriétés :

- La 1ère propriété est le nom "name" et la valeur "Antoine".
- Le second est le nom "age" et la valeur 23.
