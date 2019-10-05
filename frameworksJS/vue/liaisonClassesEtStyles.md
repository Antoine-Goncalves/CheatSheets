# Liaisons de classes et de styles :

Ce sont tous deux des attributs, il est possible d'utiliser `v-bind` pour les gérer. Vue fournit des améliorations spécifiques quand `v-bind` est utilisé avec `class` et `style`. En plus des chaines de caractères, l'expression peut évaluer des objets ou alors des tableaux.

## Classes HTML :

Il est possible de passer un objet à `v-bind:class` pour permuter les classes automatiquement :

`<div v-bind:class="{ active: isActive }"></div>`

*La syntaxe signifique que la classe `active` sera présente si la propriété `isActive` est considérée comme vraie*.

On peut permuter plusieurs classes en ayant plus de champs dans l'objet. La directive `v-bind:class` peut aussi coexister avec l'attribut `class`. L'objet lié n'a pas besoin d'être déclaré dans l'attribut, on obtient le même résultat. Il est également possible de lier une **propriété calculée** qui retourne un objet. C'est une méthode courante et puissante :

```
<div v-bind:class="classObject"></div>

data: {
  isActive: true,
  error: null
},
computed: {
  classObject: function () {
    return {
      active: this.isActive && !this.error,
      'text-danger': this.error && this.error.type === 'fatal'
    }
  }
}
```

Il est possible de passer un tableau à `v-bind:class` pour appliquer une liste de classes.

```
<div v-bind:class="[activeClass, errorClass]"></div>

data: {
  activeClass: 'active',
  errorClass: 'text-danger'
}
```

Quand on utilise l’attribut `class` sur un composant personnalisé, ces classes seront ajoutées à l’élément à la racine du composant. Les classes présentes sur cet élément ne seront pas réécrites.

## Styles HTML :

La syntaxe objet pour `v-bind:style` est assez simple (presque comme du CSS), sauf que c’est un objet JavaScript. On peut utiliser camelCase ou kebab-case (camelCase meilleur) pour les noms des propriétés CSS :

```
<div v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }"></div>

data: {
  activeColor: 'red',
  fontSize: 30
}
```

On peut lier directement un objet de style, pour que le template soit plus propre. Encore une fois, la syntaxe objet est souvent utilisée en conjonction avec des propriétés calculées retournant des objes.

La syntaxe tableau pour `v-bind:style` permet d'appliquer plusieurs objets de style à un même élément.

Quand on utilise une propriété CSS qui nécessite un **préfixe vendeur** dans `v-bind:style`, par exemple `transform`, Vue le détectera automatiquement, et ajoutera les préfixes appropriés aux styles appliqués.

On peut maintenant fournir de multiples valeurs de préfixes à une propriété style, par exemple :

```
<div v-bind:style="{ display: ['-webkit-box', '-ms-flexbox', 'flex'] }"></div>
```

Cela rend uniquement la dernière valeur dans le tableau supportée par le navigateur. Dans cet exemple, cela rend `display: flex` pour les navigateurs qui supportent la version sans préfixe de flexbox.
