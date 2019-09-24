# Javascript :

## Comprendre comment fonctionnent `WeaKmap` et `WeakSet` :

Comprendre la principale différence entre :

1. `WeakMap` et `Map`.
2. `WeakSet` `Set`.

### `WeakMap` et `Map` :

La première différence avec `Map` est que les clés `WeakMap` doivent être **des objets et non des valeurs quelconque**.

**`WeakMap` ne supporte pas l'itération et les méthodes `keys()` , `values()` , `entries()` . Donc aucun moyen d'obtenir toutes les clés ou valeurs.**

Les méthodes de `WeakMap` sont :

* `weakMap.get(clé)` => *(retourne la valeur lié à la clé, `undefined` si `clé` n'existe pas dans `weakMap`).*
* `weakMap.set(clé, valeur)` => *(stocke la valeur lié à la clé).*
* `weakMap.delete(clé)` => *(supprime la valeur lié à la clé).*
* `weakMap.has(clé)` => *(retourne `true` si `clé` existe, `false` sinon).*

Le cas d'utilisation le plus fréquent de `WeakMap` est un **stockage de données supplémentaires**.

Si par exemple, on travaille avec un objet qui «appartient» à un autre code, et qui souhaiterait stocker des données qui lui sont associées, cela ne devrait exister pendant que l'objet est en vie , c'est pourquoi `WeakMap` est nécessaire.

avec `WeakMap` , en utilisant l'objet comme clé, et lorsque l'objet est collecté, ces données disparaissent automatiquement. Contrairement à `Map`.

Un autre cas d'utilisation de `WeakMap` est la **mise en cache**.

Il est judicieux d'utiliser `WeakMap` pour que le résultat "mis en cache" sera automatiquement supprimé de la mémoire une fois que l'obje aura été nettoyé.

### `WeakSet` et `Set` :

Même principe que `WeakMap` , mais pour `Set` :

* C'est similaire à `Set`, **mais on peut ajouter que des objets à `WeakSet`** (pas de primitives).
* **Un objet existe dans un `Set` tant qu'il est accesible quelque part**.
* Comme `Set`, **il supporte `add`,`has` et `delete`, mais pas `size`, `keys()` et aucune itérations**.

Il sert également de **stockage supplémentaire**, mais pour des faits "`true` / `false`".
