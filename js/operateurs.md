# Opérateurs :

## Fonctionnement des opérateurs :

On connaît beaucoup d'opérateurs grâce à l'école (addition `+`, multiplication `*`, soustraction `-`, et plein d'autres).

**Différence entre `unary`,`binary` et `operand`**.

- **Un operand est ce à quoi les opérateurs sont appliqués**.

Exemple:

Dans une multiplication (`5*2`) il y a 2 operand.

- **Un opérateur est unaire si il a un operand seule**.

- **Un opérateur est binaire si il a 2 operand**.

## Concatenation :

Concatenation des chaînes, binary+.

Le binary+ s'appelle au chaîne, il faut concatener 2 chaînes.

*Note: Si un operand est une chaîne, l'autre est convertie en chaîne également.*

La concatenation et conversion des chaînes est spéciale à binary+.
Les autres opérateurs travaillent qu'avec des nombres et convertie toujours en nombres leurs operand.

conversion numérique, unary+.

Le + existe en 2 formes : le binary+ et unary+.

Le unary+ applique simplement une valeur à quelque chose (inutile pour les nombres). Mais pour les operand qui ne sont pas des nombres, il les convertie en nombre (même fonctionnement que Number(..) mais plus court).

**Les unary+ s'applique entre premier, il convertisse les chaînes en nombres, et les binary+ font le reste.**

## Opérateurs de précédence :

Si une expression a plus d'un operateur, la précédence est obligatoire.

Les parenthèses dominent tout.

## Incrémentation/Décrémentation :

Il y a des opérateurs spéciaux :

- incrémentation `++` incrémente une variable de 1.
- décrémentation `--` décrémente une variable de 1.

Les opérateurs `++` et `--` peuvent être placés avant ou après une variable :

- si avant, on parle de la forme préfix.
- si après, on parle de la forme postfix.

*Note: La forme préfix retourne la nouvelle valeur tandis que la forme postfix retourne l'ancienne valeur.*

## Bitwise operateurs :

la liste des opérateurs :

- AND (`&`)
- OR (`|`)
- XOR (`^`)
- NOT (`~`)
- LEFT SHIFT (`<<`)
- RIGHT SHIFT (`>>`)
- ZERO-FILL RIGHT SHIFT (`>>>`)

## Modify-in-place :

On peut modifier sur place une variable en lui appliquant un opérateur. On peut raccourcir avec les opérateurs `+=` et `*=`.

Ils ont la même précédence qu'un assignement normal.

## Comma (`,`) :

Opérateur le plus faible, sert à séparer des expressions.
