# Comprendre le fonctionnement des actions par défaut du navigateur

## De nombreux événements entraînent automatiquement des actions par défaut du navigateur

*   Le clic gauche de la souris (`down`) => **lance la sélection (déplacez la souris pour sélectionner)**.
*   Le clic droit (`contextmenu`) => **l'action consiste à afficher le menu contextuel du navigateur**.
*   Le clic dans un `checkbox` => **coche / décoche l'`input`**.
*   Un `submit` ou touche `Entrée` => **dans un champ de formulaire pour que cet événement se fasse et que le navigateur envoie le formulaire après le clic**.
* Une pression d'une touche du clavier => **conduit à ajouter un caractère dans un champ ou à d'autres actions spécifique en fonction d'où l'on se trouve**.
* Et beaucoup d'autres ...

## Savoir comment empêcher le comportement par défaut

Toutes les actions par défaut peuvent être empêchées si on vas gérer l'événement exclusif avec JavaScript.

Pour empêcher une action par défaut, 2 choix possibles :

1.  **Le moyen principal consiste à utiliser l'objet `event`. Il utilise la méthode : `event.preventDefault()`**.
2.  **Sinon si le gestionnaire est affecté à l'aide de `on<event>` (pas par `addEventListener`), on peut également renvoyer `false` à partir de celui-ci**.

L'option `passive: true` de `addEventListener` indique au navigateur que l'action ne va pas être empêchée. Cela est utile pour certains événements mobiles, tel que `touchstart` et `touchmove`, pour indiquer au navigateur qu'il ne doit pas attendre que tous les gestionnaires aient fini avant de faire défiler.

Si l'action par défaut a été empêchée, la valeur de `event.defaultPrevented` devient `true`, sinon `false`.
