# `let` vs `var` :

`let` et `const` se comporte de la même manière en terme d'environnements lexicaux.

## `var` n'as pas de portée de bloc :

Les variables , qui sont déclarées avec `var`, sont à l'échelle de la fonction ou globales. Elles sont visibles partout où l'on se trouve.

Exemple :

```
if (true) {
  var test = true;
}

alert(test); // true, car la variable vie après le if (comme on utilise `var`)
```

Alors que `let` est visible qu'à l'intérieur du if.

```
if (true) {
  let test = true;
}

alert(test); // Erreur: test n'est pas définie.
```

La même chose pour les boucles , si on utilise `var` il nous renverra que la dernière valeur d'une boucle car c'est au niveau global.

Exemple:

```
for (var i = 0; i < 10; i++) {
  // ...
}

alert(i); // 10, "i" est visible après la boucle, car c'est une variable globale.
```

Si un bloc de code est à l'intérieur d'une fonction, `var` devient alors une variable au niveau de la fonction :

```
function sayHi() {
  if (true) {
    var phrase = "Hello";
  }

  alert(phrase); // Hello , ici ça fonctionne
}

sayHi();
alert(phrase); // Erreur: phrase n'est pas définie
```

## Les déclarations `var` sont traitées au début de la fonction :

Les déclarations `var` sont traitées quand la fonction démarre ( ou du script pour le global)

**Les déclarations sont levées (hoisting), mais les assignements ne le sont pas.**

Exemple :

```
function sayHi() {
  alert(phrase);

  var phrase = "Hello";
}

sayHi();    // undefined
```

La ligne `var phrase = "Hello"` contient deux actions :

1. Déclaration de variable `var`.
2. Affectation de variable `=`.

C'est pourquoi l'affectation doit **TOUJOURS** être mis en premier.
