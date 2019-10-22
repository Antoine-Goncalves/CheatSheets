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
