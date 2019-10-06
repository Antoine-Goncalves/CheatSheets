# Rendu de liste :

## Associer un tableau à des éléments avec `v-for` :

On peut utiliser la directive `v-for` pour faire le rendu d'une liste d'éléments en se basant sur un tableau. La directive `v-for` utilise une syntaxe spécifique de la forme `item in items`, où `items` représente le tableau source des données et où `item` est un `alias` représentant l'élément du tableau en cours d'itération :

```
<ul id="example-1">
  <li v-for="item in items">
    {{ item.message }}
  </li>
</ul>

var example1 = new Vue({
  el: '#example-1',
  data: {
    items: [
      { message: 'Foo' },
      { message: 'Bar' }
    ]
  }
})
```

À l'intérieur des structures `v-for`, on as un accès complet aux propriétés de la portée parente. `v-for` supporte également un second argument optionnel représentant l'index de l'élément courant.

```
<ul id="example-2">
  <li v-for="(item, index) in items">
    {{ parentMessage }} - {{ index }} - {{ item.message }}
  </li>
</ul>

var example2 = new Vue({
  el: '#example-2',
  data: {
    parentMessage: 'Parent',
    items: [
      { message: 'Foo' },
      { message: 'Bar' }
    ]
  }
})
```

On peut aussi utiliser `of` en mot-clé à la place de `in` :

```
<div v-for="item of items"></div>
```

## `v-for` avec l'objet :

On peut aussi utiliser `v-for` pour utérer sur les propriétés d'un objet.

```
<ul id="v-for-object" class="demo">
  <li v-for="value in object">
    {{ value }}
  </li>
</ul>

new Vue({
  el: '#v-for-object',
  data: {
    object: {
      title: 'How to do lists in Vue',
      author: 'Jane Doe',
      publishedAt: '2016-04-10'
    }
  }
})
```

On peut également fournir un deuxième argument représentant la clé de la propriété courante.

```
<div v-for="(value, name) in object">
  {{ name }}: {{ value }}
</div>
```

et un autre pour l'index :

```
<div v-for="(value, name, index) in object">
  {{ index }}. {{ name }}: {{ value }}
</div>
```

*Note: Quand on itére sur un objet, l'ordre est basé sur l'orde d'énumération de `Object.keys()` et il n'y a* **aucune** *garantie de cohérence à travers toutes les implémentations des moteurs JS.*

Quand Vue met à jour une liste d'éléments rendus avec `v-for`, il utilise par défaut une stratégie de "modification localisée" (**in-place patch**). Si l'ordre des éléments d'un tableau dans `data` a changé, plutôt que de déplacer les éléments du DOM pour concorder avec le nouvel ordre des éléments. Vue va simplement modifier chaque élément déjà en place et s'assurer que cela reflète ce qui aurait dû être rendu à cet index en particulier. C'est un comportement similaire au `track-by="$index"` de la première version de Vue.



Ce mode par défaut est performant, mais adapté seulement lorsque **le résultat du rendu de votre liste ne dépend pas de l’état d’un composant enfant ou de l’état temporaire du DOM (par ex. : les valeurs de champs d’un formulaire)**.

Pour expliquer à Vue comment suivre l'identité de chaque noeud, afin que les éléments existants puissent être réutilisés et réordonnés, vous devez fournir un attribut unique `key` pour chaque élément:

```
<div v-for="item in items" :key="item.id">
  <!-- contenu -->
</div>
```

Il est recommandé de fournir une `key` avec `v-for` chaque fois que possible, à moins que le contenu itéré du DOM soit simple ou que vous utilisiez intentionnellement le comportement de base pour un gain de performance.

*Note: Ne pas utiliser des valeurs non primitive comme des objets ou des tableauw comme clés pour `v-for`. Utiliser des chaînes de caractères ou des nombres à la place.*

## Changement dans un tableau :

Vue surcharge les méthodes de mutation d'un tableau observé afin qu'elles déclenchent également des mises à jour de la vue. Les méthodes sont :

