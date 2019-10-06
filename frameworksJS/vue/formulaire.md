# Liaisons sur les champs de formulaire :

On peut utiliser la directive `v-model` pour créer une liaison de données bidirectionnelle sur les champs de formulaire (input, selec ou textarea). Elle choisira automatiquement la bonne manière de mettre à jour l'élément en fonction du type de champ. Bien qu'un peu magique, `v-model` est essentiellement du sucre syntaxique pour mettre à jour les données lors des évènements de saisie utilisateur sur les champs, ainsi que quelques traitements spéciaux pour certains cas particuliers.

*Note: `v-model` ne prend pas en compte la valeur initiale des attributs `value`, `checked` ou `selected` fournis par un champ. Elle traitera toujours les données de l’instance de vue comme la source de vérité. On doit déclarer la valeur initiale dans notre JS, dans l’option `data` de notre composant*.

`v-model` utilise en interne différentes propriétés et émetteurs d'évènement pour différents éléments de saisie :

* **Les éléments `text` et `textarea` utilisent la propriété `value` et évènement `input`**;
* **Les éléments `checkboxes` et `radiobuttons` utilisent la propriété `checked` et l'évènement `change`**;
* **Les évènements `select` utilisent `value` comme une propriété et `change` comme un évènement**.

## Texte :

```
<input v-model="message" placeholder="modifiez-moi">
<p>Le message est : {{ message }}</p>
```

## Texte multiligne :

```
<span>Le message multiligne est :</span>
<p style="white-space: pre-line;">{{ message }}</p>
<br>
<textarea v-model="message" placeholder="ajoutez plusieurs lignes"></textarea>
```

## Checkbox :

```
<input type="checkbox" id="checkbox" v-model="checked">
<label for="checkbox">{{ checked }}</label>
```

## Radio :

```
<input type="radio" id="one" value="Un" v-model="picked">
<label for="one">Un</label>
<br>
<input type="radio" id="two" value="Deux" v-model="picked">
<label for="two">Deux</label>
<br>
<span>Choisi : {{ picked }}</span>
```

## Select :

```
<select v-model="selected">
  <option disabled value="">Choisissez</option>
  <option>A</option>
  <option>B</option>
  <option>C</option>
</select>
<span>Sélectionné : {{ selected }}</span>

new Vue({
  el: '...',
  data: {
    selected: ''
  }
})
```

Options dynamiques générées avec `v-for` :

```
<select v-model="selected">
  <option v-for="option in options" v-bind:value="option.value">
    {{ option.text }}
  </option>
</select>
<span>Sélectionné : {{ selected }}</span>

new Vue({
  el: '...',
  data: {
    selected: 'A',
    options: [
      { text: 'Un', value: 'A' },
      { text: 'Deux', value: 'B' },
      { text: 'Trois', value: 'C' }
    ]
  }
})
```

## Liaisons des attributs value :

Pour les boutons radio, les cases à cocher et les listes d'options, les valeurs de liaison de `v-model` sont habituellement des chaînes de caractères statiques (ou des booléens pour une case à cocher) :

```
<!-- `picked` sera une chaine de caractères "a" quand le bouton radio sera sélectionné -->
<input type="radio" v-model="picked" value="a">

<!-- `toggle` est soit true soit false -->
<input type="checkbox" v-model="toggle">

<!-- `selected` sera une chaine de caractères "abc" quand la première option sera sélectionnée -->
<select v-model="selected">
  <option value="abc">ABC</option>
</select>
```

Mais parfois on peut souhaiter lier la valeur à une propriété dynamique de l’instance de Vue. On peut réaliser cela en utilisant `v-bind`. De plus, utiliser `v-bind` nous permet de lier la valeur de l’input à des valeurs qui ne sont pas des chaines de caractères.

## Modificateurs :

* `.lazy` :

Par défaut, `v-model` synchronise le champ avec les données après chaque évènement `input`. On peut ajouter le modificateur `lazy` pour synchroniser après les évènements `change` à la place :

```
<!-- synchronisé après le "change" au lieu du "input" -->
<input v-model.lazy="msg" >
```

* `.number` :

Si on veut que la saisie utilisateur soit automatiquement convertie en nombre, on peut ajouter le modificateur `number` à vos champs gérés par `v-model` :

```
<input v-model.number="age" type="number">
```

* `.trim` :

Si on veut que les espaces superflus de saisies utilisateur soient automatiquement retirés, on peut ajouter le modificateur `trim` à vos champs gérés par `v-model` :

```
<input v-model.trim="msg">
```

Les types de champ standards HTML ne couvriront pas toujours vos besoins. Heureusement, les composanys de Vue nous permettent de construire des champs avec un comportement complètement personnalisé. Ces champs fonctionnent même avec `v-model` !
