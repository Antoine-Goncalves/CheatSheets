# Vue JS :

## Instance vue :

[:question: :question:](instanceVue.md)

* **Syntaxe :**

```
var vm = new Vue({
  // options
})
```

* **`Object.freeze()` => empêche les propriétés existantes d'être changées.**

* **`vm.key` Possibilité de changer la valeur d'une objet en appellant l'instance et en ciblant la clé de l'objet ciblé.**

* **Les propriétés et méthodes sont préfixées par `$`.**

## Fonctionnement et syntaxe de template :

[:question: :question:](syntaxeTemplate.md)

### Interpolations :

* **Syntaxe Interpolations (dit "Moustache") =>**

```
<span>Message: {{ msg }}</span>
```

* **La balise moustache sera remplacée par la valeur de la propriété `msg` de l'objet data correspondant. ELle sera mise à jour à chaque modification de la propriété `msg` de l'objet data**.

* **Interpolations interprètent la donnée en texte brut, pas HTML**. *(Il faut utiliser la directive `v-html`)*

* **Interpolations ne peuvent pas être utilisées à l'intérieur des attributs HTML, on utilise donc la directive `v-bind`**.


### Directives :

* **Attributs spéciaux avec comme syntaxe : préfixe `v-`. Le travail d'une directive => appliquer réactivement des effets secondaires au DOM quand la valeur de son expression change**.

* **Possibilité d'utiliser des abréviations pour les directives**.
