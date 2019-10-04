# Les évènements basés sur la souris :

## Types d'événements de souris :

2 Catégories :

1. Simple
2. Complexe

### Simple :

* `mousedown` ou `mouseup` => **Le bouton de la souris est cliqué/relâché sur un élément**.
* `mouseover` ou `mouseout` => **Le pointeur de la souris sur/hors d'un élément**.
* `mousemove` => **Chaque souris survolant un élément déclenche cet événement**.

### Complexe :

* `click` => **Déclenche après `mousedown`, puis `mouseup` sur le même élément si le bouton gauche de la souris a été utilisé**.
* `contextmenu` => **Déclenche après `mousedown` si le bouton droite de la souris a été utilisé**.
* `dblclick` => **Déclenche après un double clic sur un élément**.

## Ordre d'événements :

Une action peut déclencher plusieurs événements. Il y a donc un ordre à respecter.
Exemple: `mousedown` => `mouseup` => `click`.

## Obtenir le bouton => `which` :

Les événements liés aux clics ont toujours une propriété `which`, qui permet de déterminer le bouton exact de la souris.

*Note: Pas utilisé pour les événements `click` et `contextmenu`, car le premier spécifique au clic gauche et le second au clic droit.*

3 valeurs possibles :
* `event.which == 1` => **Le bouton de gauche**.
* `event.which == 2` => **Le bouton du milieu**.
* `event.which == 3` => **Le bouton de droite**.

## Modificateurs => `shift`, `alt`, `ctrl` et `meta` :

Propriétés de l'événement :
* `shiftKey` => **`Shift`**.
* `altKey` => **`Alt` (`Opt` pour Mac)**.
* `ctrlKey` => **`Ctrl`**.
* `metaKey` => **`Cmd` pour Mac**.

Ils sont `true` si ils correspondent à la touche enfoncée pendant l'événement.

## Coordonnées => `clientX` et `clientY` / `pageX` et `pageY` :

2 types de coordonnées :

1. **Relatives à la fenêtre => `clientX` et `clientY`**.
2. **Relatives au document => `pageX` et `pageY`**.

## Désactiver la sélection :

L'action par défaut du navifateur `mousedown` , si on double clic, est la séléction du texte. On peut alors l'empêcher.

Pour l'empêcher, on utilise `onmousedown="return false"`.
