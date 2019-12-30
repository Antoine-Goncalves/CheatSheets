# Conversion de types en JS

La plupart du temps, les opérateurs et les fonctions convertise automatiquement les valeurs qu'on leurs donnent dans le bon type. Il y a des cas où on doit convertir nous-même une valeur en type que l'on veut.

## `ToString` => `String(valeur)`

La conversion en chaîne intervient quand on as besoin qu'une valeur est une forme de chaîne.

## `ToNumber` => `Number(valeur)`

La conversion en nombre intervient dans les fonctions mathématiques et les expressions automatique. Si la chaîne n'est pas un nombre valide, le résultat sera forcément NaN.

Règle des conversions numériques :
- **`undefined` devient `NaN`**.
- **`null` devient `0`**.
- **`true` et `false` devient `1` et `0`**.

## `ToBoolean` => `Boolean`

Les conversions booléennes sont les plus simple. Ça s'applique dans les opérations logiciels, mais aussi avec Boolean(valeur).

La règle de conversion :
- Si la valeur vide comme `0`, `chaine vide`, `undefined`, `NaN` deviennent `false`.
- Tout le reste est `true`.
