# Déplacements de la souris

## Événements `mouseover` / `mouseout`, `relatedTarget`

*   `mouseover` => **L'événement se produit lorsqu'un pointeur de la souris survole un élément**.
*   `mouseout` => **L'événement se produit lorsqu'un pointeur de la souris quitte un élément**.

Ces événements sont spéciaux, car ils ont une propriété `relatedTarget`. Cette propriété complète la `target`. Quand une souris laisse un élément pour un autre, l'un d'eux devient la `target` et l'autre `relatedTarget`.

Pour `mouseover` :

*   `event.target` => **L'élément où la souris est passée**.
*   `event.relatedTarget` => **L'élément d'origine de la souris (`relatedTarget` -> `target`)**.

Pour `mouseout` c'est l'inverse :

*   `event.target` => **L'élément que la souris a laissé**.
*   `event.relatedTarget` => **Le nouvel élément situé sous le pointeur, que la souris a laissé pour (`target` -> `relatedTarget`)**.

## Sauter des éléments

L'événement `mousemove` est déclenché lorsque la souris se déplace. Tout n'est pas vérifié, si on déplace la souris très rapidement, certains éléments DOM peuvent être ignorés.

Si `mouseover` déclenché, il doit y avoir `mouseout`.

## `mouseout` en partant pour un enfant

Une caractéristique importante de `mouseout` : elle se déclenche lorsque le pointeur passe d'un élément à son descendant.

**Selon la logique du navigateur, le curseur de la souris peut ne survoler qu'un seul élément à tout moment - l'élément le plus imbriqué et le plus élevé par z-index**.

Lorsqu'on passe d'un élément parent à enfant, deux gestionnaires se déclenchent sur l'élément parent: `mouseout` et `mouseover`.

## Événements `mouseenter` et `mouseleave`

Les événements `mouseenter/mouseleave` sont comme `mouseover/mouseout`. Ils se déclenchent lorsque le pointeur de la souris entre/sort de l'élément.

2 grosses différences :

1. **Les transitions à l'intérieur de l'élément, vers/depuis les descendants, ne sont pas comptées**.
2. **Les événements `mouseenter/mouseleave` ne font pas de `bubble`**.

## Délégation d'événement

Si on doit utiliser la délégation d'événement, il faut utiliser `mouseover/mouseout` car `mouseenter/mouseleave` ne font pas de `bubble`.
