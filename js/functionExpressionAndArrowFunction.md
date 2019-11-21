# `Function Expression` et `Arrow Function` :

## `Function Expression` :

Principales différences entre déclaration et expression :

- La syntaxe.
- `Function Declaration` : une fonction, déclarée comme une instruction séparée, dans le flux de code principal.

Syntaxe :

```
function sum(a, b) {
    return a+b;
}
```

- `Function Expression` : une fonction, créer dans une expression ou dans une autre construction de syntaxe. Ici, la fonction est créer à droite de l'expression "assignement =".

Syntaxe :

```
let sum = function(a, b) {
    return a+b;
};
```
