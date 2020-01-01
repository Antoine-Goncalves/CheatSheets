# Promise

1.  _Un `"code producteur"` qui fait quelque chose et prend du temps. Par exemple, un code qui charge les données sur un réseau._
2.  _Un `"code consommateur"` qui veut le résultat du `"code producteur"` une fois prêt. Beaucoup de fonctions peuvent avoir besoin de ce résultat._
3.  **Une `promise` est un objet JavaScript spécial qui lie le `"code producteur"` et le `"code consommateur"`**. _Le `"code producteur"` prend tout le temps nécessaire pour produire le résultat promis, et la `"promesse"` rend ce résultat disponible pour tout le code souscrit lorsqu'il est prêt._

La syntaxe du constructeur pour un objet `promise` est :

```
let promise = new Promise(function(resolve, reject) {
  // exécuteur (le "code producteur")
});
```

La fonction passée à `new Promise` est appelée l'_exécuteur_. Quand `new Promise` est crée, elle s'exécute automatiquement. Elle contient le `"code producteur"`, qui devrait éventuellement produire un résultat.

Les arguments `resolve` et `reject` sont des `callback` fournis par JavaScript lui-même. Le code est seulement à l'intérieur de l'_exécuteur_.

Quand l'_exécuteur_ obtient un résultat, que ce soit tôt ou tard, cela n'a pas d'importance, il devrait appeller l'un de ces `callback` :

- **`resolve(value)` => Si le travail s'est terminé avec succès, avec comme résultat `value`.**
- **`reject(error)` => Si une erreur survient, `error` est l'objet d'erreur.**

Pour résumer : L'_exécuteur_ s'exécute automatiquement, il devrait faire un travail et ensuite appeler soit `resolve` ou `reject`.

L'objet `promise` retourné par le `new Promise` constructeur as des propriétés internes :

- **`state` => initialement `"en attente"` , puis `"rempli"` lorsque `resolve` est appelée ou `"rejeté"` lorsque `reject` est appelé**.
- **`result` => initialement `"undefined"`, puis passe à `value` quand `resolve(value)` est appelée ou `error` quand `reject(error)` est appelé**.

Ainsi , l'_exécuteur_ déplace finalement `promise` dans l'un de ces états.

Voici un exemple de constructeur de promesse et de fonction _exécuteur_ simple avec `"production de code"` prenant du temps (via `setTimeout` ):

```
let promise = new Promise(function(resolve, reject) {
  // la fonction est exécuter automatiquement quand une promesse est construite

  // après 1 seconde signal que le travail est terminé avec le résultat "done"
  setTimeout(() => resolve("done"), 1000);
});
```

On peut voir deux choses en exécutant le code ci-dessus:

1.  **L'** _exécuteur_ **est appelé automatiquement et immédiatement (par `new Promise`)**.
2.  **L'** _exécuteur_ **reçoit deux arguments : `resolve` et `reject` => Ces fonctions sont prédéfinies par le moteur JavaScript. Donc pas besoin de les créer. On as seulement besoin d'appeler l'une d'entre elle lorsqu'on est prêt.**

Après une seconde de "traitement" l'_exécuteur_ appelle `resolve("done")` pour produire le résultat. Cela change `state` de l'objet `promise`.

C’était un exemple de réussite du travail, une "promesse remplie".

Et maintenant un exemple de l'exécuteur rejettant une promesse avec une erreur :

```
let promise = new Promise(function(resolve, reject) {
  // après 1 seconde signalant que le travail est terminé avec une erreur
  setTimeout(() => reject(new Error("Whoops!")), 1000);
});
```

L'appel à `reject(...)` déplace l'objet de promesse à l'état `"rejected"`.

En résumé, l'exécuteur doit effectuer un travail (quelque chose qui prend généralement du temps), puis appeler `resolve` ou `reject` pour modifier l'état de l'objet de promesse correspondant.

Une promesse qui est soit résolue soit rejetée est appelée `"réglée"`, par opposition à une promesse initialement `"en attente"`.

_Note: Il ne peut y avoir qu'un seul résultat ou une erreur, l'exécuteur doit appeler seulement un `resolve` ou un `reject`. Tout changement d'état est définitif. De plus, `resolve` et `reject` n'attend qu'un seul argument (ou aucun) et ignorera les arguments supplémentaires._

_Note: Les propriétés de l'objet promise `state` et `result` sont internes. On ne peut pas y accéder directement. On peut utiliser les méthodes `.then`, `.catch` ou `.finally` pour ça._

## Consommateurs => `then`, `catch` et `finally`

L'objet promise sert de lien entre l'_exécuteur_ (le `"code producteur"`) et les fonctions consommatrices, qui recevront le résultat ou l'erreur. Les fonctions consommatrices peuvent être enregistrées (souscrites) en utilisant les méthodes `.then`, `.catch` et `.finally`.

### `then`

Le plus important, fondamental est `.then`.

La syntaxe est :

```
promise.then(
  function(result) { /* gestion d'un résultat réussi */ },
  function(error) { /* gestion d'une erreur */ }
);
```

