# Composants

Exemple de base :

```javascript
// Définition d'un nouveau composant appelé `button-counter`
Vue.component('button-counter', {
  data: function () {
    return {
      count: 0
    }
  },
  template: '<button v-on:click="count++">Vous m\'avez cliqué {{ count }} fois.</button>'
})
```

Les composants sont des instances de Vue réutilisables avec un nom: dans notre cas `<button-counter>`. On peut utiliser ce composant en tant qu'élément personnalisé à l'intérieur d'une instance de Vue racine créée avec `new Vue` :

```javascript
<div id="components-demo">
  <button-counter></button-counter>
</div>

new Vue({ el: '#components-demo' })
```

Puisque les composants sont des instances de Vue réutilisables, ils acceptent les mêmes options que `new Vue` comme `data`, `computed`, `watch`, `methods`, et les hooks du cycle de vie. Les seules exceptions sont quelques options spécifiques à la racine comme `el`.

Les composants peuvent être réutilisés autant de fois que souhaité :

```javascript
<div id="components-demo">
  <button-counter></button-counter>
  <button-counter></button-counter>
  <button-counter></button-counter>
</div>
```

Quand on définit le composant `<button-counter>`, on doit faire attention que `data` ne soit pas directement fourni en tant qu'objet. **La propriété du composant `data` doit être une fonction**, afin que chaque instance puisse conserver une copie indépendante de l'objet retourné :

```javascript
data: function () {
  return {
    count: 0
  }
}
```

*Note : Si Vue n'avait pas cette règle , cliquer sur un bouton affecterait les données de toutes les autres instances.*

Pour utiliser ces composants dans des templates, ils doivent être enregistrés pour que Vue les connaisse. Il y a deux types d'enregistrement de composant: **global** et **local**. On as vu uniquement en global avec `Vue.component` :

```javascript
Vue.component('my-component-name', {
  // ... options ...
})
```

Les composants enregistrés globalement peuvent être utilisés dans le template de n'importe quelle instance racine de Vue (`new Vue`) créée après coup, ainsi que dans les sous-composants de l'arbre des composants de cette instance de Vue.

Les props sont des attributs personnalisables qu'on peut enregister dans un composant. Quand une valeur est passée à un attribut prop, elle devient une propriété de l'instance du composant. Pour passer un titre à quelque chose, on doit l'inclure dans une liste de props que ce composant accepte, en utilisant l'option `props` :

```javascript
Vue.component('blog-post', {
  props: ['title'],
  template: '<h3>{{ title }}</h3>'
})
```

Un composant peut avoir autant de props que l'on souhaite et par défaut, n'importe quelle valeur peut être passée à une prop. Dans le template ci-dessus, on doit voir cette valeur dans l'instance du composant, comme pour `data`.

Une fois une prop enregistrée, on peut lui passer des données en tant qu'attribut personnalisé comme ceci :

```javascript
<blog-post title="Mon initiation avec Vue"></blog-post>
<blog-post title="Blogger avec Vue"></blog-post>
<blog-post title="Pourquoi Vue est tellement cool"></blog-post>
```

Dans une application typique, on préfère avoir un tableau de billets dans `data` :

```javascript
new Vue({
  el: '#blog-post-demo',
  data: {
    posts: [
      { id: 1, title: 'Mon initiation avec Vue' },
      { id: 2, title: 'Blogger avec Vue' },
      { id: 3, title: 'Pourquoi Vue est tellement cool' }
    ]
  }
})
```

Maintenant, faisons le rendu d'un composant pour chacun :

```javascript
<blog-post
  v-for="post in posts"
  v-bind:key="post.id"
  v-bind:title="post.title"
></blog-post>
```

On peut utiliser `v-bind` pour dynamiquement passer des props. Cela est particulièrement utile quand on connait pas exactement le contenu dont on est en train de faire le rendu à l'avance.

Quand on réalise un composant `<blog-post>`, notre template va éventuellement contenir plus que juste le titre :

```javascript
<h3>{{ title }}</h3>
```

**Tout composant doit avoir un unique élément racine**.

Le temps sera alors venu de refactoriser le composant `<blog-post>` pour accepter une propriété `post` unique à la place :

```javascript
<blog-post
  v-for="post in posts"
  v-bind:key="post.id"
  v-bind:post="post"
></blog-post>

Vue.component('blog-post', {
  props: ['post'],
  template: `
    <div class="blog-post">
      <h3>{{ post.title }}</h3>
      <div v-html="post.content"></div>
    </div>
  `
})
```

Maintenant, chaque fois qu'une nouvelle propriété sera ajoutée à l'objet `post`, elle sera automatiquement disponible dans `<blog-post>`.

Lors de notre développement du composant `<blog-post>`, plusieurs fonctionnalités vont demander de communiquer des info au parent.

Il est parfois utile d'émettre une valeur spécifique avec un évènement.

Les évènements personnalisés peuvent aussi être utilisés pour créer des champs qui fonctionnent avec `v-model`.

Par exemple :

```javascript
Vue.component('custom-input', {
  props: ['value'],
  template: `
    <input
      v-bind:value="value"
      v-on:input="$emit('input', $event.target.value)"
    >
  `
})
```

Exactement comme les éléments HTML, il est souvent utile de passer du contenu à un composant comme ceci :

```javascript
<alert-box>
  Quelque chose s'est mal passé.
</alert-box>
```

Heureusement, cette tâche est vraiment simple avec l’élément personnalisé `<slot>` de Vue :

```javascript
Vue.component('alert-box', {
  template: `
    <div class="demo-alert-box">
      <strong>Erreur !</strong>
      <slot></slot>
    </div>
  `
})
```

Parfois, il est utile de dynamiquement interchanger des composants.

Ceci est rendu possible grâce à l'élément `<component>` de Vue avec l'attribut spécial `is` :

```javascript
<!-- Component changes when currentTabComponent changes -->
<component v-bind:is="currentTabComponent"></component>
```

Plusieurs éléments HTML, comme `<ul>`, `<ol>`, `<table>` et `<select>` ont des restrictions en ce qui concerne les éléments à l'intérieur desquels ils apparaissent. D’autres éléments quant à eux, tel que `<li>`, `<tr>`, ou `<option>` peuvent uniquement être placés à l’intérieur de certains éléments parents uniquement.

Il doit être noté que **cette limitation n'affecte pas les templates sous forme de chaîne de caractères provenant d'une des sources suivantes** :

*   **Un template de chaîne de caractères**.
*   **Les composants monofichier (`.vue`)**.
*   **`<script type="text/x-template">`.**
