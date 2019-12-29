# Rendu conditionnel

## `v-if`

La directive `v-if` est utilisée pour conditionnellement faire le rendu d'un bloc. Le rendu du bloc sera effectué uniquement si l'expression de la directive retourne une valeur évaluée en vrai.

```
<h1 v-if="awesome">Vue est extraordinaire !</h1>
```

Possible d'ajouter une structure "sinon" avec `v-else` :

```
<h1 v-if="awesome">Vue est extraordinaire !</h1>

<h1 v-else>Oh non 😢</h1>
```

Comme `v-if` est une directive, elle doit être attachée à un seul élément. Mais comment faire si on veut permuter plusieurs éléments ? Dans ce cas, on peut utiliser `v-if` sur un élément `<template>`, qui sert d'enveloppe invisible. Le résultat final rendu n'inclura pas l'élément `<template>`.

## `v-else`

On peut utiliser la directive `v-else` pour indiquer une "structure sinon" pour `v-if` :

```
<div v-if="Math.random() > 0.5">
  Maintenant vous me voyez
</div>
<div v-else>
  Maintenant vous ne me voyez pas
</div>
```

Un élément `v-else` doit immédiatement suivre un élément `v-if` ou un élément `v-else-if` (sinon il ne sera pas reconnu).

## `v-else-if`

Le `v-else-if`, comme le nom le suggère, sert comme une "structure sinon si" pour `v-if`.

Semblable à `v-else`, un élément `v-else-if` doit immédiatement suivre un élément `v-if` ou un élément `v-else-if`.

Vue tente de restituer les éléments aussi efficacement que possible, en les réutilisant souvent au lieu de faire de la restitution à partir de zéro. En plus de permettre à Vue d’être très rapide, cela peut avoir quelques avantages utiles. Par exemple, si vous autorisez les utilisateurs à choisir entre plusieurs types de connexion :

```
<template v-if="loginType === 'username'">
  <label>Nom d'utilisateur</label>
  <input placeholder="Entrez votre nom d'utilisateur">
</template>
<template v-else>
  <label>Email</label>
  <input placeholder="Entrez votre adresse email">
</template>
```

Le `<input>` n'est pas remplacé (juste son `placeholder`).

C'est pourquoi Vue offre un moyen de les rendre complètement distincts. Il faut ajouter un attribut `key` avec des valeurs uniques :

```
<template v-if="loginType === 'username'">
  <label>Nom d'utilisateur</label>
  <input placeholder="Entrez votre nom d'utilisateur" key="username-input">
</template>
<template v-else>
  <label>Email</label>
  <input placeholder="Entrez votre adresse email" key="email-input">
</template>
```

## `v-show`

Une autre option pour afficher conditionnellement un élément est la directive `v-show`.

```
<h1 v-show="ok">Bonjour !</h1>
```

La différence est qu’un élément avec `v-show` sera toujours restitué et restera dans le DOM ; `v-show` permute simplement la propriété CSS `display` de l’élément.

*Note: `v-show` ne prend pas en charge la syntaxe de l'élément `<template>` et ne fonctionne pas avec `v-else`*.

## `v-if` vs `v-show`

`v-if` est un "vrai" rendu conditionnel car il garantit que les écouteurs d'évènements et les composants enfants à l'intérieur de la structure conditionnelle sont correctement détruits et recréés lors des permutations.

`v-if` est également **pareseux** : si la condition est fausse sur le rendu initial, il ne fait rien (la structure conditionnelle sera rendue quand la condition sera vraie pour la première fois).

En comparaison, `v-show` est beaucoup plus simple. L'élément est toujours rendu indépendamment de la condition initiale, avec juste une simple permutation basée sur du CSS.

D'une manière général, `v-if` a des couts à la permutation plus élevés alors que `v-show` a des couts au rendu initial plus élevés. Donc on choisit `v-show` si on a besoin de permuter quelque chose très souvent et on choisit `v-if` si la condition ne change probablement pas à l'exécution.

*Note: on utilise `v-if` et `v-for` ensemble n'est* **pas recommandé**.

Lorsque'il est utilisé en même temps que `v-if`, `v-for` a une propriété plus élevée que `v-if`.