Le premier argument de `.then` est une fonction qui s'exécute lorsque la promesse est résolue et reçoit le résultat.

Le deuxième argument de `.then` est une fonction qui s'exécute lorsque la promesse est rejetée et reçoit l'erreur.

Par exemple, voici une réaction à une promesse résolue avec succès:

```
let promise = new Promise(function(resolve, reject) {
  setTimeout(() => resolve("done!"), 1000);
});

// resolve exécute la première fonction en .then
promise.then(
  result => alert(result), // affiche "done!" après 1 seconde.
  error => alert(error) // ne fonctionne pas
);
```

Et le cas du refus :

```
let promise = new Promise(function(resolve, reject) {
  setTimeout(() => reject(new Error("Whoops!")), 1000);
});

// reject exécute la seconde fonction en .then
promise.then(
  result => alert(result), // ne fonctionne pas
  error => alert(error) // affiche "Error: Whoops!" après 1 seconde.
);
```

Si on s'intéresse seulement par les complétions réussies, on ne peut fournir qu'un seul argument de fonction à `.then` :

```
let promise = new Promise(resolve => {
  setTimeout(() => resolve("done!"), 1000);
});

promise.then(alert); // affiche "done!" après 1 seconde.
```

### `catch`

Si on s'intéresse seulement aux erreurs, alors on peut utiliser `null` comme premier argument : `.then(null, errorHandlingFunction)`. Ou on peut utiliser `.cath(errorHandlingFunction)`, qui est exactement pareil :

```
let promise = new Promise((resolve, reject) => {
  setTimeout(() => reject(new Error("Whoops!")), 1000);
});

// .catch(f) est pareil que promise.then(null, f)
promise.catch(alert); // affiche "Error: Whoops!" après 1 seconde
```

L'appel `.catch(f)` est juste un raccourci de `.then(null, f)`.

### `finally`

L'appel `.finally(f)` est similaire à `.then(f, f)` en ce sens que `f` toujours exécuté lorsque la promesse est réglée: résolue ou rejetée.

`finally` est un bon gestionnaire pour effectuer le nettoyage, par exemple en arrêtant nos indicateurs de chargement, car ils ne sont plus nécessaires, quel que soit le résultat.

Comme ceci :

```
new Promise((resolve, reject) => {
  /* faire quelque chose qui prend du temps, puis appeler resolve/reject */
})
  // s'exécute lorsque la promesse est réglée, peu importe avec succès ou non
  .finally(() => stop loading indicator)
  .then(result => show result, err => show error)
```

Il y a plusieurs différences avec `then(f,f)` :

1.  Le gestionnaire `finally` n'as pas d'argument. Dans `finally` on ne sait pas si la promesse est réussie ou non. Ce n'est pas grave, car notre tâche consiste généralement à effectuer des procédures de finalisation "générales".
2.  Un gesstionnaire `finally` transmet les résultats et les erreurs au gestionnaire suivant. C'est très pratique, parce que `finally` n'est pas destiné à traiter un résultat de promesse. Alors ça passe à travers.
3.  Dernier point, mais non des moindres, `.finally(f)` est une syntaxe plus pratique que `.then(f, f)` : inutile de dupliquer la fonction `f`.

On peut voir des exemples où les promesses peuvent aider à écrire du code asynchrone.

On réécrit la fonction `loadScript` mais en utilisant les `promises`.

Elle ne requiert pas de `callback`. Au lieu de cela, il créera et retournera un objet `promise` qui sera résolu une fois le chargement terminé. Le code externe peut lui ajouter des gestionnaires en utilisant `.then` :

```
function loadScript(src) {
  return new Promise(function(resolve, reject) {
    let script = document.createElement('script');
    script.src = src;

    script.onload = () => resolve(script);
    script.onerror = () => reject(new Error(`Script load error for ${src}`));

    document.head.append(script);
  });
}
```

Usage :

```
let promise = loadScript("https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.11/lodash.js");

promise.then(
  script => alert(`${script.src} is loaded!`),
  error => alert(`Error: ${error.message}`)
);

promise.then(script => alert('Another handler...'));
```

On peut immédiatement voir quelques avantages par rapport au modèle basé sur le rappel :

| `Promesse`                                                                                                                                                             | `Callback`                                                                                                                                                                                             |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Les promesses permettent de faire les choses dans l'ordre naturel. Tout d'abord, on exécute `loadScript(script)` , puis `.then` écrit quoi faire avec le résultat.** | **On doit avoir une fonction `callback` à disposition lorsqu'on appelle `loadScript(script, callback)`. En d'autres termes, on doit savoir quoi faire avec le résultat avant d'appeler `loadScript`.** |
| **On peut faire appel à une promesse `.then` autant de fois qu'on souhaite. À chaque fois, on ajoute un "code consommateur", une nouvelle fonction, à la "promesse".** | **Il ne peut y avoir qu'un seul `callback`**.                                                                                                                                                          |

Les promesses donnent donc un meilleur flux de code et une meilleur flexibilité.
