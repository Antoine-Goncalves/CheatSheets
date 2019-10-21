# Callbacks :

Plusieurs actions en JavaScript sont _asynchrones_. C'est-à-dire, on l'initie à un temps T, mais ils se finissent plus tard.

Par exemple, on peut programmer plusieurs actions en utilisant `setTimeout`.

On prend comme exemple la fonction `loadScript(src)`, qui charge un script avec la `src` donnée :

```
function loadScript(src) {
  let script = document.createElement('script');
  script.src = src;
  document.head.append(script);
}
```

On y voit qu'elle ajoute au document une nouvelle balise `<script src="">`, créée dynamiquement, que le navigateur charge et exécute.

On peut donc utiliser cette fonction comme ceci :

```
// charge et exécute le script à l'endroit donné
loadScript('/my/script.js');
```

Le script est exécuté de manière _asynchrone_ car il commence à charger, mais s’exécute plus tard, lorsque la fonction est déjà terminée.

S'il existe un code sous `loadScript(...)`, il n'attend pas la fin du chargement du script.

Si on ajoute une fonction `callback` en tant que second argument de `loadScript` qui doit s'exécuter lors du chargement du script.

```
function loadScript(src, callback) {
  let script = document.createElement('script');
  script.src = src;

  script.onload = () => callback(script);

  document.head.append(script);
}
```

Maintenant si on veut appeler de nouvelles fonctions à partir du script, on doit écrire cela dans un `callback` :

```
loadScript('/my/script.js', function() {
  // le callback se met en marche après que le script est chargé
  newFunction(); // donc maintenant cela fonctionne
  ...
});
```

L'idée est que le second argument est une fonction (généralement anonyme) qui s'exécute lorsque l'action est terminée.

Voici un exemple exécutable avec un script réel:

```
function loadScript(src, callback) {
  let script = document.createElement('script');
  script.src = src;
  script.onload = () => callback(script);
  document.head.append(script);
}

loadScript('https://cdnjs.cloudflare.com/ajax/libs/lodash.js/3.2.0/lodash.js', script => {
  alert(`Cool, the ${script.src} is loaded`);
  alert( _ ); // fonction déclarée dans le script chargé
});
```

C'est ce qu'on appelle un **style de programmation asynchrone "callback-based" (basé sur le rappel)**. Une fonction qui fait quelque chose de manière asynchrone devrait fournir un argument de `callback` lequel on met à s'exécuter une fois terminée.

On as pris un exemple avec `loadScript`, mais bien sur, c'est une approche général.

## Callback dans callback :

On peut charger deux scripts de manière séquentielle : Le premier, puis le second après.

La solution logique serait de placer le second appel `loadScript` dans le `callback` :

```
loadScript('/my/script.js', function(script) {

  alert(`Cool, the ${script.src} is loaded, let's load one more`);

  loadScript('/my/script2.js', function(script) {
    alert(`Cool, the second script is loaded`);
  });

});
```

Une fois le `loadScript` externe terminé, le `callback` initie celui interne. Du coup si on veut plusieurs scripts il suffit juste de les imbriqués.

Ainsi, chaque nouvelle action est dans un rappel. C'est bien pour quelques actions, mais pas bien pour beaucoup.

## Gestion des erreurs :

On as pour l'instant pas pris en compte les erreurs. Mais si notre chargement du script échoue ? Nos `callback` doivent réagir à ça.

```
function loadScript(src, callback) {
  let script = document.createElement('script');
  script.src = src;

  script.onload = () => callback(null, script);
  script.onerror = () => callback(new Error(`Script load error for ${src}`));

  document.head.append(script);
}
```

C'est une version améliorée de `loadScript` qui permet de suivre les erreurs de chargement, il appelle `callback(null, script)` pour un chargement réussi et sinon le `callback(error)`.

```
loadScript('/my/script.js', function(error, script) {
  if (error) {
    // gestion d'erreur
  } else {
    // script chargé avec succes
  }
});
```

Encore une fois, on montre l'exemple avec `loadScript` mais c'est une façon générale. Elle s'appelle le **style "error-first callback" (erreur-premier rappel)**.

La convention est :

1. Le premier argument du `callback` est réserver à une erreur si elle se produit. Puis `callback(err)` est appelé.
2. Le deuxième argument (et les suivants si nécessaire) sont pour le résultat réussi. Ensuite, le `callback(null, result1, result2…)` est appelé.

La fonction de `callback` unique est donc utilisée à la fois pour signaler les erreurs et renvoyer les résultats.

## Pyramide du malheur :

On peut voir que cette méthode est bien pour 2 ou 3 appels imbriqués. Mais si il y a des plusieurs actions asynchrones qui se suit, cela devient problématique :

```
loadScript('1.js', function(error, script) {

  if (error) {
    handleError(error);
  } else {
    // ...
    loadScript('2.js', function(error, script) {
      if (error) {
        handleError(error);
      } else {
        // ...
        loadScript('3.js', function(error, script) {
          if (error) {
            handleError(error);
          } else {
            // ...continue après le chargement de tous les scripts
          }
        });

      }
    })
  }
});
```

Cela s'appelle souvent **"callback hell" (rappel de l'enfer) ou "pyramid of doom" (pyramide du malheur)**.

La "pyramide" des appels imbriqués se développe vers la droite à chaque action asynchrone. Ce n'est pas une bonne solution pour la durée.

On peut donc atténuer le problème en faisant de chaque action une fonction autonome :

```
loadScript('1.js', step1);

function step1(error, script) {
  if (error) {
    handleError(error);
  } else {
    // ...
    loadScript('2.js', step2);
  }
}

function step2(error, script) {
  if (error) {
    handleError(error);
  } else {
    // ...
    loadScript('3.js', step3);
  }
}

function step3(error, script) {
  if (error) {
    handleError(error);
  } else {
    // ...continue après le chargement de tous les scripts
  }
};
```

Il n'y a plus d'imbrication maintenant. Cela fonctionne, mais le code ressemble pas à grand chose non plus. Il est difficile à lire également.

De plus, les fonctions nommées `step*` sont toutes à usage unique, elles sont créées uniquement pour éviter la "pyramide du malheur".

Heureusement, il existe d'autres moyens d'éviter de telles pyramides. L'un des meilleurs moyens consiste à utiliser les [promesses](promesses.md).
