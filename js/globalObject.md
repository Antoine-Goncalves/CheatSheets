# Objet Global :

L’objet global fournit des variables et des fonctions qui sont disponibles partout. Par défaut, celles qui sont intégrées au langage ou à l’environnement.

Dans un navigateur, c’est appelé `window`, pour `Node.js` c’est global, et pour les autres environnements, il peut porter un autre nom.

`globalThis` a été ajouté au langage comme un nom standardisé pour l'objet global et devrait être supporté à travers tous les environnements.

Il est préférable d'utiliser `globalThis`.

Toutes les propriétés de l'objet global sont directement accessibles :

Exemple :

```javascript
alert("Hello");
// la même chose que
globalThis(ou window).alert("Hello");
```

Dans un navigateur, les fonctions globales et les variables déclarées avec `var` (pas `let`/`const`!) deviennent la propriété de l’objet global :

Exemple :

```javascript
var gVar = 5;

alert(globalThis(ou window).gVar); // 5 (`var` est devenue une propriété de l'objet global)
```

On utilise l'objet global pour tester le support des fonctionnalités du langage moderne. On peut tester si l'objet natif `Promise` existe (il n'existe pas dans les navigateurs très anciens).

On peut créer des "polyfills". Les "polyfills" ajoutent des fonctions qui ne sont pas supportés par l'environnement, mais qui existent dans le standard moderne.
