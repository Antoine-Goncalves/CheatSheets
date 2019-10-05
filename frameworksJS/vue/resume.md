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

## Intérêt des `computed properties` :

[:question: :question:](computedProperties.md)

* **On doit utiliser les `propriétés calculées` pour toute logique complexe**.

* **On peut lier des données aux `computed properties` dans les templates comme une propriété normal**.

## Liaisons de classes et de styles :

[:question: :question:](liaisonsClassesEtStyles.md)

* **`v-bind` utiliser avec `class` et `style`**.

## Rendu conditionnel :

[:question: :question:](renduConditionnel.md)

* **`v-if` => faire le rendu d'un bloc. Rendu du bloc effectué si l'expression de la directive retourne une valeur vrai**.

* **`v-else` => sert comme une "structure sinon"**.

* **`v-else-if` => sert comme une "structure sinon si"**.

* **`v-show` => la différence est qu'un élément sera toujours restitué et restera dans le DOM**.

### `v-if` vs `v-show` :

* **`v-if` si la condition ne change probablement pas à l'exécution, `v-show` si on a besoin de permuter quelque chose très souvent**.
