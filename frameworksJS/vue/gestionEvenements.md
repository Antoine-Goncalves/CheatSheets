# Gestion des évènements

On peut utiliser l'instruction `v-on` pour écouter les évènements du DOM afin d'exécuter du JS lorsque ces évènements surviennent.
Par exemple :

```javascript
<div id="example-1">
  <button v-on:click="counter += 1">Add 1</button>
  <p>Le bouton ci-dessus a été cliqué {{ counter }} fois.</p>
</div>

var example1 = new Vue({
  el: '#example-1',
  data: {
    counter: 0
  }
})
```

La logique avec beaucoup de gestionnaires d’évènements sera très certainement plus complexe, par conséquent, garder notre JS dans la valeur de l’attribut `v-on` ne sera tout simplement pas faisable. C’est pourquoi `v-on` peut aussi accepter le nom d’une méthode qu'on veut appeler.

Au lieu de lier directement la méthode par son nom dans l'attribut, on peut également utiliser des méthodes dans une instruction JS.

Parfois on as besoin d'accéder à l'évènement original du DOM depuis l'instruction dans l'attribut. On peut passer à une méthode en utilisant la variable spéciale `$event` :

```javascript
<button v-on:click="warn('Le formulaire ne peut être soumis pour le moment.', $event)">
  Soumettre
</button>

// ...
methods: {
  warn: function (message, event) {
    // maintenant nous avons accès à l'évènement natif
    if (event) event.preventDefault()
    alert(message)
  }
}
```

C'est un besoin courant que de faire appel à `event.preventDefault()` ou `event.stopPropagation()` à l'intérieur d'une déclaration de gestionnaire d'évènements. Bien qu'on peut réaliser ceci facilement à l'intérieur des méthodes, il serait préférable que les méthodes restent purement dédiées à la logique des données au lieu d'avoir à gérer les détails des évènements du DOM.

Pour résoudre ce problème, Vue propose des modificateurs d'évènements pour `v-on`.

*   `.stop`
*   `.prevent`
*   `.capture`
*   `.self`
*   `.once`
*   `.passive`

Lorsqu'on écoute les évènements du clavier, on as régulièrement besoin de nous assurer du code des touches. Vue permet également d'ajouter un modificateur de touches pour `v-on`. On peut utiliser n'importe quel nom de touche clavier valide fourni par `KeyboardEvent.key` en tant que modificateur en les écrivant au format kebab-case.

On peut utiliser des attributs `keyCode` est également possible. Vue fournit des alias pour la plupart des clés communes utilisés quand necessaire pour le support des anciens navigateurs :

*   `.enter`
*   `.tab`
*   `.delete` (fonctionne pour les touches "suppression" et "retour arrière")
*   `.esc`
*   `.space`
*   `.up`
*   `.down`
*   `.left`
*   `.right`

On peut utiliser les modificateurs suivants pour déclencher un évènement du clavier ou de la souris seulement lorsque la touche du modificateur correspondante est pressée :

*   `.ctrl`
*   `.alt`
*   `.shift`
*   `.meta`

Le modificateur `.exact` permet le contrôle de la combinaison de touches système exacte requise pour déclencher le gestionnaire d'évènements.

*   `.left`
*   `.right`
*   `.middle`

Ces modificateurs n'autorisent la gestion de l'évènement que s'il a été déclenché par un bouton spécifique de la souris.

Avantage à utiliser `v-on` :

1.  Il est plus facile de localiser l’implémentation des fonctions gestionnaires dans le code JS en survolant le code HTML.
2.  Comme on as pas à attacher manuellement les écouteurs dans notre JS, le code du "ViewModel" peut être purement logique et sans DOM. Ceci le rend plus facile à tester.
3.  Quand un "ViewModel" est détruit, tous les écouteurs d’évènements sont automatiquement retirés. On as pas à se soucier de le faire soit-même.
