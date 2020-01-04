# Closure

Si variable global créer alors le changement dans une fonction se fait sur tout le code.

Exemple :

```javascript
let name = "John";

function sayHi() {
  alert("Hi, " + name);
}

name = "Pete";

sayHi(); // Cela affiche "Pete".
```

Si variable interne alors le changement ne s'affectue pas.

Exemple :

```javascript
function makeWorker() {
  let name = "Pete";

  return function() {
    alert(name);
  };
}

let name = "John";

let work = makeWorker();

work(); // Cela affiche "Pete".
```

## Environnement Lexical

2 parties :

*   Environnement Record (Enregistrement d'Environnement) - un objet qui stocke toutes les variable locales en tant que propriétés.
*   Une référence à l'environnement lexical externe, celui associé au code externe.

*   **Une variable est une propriété d'un objet interne spécial, associée au bloc/fonction/script en cours d'exécution.**
*   **Travailler avec des variables, c'est travailler avec les propriétés de cet objet.**

Quand on créer une fonction , deux environnement lexicaux se crée :

*   L'environnement interne.
*   L'environnement externe.

**Lorsque le code veut accéder à une variable, l'environnement lexical interne est recherché en premier, puis l'environnement externe, puis l'environnement externe et ainsi de suite jusqu'à l'environnement global.**

*   **Une fonction obtient les variables externes telles qu'elles sont maintenant, elle utilise les valeurs les plus récentes.**

_Note : Un appel - un environnement lexical => Une nouvelle fonction Environnement lexical est créée à chaque exécution d'une fonction. Et si une fonction est appelée plusieurs fois, chaque appel aura son propre environnement lexical, avec des variables locales et des paramètres spécifiques à cette exécution._

Toutes les fonctions “à la naissance” reçoivent une propriété cachée `[[Environment]]` avec une référence à l'environnement lexical de leur création.

_Note : Closure => Qui se souvient automatiquement de l'endroit où ils ont été créés à l'aide d'une propriété `[[Environment]]` cachée, et tous peuvent accéder aux variables externes. (Fonctions qui a accès a des variables externes)_

L'environnement lexical s'applique pour tout bloc de code `{...}`.

*   **Un environnement lexical est créé lors de l’exécution d’un bloc de code et contient des variables locales au bloc.**

*   **Un environnement lexical est nettoyé et supprimé après l'exécution de la fonction.**
