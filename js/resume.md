# Javascript :

## Variables :

[:question: :question:](variable.md)

* **Pour créer une variable en js => `let`**.
* **Ancienne version => `var`**.
* **Variable non changeante => `const`**.

## 7 Types de données :

[:question: :question:](typesDeDonnees.md)

* **number => pour les nombres de toute sorte: entier ou virgule flottante**.
* **string => pour les chaînes de caractères**.
* **boolean => pour **`true` / `false`.
* **null => pour les valeurs inconnues**.
* **undefined => pour les valeurs non attribuées**.
* **object => pour des structures de données plus complexes**.
* **symbol => d'identificateurs uniques**. 
* **(typeof => permet de connaitre le type de contenu dans une variable)**.

## Conversion de types en JS :

[:question: :question:](conversionDeTypes.md)

Les trois conversions de types les plus utilisées sont chaîne, nombre et booléen.

* **String Conversion => `String(value)`**.
* **Numeric Conversion => `Number(value)`**.
* **Boolean Conversion => `Boolean(value)`**.
 
## `WeakMap` et `WeakSet` :

[:question: :question:](weakMapAndWeakSet.md)

* **`WeakMap` est une collection semblable à `Map` qui n'accepte que les objets en tant que clés et les supprime avec la valeur associée une fois qu'ils sont inaccessibles par d'autres moyens**.
* **`WeakSet` est une collection semblable à `Set` qui stocke uniquement les objets et les supprime une fois qu'ils deviennent inaccessible par d'autres moyens**.
* **Les deux ne prennent pas en charge les méthodes et propriétés qui font référence à toutes les clés ou à leur nombre. Seules les opérations individuelles sont autorisées**.
* **`WeakMap` et `WeakSet` sont utilisés comme structures de données «secondaires» en plus du stockage d'objet «principal». Une fois que l'objet est supprimé de la mémoire principale, s'il est uniquement trouvé en tant que clé de `WeakMap` ou dans un `WeakSet` , il sera automatiquement nettoyé**.

## Destructuration en js :

[:question: :question:](destructuration.md)

* **L'attribution de destructuration permet de modéliser un `object` ou un `array` sur de nombreuses variables**.

* **Syntaxe `object` => `let {propriété : nom de variable = défaut,...rest} = object`**.

*La `propriété` doit aller dans la variable `nom de variable` et que, si aucune propriété de ce type n'existe, la valeur `défaut` doit être utilisée*.

*Les propriétés d'objet sans modélisation sont copiées dans l'objet `rest`*.

* **Syntaxe `array` => `let [element1 = défaut, element2, ...rest] = array`**.

*Le premier élément va à `element1` ; le second passe à `element2`, tout le reste se met dans un tableau `rest`*.

* **Il est possible d'extraire des données de tableaux/ objets imbriqués, car le côté gauche doit avoir la même structure que le côté droit**.

## `Recursion` et `stack` :

[:question: :question:](recursionAndStack.md)

* **`Recursion` => Terme de programmation qui signifie appeler une fonction à partir de lui-même. Les fonctions récursives peuvent être utilisées pour résoudre des tâches de manière élégante**.

* **`recursion step` => Lorsqu'une fonction s'appelle elle-même. La base de la récursivité est constituée par les arguments de la fonction qui rendent la tâche si simple que la fonction ne fait plus d'appels**.

* **Une structure de données définie de manière récursive => Structure de données qui peut être définie à l'aide de celle-ci**.

* **Toute fonction récursive peut être réécrite en une fonction itérative. Et c'est parfois nécessaire pour optimiser les choses. Mais pour de nombreuses tâches, une solution récursive est assez rapide et plus facile à écrire et à supporter**.

## `Rest parameters` et `spread operator` :

[:question: :question:](spreadOperatorAndRestParameters.md)

* **Quand on voit `...` dans le code , 2 choix s'offrent à nous :**
	- **Quand `...` est à la fin du paramètre de la fonction => c'est appeler `rest parameters` et rassemble le reste de la liste des arguments dans un tableau.**
	- **Quand `...` se fait à la fin d'une appel de fonction ou similaire => c'est appeler `spread operator` et étend un tableau dans une liste.**
* **`Rest parameters` => Utilisés pour créer des fonctions acceptant un nombre quelconque d'arguments.**
* **`Spread operator` => Utilisé pour passer un tableau à des fonctions nécessitant normalement une liste d'arguments.**

* **À deux, ils permettent de voyager facilement entre une liste et un tableau de paramètres.**
