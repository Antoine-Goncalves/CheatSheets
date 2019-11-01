# Promesses Chaining :

L'enchaînement des promesses ressemble à ça :

```
new Promise(function(resolve, reject) {

  setTimeout(() => resolve(1), 1000); // (*)

}).then(function(result) { // (**)

  alert(result); // 1
  return result * 2;

}).then(function(result) { // (***)

  alert(result); // 2
  return result * 2;

}).then(function(result) {

  alert(result); // 4
  return result * 2;

});
```

L'idée est que le résultat est transmis à travers la chaîne de gestionnaires `.then`.

Ici le flux est :

1. La promesse initiale est résolue en 1 seconde `(*)`
2. Puis, le gestionnaire `.then` est appelé `(**)`.
3. La valeur qu'il renvoie est transmise au prochain gestionnaire `.then` `(***)`
4. ...etc.

Lorsque le résultat est transmis le long de la chaîne de gestionnaires, on peut voir une séquence d'appels `alert` : `1` -> `2` -> `4`.

Le tout fonctionne, car une appel à `promise.then` renvoie une promesse, de sorte qu'on puisse appeler le prochain `.then` dessus.

Lorsqu'un gestionnaire renvoie une valeur, cela devient le résultat de cette promesse. Le prochain `.then` est appelé avec.

**Une erreur classique pour les débutants: techniquement, on peut également ajouter plusieurs `.then` à une seule promesse. Ceci n'est pas le chaînage des promesses.**

Par exemple :

```
let promise = new Promise(function(resolve, reject) {
  setTimeout(() => resolve(1), 1000);
});

promise.then(function(result) {
  alert(result); // 1
  return result * 2;
});

promise.then(function(result) {
  alert(result); // 1
  return result * 2;
});

promise.then(function(result) {
  alert(result); // 1
  return result * 2;
});
```

Ce qui est fait ici n'est que plusieurs gestionnaires contre une promesse. Ils ne se transmettent pas le résultat, ils le traitent de manière indépendante.

Tous les `.then` sur la même promesse obtiennet le même résultat (ici `1`).

En pratique, on as rarement besoin de plusieurs gestionnaires pour une même promesse. Le chaînage est utilisé beaucoup plus souvent.

## Renvoie de promesses :

Un gestionnaire, utilisé dans `.then(handler)` peut créer et renvoyer une promesse.

Dans ce cas, d'autres gestionnaires jusqu'a ce qu'elle soit tenue, puis obtiennent son résultat.

Par exemple :

```
new Promise(function(resolve, reject) {

  setTimeout(() => resolve(1), 1000);

}).then(function(result) {

  alert(result); // 1

  return new Promise((resolve, reject) => { // (*)
    setTimeout(() => resolve(result * 2), 1000);
  });

}).then(function(result) { // (**)

  alert(result); // 2

  return new Promise((resolve, reject) => {
    setTimeout(() => resolve(result * 2), 1000);
  });

}).then(function(result) {

  alert(result); // 4

});
```

Ce qui change avec le code ci-dessus , il y a maintenant un délair d'une seconde entre les appels `ælert`.

Le renvoie des promesses permet de contruire des chaînes d'actions asynchrones.

## Exemple : `fetch` :

La syntaxe est :

```
let promise = fetch (url);
```

Cela fait une requête réseau à l'`url` et renvoie une promesse. La promesse se résout avec un objet `response` lorsque le serveur distant répond avec des en-têtes, mais _avant le téléchargement complet de la réponse._

Pour lire la réponse complète, appelez la méthode `response.text()` : elle renvoie une promesse qui résout le téléchargement du texte intégral à partir du serveur distant, avec ce texte en conséquence.

Le code ci-dessous envoie une requête à `user.json` et charge son texte depuis le serveur :

```
fetch('/article/promise-chaining/user.json')
  // .then ci-dessous s'exécute lorsque le serveur distant répond
  .then(function(response) {
    // response.text() renvoie une nouvelle promesse qui résout avec le texte de réponse complet
    // quand ça charge
    return response.text();
  })
  .then(function(text) {
    // ...et voici le contenu du fichier distant
    alert(text); // {"name": "iliakan", isAdmin: true}
  });
```

Il existe également une méthode `response.json()` qui lit les données distantes et les analyse au format JSON. Dans notre cas, c’est encore plus pratique, alors on passe à cela.

```
// comme ci-dessus, mais response.json() analyse le contenu distant en tant que JSON
fetch('/article/promise-chaining/user.json')
  .then(response => response.json())
  .then(user => alert(user.name)); // iliakan, nom d'utilisateur obtenu
```

Maintenant on peut faire quelque chose avec l'utilisateur chargé.

Par exemple, on peut faire une demande pour charger le profil de l'utilisateur et afficher l'avatar :

```
// Faire une demande pour user.json
fetch('/article/promise-chaining/user.json')
  // Charger en tant que json
  .then(response => response.json())
  // Faire une demande à GitHub
  .then(user => fetch(`https://api.github.com/users/${user.name}`))
  // Charger la réponse en tant que json
  .then(response => response.json())
  // Afficher l'image de l'avatar (githubUser.avatar_url) pendant 3 secondes (peut-être l'animer)
  .then(githubUser => {
    let img = document.createElement('img');
    img.src = githubUser.avatar_url;
    img.className = "promise-avatar-example";
    document.body.append(img);

    setTimeout(() => img.remove(), 3000); // (*)
  });
```

Ce code fonctionne mais il y a une erreur typique pour un débutants qui utilise les promesses.

On ne peut pas faire quelque chose d'autre après la suppression de l'avatar.

POur rendre la chaîne extensible, on doit retourner une promesse qui sera résolue une fois que l'avatar aura fini de s'afficher.

Comme ceci :

```
fetch('/article/promise-chaining/user.json')
  .then(response => response.json())
  .then(user => fetch(`https://api.github.com/users/${user.name}`))
  .then(response => response.json())
  .then(githubUser => new Promise(function(resolve, reject) { // (*)
    let img = document.createElement('img');
    img.src = githubUser.avatar_url;
    img.className = "promise-avatar-example";
    document.body.append(img);

    setTimeout(() => {
      img.remove();
      resolve(githubUser); // (**)
    }, 3000);
  }))
  // se déclenche après 3 secondes
  .then(githubUser => alert(`Finished showing ${githubUser.name}`));
```

En d’autres termes, le gestionnaire `.then` à la ligne (\*) renvoie `new Promise`, qui ne sera réglé qu’après l’appel de `resolve(githubUser)` dans `setTimeout` (\*\*).

Le prochain `.then` dans la chaîne attendra cela.

En règle générale, une action asynchrone doit toujours renvoyer une promesse.

Cela permet de planifier des actions après. Même si on as pas l’intention d’étendre la chaîne maintenant, on en aura peut-être besoin plus tard.

Enfin, on peut découper le code en fonctions réutilisables:

```
function loadJson(url) {
  return fetch(url)
    .then(response => response.json());
}

function loadGithubUser(name) {
  return fetch(`https://api.github.com/users/${name}`)
    .then(response => response.json());
}

function showAvatar(githubUser) {
  return new Promise(function(resolve, reject) {
    let img = document.createElement('img');
    img.src = githubUser.avatar_url;
    img.className = "promise-avatar-example";
    document.body.append(img);

    setTimeout(() => {
      img.remove();
      resolve(githubUser);
    }, 3000);
  });
}

// Utilise les:
loadJson('/article/promise-chaining/user.json')
  .then(user => loadGithubUser(user.name))
  .then(showAvatar)
  .then(githubUser => alert(`Finished showing ${githubUser.name}`));
  // ...
```
