# Gestion des erreurs Promesses

Les chaînes de promesse sont super pour la gestion des erreurs. Lorsqu'une promesse est rejetée, le contrôle passe au gestionnaire de rejet le plus proche. C'est très pratique.

Par exemple, dans le code ci-dessous, l'URL `fetch` est incorrecte (aucun site de ce type) et `.catch` gère l'erreur:

```javascript
fetch("https://pas-serveur-connu.blabla") // rejetée
  .then(response => response.json())
  .catch(err => alert(err)); // TypeError: impossible d'aller chercher.
```

Comme on peut le voir, le `.catch` ne doit pas être immédiat. Il peut apparaître après un ou plusieurs `.then`.

Ou, peut-être, tout est ok, mais la réponse n'est pas valide en JSON. Le moyen le plus simple de détecter toutes les erreurs consiste à ajouter `.catch` à la fin de la chaîne :

```javascript
fetch("/article/promise-chaining/user.json")
  .then(response => response.json())
  .then(user => fetch(`https://api.github.com/users/${user.name}`))
  .then(response => response.json())
  .then(
    githubUser =>
      new Promise((resolve, reject) => {
        let img = document.createElement("img");
        img.src = githubUser.avatar_url;
        img.className = "promise-avatar-example";
        document.body.append(img);

        setTimeout(() => {
          img.remove();
          resolve(githubUser);
        }, 3000);
      })
  )
  .catch(error => alert(error.message));
```

Normalement, un tel `.catch` ne se déclenche pas du tout. Mais si l'une des promesses ci-dessus est rejeter (un problème de réseau ou un json invalide ou autre), alors il le rattrapera.

## Implicite try .. catch

Le code d'un exécuteur de promesses et de gestionnaires de promesses est un " `try..catch` invisible" autour de lui. Si une exception se produit, elle est prise et traitée comme un rejet.

Par exemple :

```javascript
new Promise((resolve, reject) => {
  throw new Error("Oups!");
}).catch(alert); // Error: Oups!
```

… Fonctionne exactement de la même manière:

```javascript
new Promise((resolve, reject) => {
  reject(new Error("Oups!"));
}).catch(alert); // Error: Oups
```

Le " `try..catch` invisible" autour de l'exécuteur attrape automatiquement l'erreur et la transforme en promesse rejetée.

Cela se produit non seulement dans la fonction exécuteur, mais aussi dans ses gestionnaires. Si nous utilisons `throw` à l’intérieur d’un gestionnaire `.then`, cela signifie une promesse rejetée, donc le contrôle saute au gestionnaire d’erreur le plus proche.

En voici un exemple:

```javascript
new Promise((resolve, reject) => {
  resolve("ok");
})
  .then(result => {
    throw new Error("Oups!"); // rejette la promesse
  })
  .catch(alert); // Error: Oups!
```
