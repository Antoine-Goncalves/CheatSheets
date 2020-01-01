# Opérateurs conditionnels : `if` et `?`

# L'opérateur `if`

Le if(..) évalue une condition entre parenthèse et, si le résultat est `true`, il exécute un bloc de code.

Exemple :

```
let year = prompt('Quelle année somme-nous?','');
if (year==2019) alert('Exact!');
```

Si on veut exécuter plus d'une déclarations, on doit englober notre code dans {..}.

Il est recommandé, pour la visibilité, d'écrire entre {..} si on utilise l'opérateur `if`.

## Conversion Booléenne

L'opérateur `if {..}` évalue l'expression entre parenthèses et convertie le résultat en booléen.

-   _Le nombre 0, chaîne vide "", `null`, `undefined` and `NaN` deviennent `false`. Car ils sont appellées les valeurs fausses._
-   _Toutes les autres valeurs deviennent `true`, et sont appelées les vrais_

## La clause `else`

L'opérateur `if` peut contenir des blocks `else` optionnel. Il s'éxecute si la condition est `false`.

Exemple :

```
let year = prompt('Quelle année somme-nous ?', '');

if (year == 2019) {
  alert( 'Exact!' );
} else {
  alert( 'Non, non ! Désolé' ); // toute autre valeur que 2019
}
```

## PLusieurs conditions : `else if`

Des fois, on veut utiliser plusieurs variante de condition. La clause `else if` est là pour ça.

Exemple :

```
let age = prompt('Âge de majorité ?', '');

if (age < 18) {
  alert( 'Trop jeune !' );
} else if (age > 18) {
  alert( 'Majeur oui, mais pas l'âge de majorité' );
} else {
  alert( 'OUI! On est enfin libre !' );
}
```

## L'opérateur conditionnel `?`

Parfois, on doit assigner une variable en fonction d'une condition. Avec l'opérateur `?`, il permet de faire ceci plus simplement et plus rapide. Il est appelé, parfois, `ternary` (ternaire), car l'opérateur a 3 opérandes. **C'est actuellement le premier et le seul qui en possède autant**.

La syntaxe est :

```
let result = condition ? resp1 : resp2;
```

La condition est évaluée, si c'est truthy, alors on retourne resp1, resp2 sinon.

## `?` multiple

Une séquence de `?` peut retourner une valeur qui dépend de plusieurs conditions.

Exemple :

```
let age = prompt('age?', 18);

let message = (age < 3) ? 'Coucou, bébé!' :
  (age < 18) ? 'Salut l'ado!' :
  (age < 100) ? 'Bonjour à vous!' :
  'Félicitations d'être toujours parmi nous!';

alert( message );
```

Le but de l'opérateur `?` est de retourner une valeur ou une autre en fonction de la condition. Il faut l'utiliser comme ça ! On utilise `if` quand on exécute différents branches de code.
