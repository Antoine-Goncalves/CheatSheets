# Comparaison en JS

**Le résulat d'une comparaison est un booléeen**. (True ou False)

Pour voir comment une chaîne de caractère est plus grande qu'une autre, JS utilise ce qu'on appelle l'ordre "dictionnaire" ou "lexicographique". Les chaînes de caractères sont comparés lettre par lettre.

L'algoritme pour comparé 2 string est simple :

1.  **On compare le 1er caractère des deux string.**
2.  **Si le 1er caractère du 1er string est plus grand (ou petit) que l'autre string, alors le 1er string est plus grand (ou petit) que le second.** C'est fini
3.  **Sinon, si le 1er caractère des strings est le même, on compare le second caractère de la même façon.**
4.  **On repète jusqu'à la fin du string.**
5.  **Si les chaînes sont de même longueur, alors ils sont égaux. Sinon, le string le plus long est plus grand.**

_Note: L'ordre Unicode fait que les minuscules sont supérieur au majuscule._

## Comparaison de différents types

Quand on compare différents types, JS les convertie en nombre.

Pour booléen, True devient et False devient.

## Égalité stricte

l'égalité (`==`) as un problème. Il ne différencie pas 0 de false.

```javascript
alert(0 == false); // true
```

Cela s'applique car les operands de différents type sont convertis en nombre avec l'opérateur `==`. Une chaîne vide, comme false, devient 0.

L'opérateur égalité stricte (`===`) vérifie les égalités sous les types de conversion.

Si a et b sont de types différents, alors `a===b` retourne false.

Il existe aussi l'opérateur "non-égal strict" `!==`. L'opérateur égalité stricte est plus long à écrire, mais rend évident le résultat et laisse moins d'erreur.

## Comparaison entre `null` et `undefined`

Avec l'égalité strict `===` : False.

Ce ne sont pas du même type du coup les valeurs sont différentes.

Avec l'égalité non strict `==` : True.

Il ya une règle spéciale pour ceci, c'est un "couple doux" : ils sont égaux, mais non pas les mêmes valeurs.

`null` et `undefined` sont convertis en nombre : `null` devient 0, alors que `undefined` devient NaN.

Résultat étrange : `null` vs 0

La comparaison convertie `null` en nombre, ici 0. D'autres part, l'égalité `==` pour `undefined` et `null` sont définies, sans aucune conversions, ils s'égalent et n'égale rien d'autres.

`undefined` est incomparable :

elle ne peut pas être comparé à une autre valeur.
