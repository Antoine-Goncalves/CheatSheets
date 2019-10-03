# Syntaxe de template :

## Interpolations :

La forme la plus élémentaire de la liaison de données est l'**interpolation** de texte en utilisant la syntaxe *Moustache* (les doubles accolades).

```
<span>Message: {{ msg }}</span>
```

La balise moustache sera remplacée par la valeur de la propriété `msg` de l'objet data correspondant. Elle sera mise à jour à chaque modification de la propriété `msg` de l'objet data.

Possibilité de réaliser des interpolations à usage unique qui ne se mettront pas à jour en utilisant la **directive `v-once`**.

L'interpolations interprètent la **donnée en tant que texte brut, pas en HTML**. Pour afficher réellement du HTML, il faut la **directive `v-html`** (valeur de propriété `rawHtml`).

Les moustache ne peuvent pas être utilisées à l'intérieur des attributs HTML, à la place on utilise la **directive `v-bind`**.

```
<div v-bind:id="dynamicId"></div>
```

Dans le cas des attributs booléens qui impliquent la présence d'une valeur évaluée à `true`, `v-bind` fonctionne différemment.

```
<button v-bind:disabled="isButtonDisabled">Button</button>
```

*Si `isButtonDisabled` a la valeur `null`, `undefined`, ou `false`, l'attribut `disabled` ne sera pas inclus dans l'élément `<button>` généré.*

Vue.js supporte en réalité toute la puissance des expressions JS à l'intérieur de toutes les liaisons de données.

*Note: Il y a une restriction, chacune de ces liaisons ne peut contenir qu'une seule expression, donc pas de déclaration , utilisez le ternaires pas de boucle à l'intérieur*.

## Directives :

Les directives sont des attributs spéciaux avec le préfixe `v-`. Les valeurs attendues pour les attributs de directives sont **une unique expression JS** (à l'exception de `v-for`). Le travail d'une directive est **d'appliquer réactivement des effets secondaires au DOM quand la valeur de son expression change**.

Certaines directives peuvent prendre un "argument", indiqué par un `:` après le nom de la directive. Par exemple, `v-bind` est utilisée pour mettre à jour un attribut HTML.

Un autre exemple est la directive `v-on`, qui écoute les événements du DOM.

Il est aussi possible d'utiliser des expressions JS dans un argument de directive inclus entre crochets :

```
<a v-bind:[attributeName]="url"> ... </a>
```

*Ici `attributeName` va dynamiquement être évalué comme une expression JS et cette valeur d'évaluation va être utilisée comme valeur finale pour l'argument. Exemple, si notre instance de Vue a une propriété de donnée, `attributeName`, et que cette valeur est `"href"`, alors la liaison est équivalente à `v-bind:href`*.

Pareil pour lier un gestionnaire d'évènement à un nom d'évènement dynamique :

```
<a v-on:[eventName]="doSomething"> ... </a>
```

*La valeur `eventName` est `"focus"`, par exemple, `v-on:[eventName] sera équivalent à `v-on:focus`*.

*Note: Contrainte des valeurs d'argument dynamique.

Les arguments dynamiques sont destinés à être évalués comme des chaines de caractères à l'exception de `null`. Car elle peut être utilisée pour retirer la liaison*.

*Note: Contrainte des expressions d'argument dynamique.

Les expressions d'argument dynamique ont des contraintes de syntaxe car certains caractères sont invalides à l'intérieur d'un nom d'attribut HTML comme les espaces ou les guillemets. Du coup il faut utiliser des expressions sans espaces ni guillemets. Attention aussi avec l'écriture Camel Case dans les clés car les navigateurs convertissent les noms d'attribut en lettre minuscule*.

Les modificateurs sont **des suffixes spéciaux indiqués par un point, qui indique qu'une directive devrait être liée d'une manière spécifique**.

Le préfixe `v-` sert d'indicateur visuel pour identifier les attriuts spécifiques à Vue dans nos templates. C'est ultra pratique quand on veut appliquer des comportements dynamiques sur un balisage existant. C'est pourquoi Vue.js fournit des abréviations pour deux des directives les plus utilisées, `v-bind` et `v-on`.

* **Abréviation pour `v-bind`** :

```
<!-- syntaxe complète -->
<a v-bind:href="url"> ... </a>

<!-- abréviation -->
<a :href="url"> ... </a>

<!-- abréviation avec argument dynamique -->
<a :[key]="url"> ... </a>
```

* **Abréviation pour `v-on`**

```
<!-- syntaxe complète -->
<a v-on:click="doSomething"> ... </a>

<!-- abréviation -->
<a @click="doSomething"> ... </a>

<!-- abréviation avec argument dynamique -->
<a @[event]="doSomething"> ... </a>
```
