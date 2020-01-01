# L'ordonnancement avec `setTimeout` et `setInterval`

Imaginons que l'on veut exécuter une fonction mais pas à l'instant T, mais à un certain moment dans le futur. Cela s'appelle "ordonnancer (ou planifier) un appel de fonction" ("scheduling a call").

Deux méthodes existe pour cela :

-   **`setTimeout` permet d'exécuter une fonction une fois uniquement après un certain laps de temps.**
-   **`setInterval` permet d'exécuter une fonction de manière répétée, en commençant après l'intervalle de temps, puis en répétant continuellement à cette intervalle.**

Ces méthodes ne font pas partie de la spécification JS. Mais la plupart des environnements ont un planificateur interne et fournissent ces méthodes. En particulier, elles sont supportées par tous les navigateurs et Node.js.

## `setTimeout`

La syntaxe =>

```javascript
let timerId = setTimeout(func|code, [delay], [arg1], [arg2], ...)
```

Les paramètres :

-   **`func|code` => Fonction ou chaîne de caractères représentant du code à exécuter. En général, c'est une fonction.**
-   **`delay` => La durée d'attente avant l'exécution, en millisecondes, par défaut 0.**
-   **`arg1, arg2 ...` => Arguments à passer à la fonction.**

Exemple :

```javascript
function sayHi() {
  alert('Hello');
}

setTimeout(sayHi, 1000);
```

Si le premier argument est une chaîne de caractères, JS crée alors une fonction à partir de celle-ci.

Exemple :

```javascript
setTimeout("alert('Bonjour')", 1000);
```

_Note: Ceci n'est pas recommandé._

## Annuler une tâche avec `clearTimeout`

Un appel à `setTimeout` renvoie un "identifiant de timer" `timerId` que l'on peut utiliser pour annuler l'exécution de la fonction.

La syntaxe pour annuler une tâche planifiée est la suivante :

```javascript
let timerId = setTimeout(...);
clearTimeout(timerId);
```

## `setInterval`

La méthode `setInterval` a la même syntaxe que `setTimeout` :

```javascript
let timerId = setInterval(func|code, [delay], [arg1], [arg2], ...)
```

la seule différence est que `setInterval` appelle la fonction périodiquement après un interval de temps donné.

Afin d'annuler les appels futurs à la fonction, il est nécessaire d'appeler `clearInterval(timerId)`.

## `setTimeout` imbriqué

Il y a deux façon d'ordonnancer l'exécution périodique d'une tâche.

L'un est `setInterval`. L'autre est un `setTimeout` imbriqué.

Exemple :

```javascript
/** Au lieu de :
let timerId = setInterval(() => alert('tick'), 2000);
*/

let timerId = setTimeout(function tick() {
  alert('tick');
  timerId = setTimeout(tick, 2000); // (*)
}, 2000);
```

Le `setTimeout` imbriqué est une méthode plus flexible que `setInterval`. Ainsi, le prochain appel peut être programmé différemment, en fonction des résultats de l’appel en cours.

**Un `setTimeout` imbriqué permet de définir le délai entre les exécutions plus précisément que `setInterval`.**

## `setTimeout` sans délai

Il y a un cas d'usage particulier : `setTimeout(func, 0)` ou simplement `setTimeout(func)`.

Ceci programme l'exécution de `func` dès que possible. Mais le planificateur ne l'invoquera qu'une fois le script en cours d'exécution terminé.
