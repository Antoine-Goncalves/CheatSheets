# `Function Expression` et `Arrow Function`

## `Function Expression`

Principales différences entre déclaration et expression :

- La syntaxe.
- `Function Declaration` : une fonction, déclarée comme une instruction séparée, dans le flux de code principal.

Syntaxe :

```javascript
function sum(a, b) {
  return a + b;
}
```

- `Function Expression` : une fonction, créer dans une expression ou dans une autre construction de syntaxe. Ici, la fonction est créer à droite de l'expression "assignement =".

Syntaxe :

```javascript
let sum = function(a, b) {
  return a + b;
};
```

Une `Function EXpression` est créer lorsque l'exécution lui parvient et n'est utilisaable qu'à partir de ce moment.

Une déclaration de fonction peut être appeléer plus tôt que sa définition. En mode strict, quand une déclaration de fonction se trouve dans un bloc de code, elle est visible partout dans ce bloc. Mais pas en dehors de ça.

## `Arrow Function`

Il existe une autre syntaxe très simple et concise pour la création de fonction, souvent meilleur que `Function Expression`.

Syntaxe:

```javascript
let func = (arg1, arg2, ..., argN) => expression
```

Même chose que la fonction expression mais plus concis.

```javascript
let sum = (a, b) => a + b;
```

_Note: Si on as qu'un argument, on est pas obligé de mettre les ()_