* `push()`
* `pop()`
* `shift()`
* `unshift()`
* `splice()`
* `sort()`
* `reverse()`

Les méthodes de mutation, modifient le tableau d'origine sur lequel elles sont appelées. En comparaison, il y a aussi des méthodes non-mutatives comme par exemple `filter()`, `concat()` et `slice()`, qui ne changent pas le tableau original mais **retourne toujours un nouveau tableau**. Quand on travaille avec des méthodes non-mutatives, on peut juste remplacer l'ancien tableau par le nouveau :

```
example1.items = example1.items.filter(function (item) {
  return item.message.match(/Foo/)
})
```

Remplacer un tableau par un autre contenant des objets différents à certains index est une opération très performante.

Il y a malheureusement des limitations dans tout ça. Vue ne peut pas détecter les changements suivants dans un tableau :

1. Quand on affecte directement un élément à un index.
2. Quand on modifie la longueur du tableau.

Par exemple :

```
var vm = new Vue({
  data: {
    items: ['a', 'b', 'c']
  }
})
vm.items[1] = 'x' // N'est PAS réactive
vm.items.length = 2 // N'est PAS réactive
```

De nouveau, **Vue ne peut détecter l'ajout ou la suppression d'une propriété**. Par exemple :

```
var vm = new Vue({
  data: {
    a: 1
  }
})
// `vm.a` est maintenant réactive

vm.b = 2
// `vm.b` N'est PAS réactive
```

Vue ne permet pas d'ajouter dynamiquement de nouvelles propriétés réactives au niveau racine sur des instances déjà créées. On peut malgré tout utiliser la méthode `Vue.set(object, propertyName, value)`. Par exemple :

```
var vm = new Vue({
  data: {
    userProfile: {
      name: 'Anika'
    }
  }
})

Vue.set(vm.userProfile, 'age', 27)
ou
vm.$set(vm.userProfile, 'age', 27)
```

Cela ajoute un nouvelle propriété `age` à l'objet imbriqué `userProfile`.

Parfois on veut afficher une version filtrée ou triée d'un tableau sans pour autant modifier ou réassigner les données d'origine. Dans ce cas, on peut créer une propriété calculée qui retourne le tableau filtré ou trié.

```
<li v-for="n in evenNumbers">{{ n }}</li>

data: {
  numbers: [ 1, 2, 3, 4, 5 ]
},
computed: {
  evenNumbers: function () {
    return this.numbers.filter(function (number) {
      return number % 2 === 0
    })
  }
}
```

Dabs les situations où les propriétés calculées ne sont pas utilisables, on peut juste utiliser une méthode:

```
<li v-for="n in even(numbers)">{{ n }}</li>

data: {
  numbers: [ 1, 2, 3, 4, 5 ]
},
methods: {
  even: function (numbers) {
    return numbers.filter(function (number) {
      return number % 2 === 0
    })
  }
}
```

`v-for` peut également prendre un nombre entier. Dans ce cas, il répètera le template autant de fois qu'indiqué.

```
<div>
  <span v-for="n in 10">{{ n }} </span>
</div>
```

De la même manière qu'avec `v-if`, on peut également utiliser la balise `<template>` avec `v-for` pour faire le rendu d'une structure contenant de multiples éléments. Par exemple :

```
<ul>
  <template v-for="item in items">
    <li>{{ item.msg }}</li>
    <li class="divider" role="presentation"></li>
  </template>
</ul>
```

*Note: Il n'est pas recommandé d'utiliser `v-if` et `v-for` ensemble.*

Quand ils existent sur le même nœud, `v-for` a une priorité plus élevée que `v-if`. Cela signifie que `v-if` va être exécuté indépendamment à chaque itération de boucle.

On peut directement utiliser `v-for` sur un composant personnalisé, comme sur n'importe quel autre élément standard :

```
<my-component v-for="item in items" :key="item.id"></my-component>
```

*Note: lors de l'utilisation de `v-for` avec un composant, une `key` est maintenant requise*.