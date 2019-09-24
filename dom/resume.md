# Dom :

## Action par défaut du navigateur : 

[:question: :question:](dom/actionParDefautNavigateur.md)

* Le clic gauche (down) => **lance la sélection (déplacez la souris pour sélectionner)**.
* Le clic droit (`contextmenu`) => **l'action consiste à afficher le menu contextuel du navigateur**.
* Le clic dans un `checkbox` => **coche / décoche l'`input`**.
* Un `submit` ou touche `Entrée` => **dans un champ de formulaire pour que cet événement se fasse et que le navigateur envoie le formulaire après le clic**.
* Une pression d'une touche du clavier => **conduit à ajouter un caractère dans un champ ou à d'autres actions spécifique en fonction d'où l'on se trouve**.
* Et beaucoup d'autres ...

Pour empêcher une action par défaut, 2 choix possibles :

1. **`event.preventDefault()`**.
2. **`on<event>`, en retournant `false`**.

L'option `passive: true` de `addEventListener` indique au navigateur que l'action ne va pas être empêchée.

Si l'action par défaut a été empêchée, la valeur de `event.defaultPrevented` devient `true`, sinon `false`.

## Événement basique de la souris :

[:question: :question:](dom/evenementBasiqueSouris.md)

Les événements de souris ont les propriétés suivantes:

* Bouton => `which` .
* Touches de modification ( `true` si enfoncées) => `altKey` , `ctrlKey` , `shiftKey` et `metaKey` (Mac).
* Préférable de vérifier `if (e.metaKey || e.ctrlKey)`.
* Coordonnées relatives à la fenêtre => `clientX/clientY` .
* Coordonnées relatives au document => `pageX/pageY` . 

L'action par défaut du navigateur mousedown est la sélection de texte. Si ce n'est pas bon pour l'interface, alors il faut l'empêcher.

## Déplacements de la souris :

[:question: :question:](dom/deplacementSouris.md)

Nous avons couvert les événements `mouseover` , `mouseout` , `mousemove` , `mouseenter` et `mouseleave`.

Bon à savoir :

* Un mouvement rapide de la souris peut ignorer les éléments intermédiaires.
* Les événements `mouseover`/`out` et `mouseenter`/`leave` ont une propriété supplémentaire: `relatedTarget` . C'est l'élément complémentaire à `target` . 

Les événements `mouseover`/`out` déclenchent même lorsque nous passons de l'élément parent à un élément enfant. Le navigateur suppose que la souris ne peut survoler qu'un seul élément à la fois.

Les événements `mouseenter`/`leave` sont différents comparé à `mouseenter`/`leave` : ils ne se déclenchent que lorsque la souris entre et sort de l'élément dans son ensemble. En outre, ils ne font pas `bubble`.
