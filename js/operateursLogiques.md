# Opérateurs Logiques :

3 opérateurs logiques en JavaScript : `||` (OR), `&&` (AND) et `!` (NOT).

Bien qu'ils sont appellés "logiques", ils peuvent être appliqués à n'importe quel type de valeurs, pas que booléen. Le résultat peut être de n'importe quel type.

`||` (OR) :

Dans le programming classique, le logique `OR` est censé manipuler les valeurs booléennes uniquement. Si un des arguments est `true`, il retourne `true`, sinon il retourne `false`.

En Javascript, l'opérateur est un petit peu délicat et plus puissant. On vas voir ce qu'il se passe avec les valeurs booléens.

4 combinaisons logiques possibles :

```
true || true => true
false || true => true
true || false => true
false || false => false
```

Comme on peut le voir, le résultat est toujours `true` sauf si les opérands sont `false`.
