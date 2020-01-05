# L'objet Function, EFN

Pour JS , les fonctions sont des objets.

Un bon moyen d’imaginer des fonctions est en tant que des “objets d’action” qu’on peut appeler. On peut non seulement les appeler, mais aussi les traiter comme des objets: ajouter/supprimer des propriétés, passer par référence, etc.

## La propriété `name`

Les objets fonction contiennent quelques propriétés utilisables.

Par exemple, le nom d'une fonction est accessible en tant que propriété `name` :

```javascript
function sayHi () {
    alert( "Hi" );
}
alert(sayHi.name);  // sayHi
```

## La propriété `length`

Il existe une autre propriété native, `length`, qui renvoie le nombre de paramètres de la fonction.

Par exemple :

```javascript
function test(a,b,c) {
    // code
}

alert(test.length); // 3
```

Les rest parameters ne sont pas pris en compte pour la propriété `length`.

La propriété `length` est parfois utilisée pour la réfléxion dans des fonctions qui opèrent sur d'autres fonctions.

Une fois qu'un utilisateur a fourni sa réponse, la fonction appelle les gestionnaires. On peut transmettre deux types de gestionnaires:

-   **Une fonction sans argument, qui n'est appelée que lorsque l'utilisateur donne une réponse positive.**
-   **Une fonction avec des arguments, appelée dans les deux cas et renvoyant une réponse.**

## Propriété personnalisées

On peut ajouter nos propres propriétés.

On ajoute ici la propriété `counter` pour suivre le nombre total d'appels :

```javascript
function sayHi() {
  alert("Hi");

  // comptons combien de fois nous executons
  sayHi.counter++;
}
sayHi.counter = 0; // valeur initiale

sayHi(); // Hi
sayHi(); // Hi

alert( `Called ${sayHi.counter} times` ); // Appelée 2 fois
```

## Expression de fonction nommée

Expression de fonction nommée, ou EFN, est un terme pour les expressions de fonction qui ont un nom.

```javascript
let sayHi = function(who) {
  alert(`Hello, ${who}`);
};
```

Et on ajoute un nom à cela :

```javascript
let sayHi = function func(who) {
  alert(`Hello, ${who}`);
};
```

La fonction est toujours disponible sous la forme `sayHi()`. Il y a deux particularités à propos du nom de la fonctione (ici `func`) :

1.  **Il permet à la fonction de se référencer en interne.**
2.  **Il n'est pas visible en dehors de la fonction**

Nommer une fonction est hyper important car son nom (ici `func`) est local à la fonction. Il n'est pas pris de l'extérieur (et non visible là-bas). La spécification garantit qu'elle fera toujours référence à la fonction actuelle.

Le code externe a toujours sa variable `sayHi` ou autre.. Tandis que `func` est un "nom de fonction interne", c'est comment la fonction peut s'appeler en interne.

_Note : La fonctionnalité “nom interne” décrite ici n’est disponible que pour les expressions de fonction, pas pour les déclarations de fonction. Pour les déclarations de fonctions, il n’y a aucune possibilité de syntaxe d’ajouter un nom “interne” supplémentaire._
