# Opérateurs Logiques

3 opérateurs logiques en JavaScript : `||` (OR), `&&` (AND) et `!` (NOT).

Bien qu'ils sont appellés "logiques", ils peuvent être appliqués à n'importe quel type de valeurs, pas que booléen. Le résultat peut être de n'importe quel type.

## `||` (OR)

Dans le programming classique, le logique `OR` est censé manipuler les valeurs booléennes uniquement. Si un des arguments est `true`, il retourne `true`, sinon il retourne `false`.

En Javascript, l'opérateur est un petit peu délicat et plus puissant. On vas voir ce qu'il se passe avec les valeurs booléens.

4 combinaisons logiques :

```
true || true => true
false || true => true
true || false => true
false || false => false
```

Comme on peut le voir, le résultat est toujours `true` sauf si les opérands sont `false`.

Si un operand n'est pas un booléen, il le convertie en tant que tel.

La plupart du temps, OR est utilisé dans une déclaration `if` pour tester si l'une des conditions données est `true`.

**OR trouve la première valeur VRAI.**

L'opérateur OR fait les choses suivantes :

- Évalue les operands de gauche à droite.
- Pour chaque operands, il le converti en booléen. Si le résultat est `true`, on stop et on retourne la valeur originale de l'operand.
- Si tout les operands ont été évaluée (c'est-à-dire tous `false`), il retourne le dernier operand.

En d'autre terme, une chaîne de OR retourne la première valeur vrai ou la dernière si aucune valeur vrai est trouvée.

## `&&` AND

Dans le programming classique, AND retourne `true` si tout les opérands sont vrai, et `false` sinon.

4 combinaisons logiques :

```
true && true => true
false && true => false
true && false => false
false && false => false
```

Comme avec OR, toute valeur est autorisé. AND trouve la première valeur fausse.

_Note: :heavy_exclamation_mark: Précédence AND est plus haute que OR. :heavy_exclamation_mark:_

## `!` NOT

L'opérateur accepte un argument simple et fait ce qui suit :

- Convertit l'operand en booléen : `true`/`false`.
- Retourne la valeur inverse.

Le double NOT `!!` est parfois utilisé pour convertir une valeur en booléen. (ce qui vient à faire `Boolean(valeur)`).

_Note: :heavy_exclamation_mark: Précédence NOT est plus haute que tout opérateurs logiques. (donc exécuter avant AND ou OR) :heavy_exclamation_mark:_
