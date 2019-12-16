# Objet en JS : `Object`

Pour rappel, il y a **7 types de données en JS**. 6 sont appellés _primitives_, car leurs valeurs contiennent seulement une seule chose. (cela peut être une chaîne de caractère, ou un nombre). Au contraire, **les objets sont utilisés pour stockés des collections de différentes données et des entités plus complexe**. En JS, les objets pénetrent presque tout les aspect du langage.

Un objet peut être **créer avec les acolades {...}** avec une liste optionnel de propriétés, **une propriété** est une **paire "clé: valeur"**, où _"clé" est une chaine de caractère (appellé aussi nom de propriété)_, et _"valeur" peut être n'importe quoi_. On peut imaginer un objet dans un tiroir avec plusieurs dossiers. Chaque morceau de données est stocké dans son fichier par une définition.

**Un objet vide** : _("tiroir vide")_

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

Le résultat de l'objet user peut-être imager par deux fichiers nommées "name" et "age".

_On peut ajouter, retirer et lire les fichiers quand on veut._

Les propriétés de valeurs sont accessible en utilisant la notation `.`.

```
// obtenir les valeurs d'un objet

alert(user.name);   // Antoine
alert(user.age);    // 23
```

La valeur peut-être de n'importe quel type. On peut ajouter un booléen.

```
user.isAdmin = true;
```

On peut utiliser des propriétés de noms multiples, mais ils ne doivent pas être entre `""`.

Exemple:

```
let user = {
    name: "Antoine",
    age: 23,
    "aime le foot": true    // MOTS MULTIPLES ENTRE "", ❗️ ❗️
};
```

La dernière propriété dans la liste peut finir avec une virgule, c'est appeler une **virgule "trainante" ou "suspendu"**. Cela rend plus facile pour ajouter/retirer/bouger autour des propriétés, car toutes les lignes se ressemblent.

**Les crochets** :

Pour les mots multiples, l'accès avec le `.` ne fonctionne pas.

```
user.aime le foot = true;   //syntaxe d'erreur
```

Car le `.` veut que la clé soit un identificateur de variable valide. _Pas d'espaces et autres limitations._ Les crochets sont la pour travailler avec les chaines.

Exemple:

```
let user = {};

// initialisation

user["aime le foot"] = true;

// récupère

alert(user["aime le foot"]);    // true

// supprime

delete user["aime le foot"];
```

Les crochets permet d'obtenir le nom de propriété à la suite de toute expression (contraireme,t à la chaîne litérale) comme les variables qui suit :

```
let key = "aime le foot";

// pareil que user["aime le foot"] = true;
user [key] = true;
```

Ici, la variable `key` peut être calculé en exécution ou dépendre de ce que l'utilisateur écrit. Grâce à ça, il permet d'accéder à la propriété. Cela donne beaucoup de flexibilité.

_Note: La notation `.` ne peut pas être utilisé dans ce cas._

Propriété ajoutée :

On peut utiliser les [] dans un objet literal. Ils sont appellés **propriété ajoutée**.

Exemple :

```
# 1

let key = prompt("À propos de l'utilisateur ?", "nom");

// accèder à la variable

alert(user[key]);   // Antoine (supposant qu'utilisateur entre comme nom Antoine).

# 2

let fruit = prompt("Quel fruit veux-tu acheter ?", "pomme");

let bag = {
    [fruit]: 5, // nom de la propriété est pris avec la variable fruit.
};

alert(bag.pomme);   // 5 (si fruit = "pomme")
```
