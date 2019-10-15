# Javascript :

## Variables :

[:question: :question:](variable.md)

- **Pour créer une variable en js => `let`**.
- **Ancienne version => `var`**.
- **Variable non changeante => `const`**.

## 7 Types de données :

[:question: :question:](typesDeDonnees.md)

- **number => pour les nombres de toute sorte: entier ou virgule flottante**.
- **string => pour les chaînes de caractères**.
- **boolean => pour `true` et `false`**.
- **null => pour les valeurs inconnues**.
- **undefined => pour les valeurs non attribuées**.
- **object => pour des structures de données plus complexes**.
- **symbol => d'identificateurs uniques**.
- **(typeof => permet de connaitre le type de contenu dans une variable)**.

## Conversion de types en JS :

[:question: :question:](conversionDeTypes.md)

Les trois conversions de types les plus utilisées sont chaîne, nombre et booléen.

- **String Conversion => `String(value)`**.
- **Numeric Conversion => `Number(value)`**.
- **Boolean Conversion => `Boolean(value)`**.

## Operateurs :

[:question: :question:](operateurs.md)

- **Un operand est ce à quoi les opérateurs sont appliqués.**

- **Un opérateur est unaire si il a un operand seule**.

- **Un opérateur est binaire si il a 2 operand**.

- **binary+ => concatener 2 chaînes**.

- **unary+ => convertit les chaînes en nombres**.

## `WeakMap` et `WeakSet` :

[:question: :question:](weakMapAndWeakSet.md)

- **`WeakMap` est une collection semblable à `Map` qui n'accepte que les objets en tant que clés et les supprime avec la valeur associée une fois qu'ils sont inaccessibles par d'autres moyens**.
- **`WeakSet` est une collection semblable à `Set` qui stocke uniquement les objets et les supprime une fois qu'ils deviennent inaccessible par d'autres moyens**.
- **Les deux ne prennent pas en charge les méthodes et propriétés qui font référence à toutes les clés ou à leur nombre. Seules les opérations individuelles sont autorisées**.
- **`WeakMap` et `WeakSet` sont utilisés comme structures de données «secondaires» en plus du stockage d'objet «principal». Une fois que l'objet est supprimé de la mémoire principale, s'il est uniquement trouvé en tant que clé de `WeakMap` ou dans un `WeakSet` , il sera automatiquement nettoyé**.

## Destructuration en js :

[:question: :question:](destructuration.md)

- **L'attribution de destructuration permet de modéliser un `object` ou un `array` sur de nombreuses variables**.

- **Syntaxe `object` => `let {propriété : nom de variable = défaut,...rest} = object`**.

_La `propriété` doit aller dans la variable `nom de variable` et que, si aucune propriété de ce type n'existe, la valeur `défaut` doit être utilisée_.

_Les propriétés d'objet sans modélisation sont copiées dans l'objet `rest`_.

- **Syntaxe `array` => `let [element1 = défaut, element2, ...rest] = array`**.

_Le premier élément va à `element1` ; le second passe à `element2`, tout le reste se met dans un tableau `rest`_.

- **Il est possible d'extraire des données de tableaux/ objets imbriqués, car le côté gauche doit avoir la même structure que le côté droit**.

## `Recursion` et `stack` :

[:question: :question:](recursionAndStack.md)

- **`Recursion` => Terme de programmation qui signifie appeler une fonction à partir de lui-même. Les fonctions récursives peuvent être utilisées pour résoudre des tâches de manière élégante**.

- **`recursion step` => Lorsqu'une fonction s'appelle elle-même. La base de la récursivité est constituée par les arguments de la fonction qui rendent la tâche si simple que la fonction ne fait plus d'appels**.

- **Une structure de données définie de manière récursive => Structure de données qui peut être définie à l'aide de celle-ci**.

- **Toute fonction récursive peut être réécrite en une fonction itérative. Et c'est parfois nécessaire pour optimiser les choses. Mais pour de nombreuses tâches, une solution récursive est assez rapide et plus facile à écrire et à supporter**.

## `Rest parameters` et `spread operator` :

[:question: :question:](spreadOperatorAndRestParameters.md)

- **Quand on voit `...` dans le code , 2 choix s'offrent à nous :** - **Quand `...` est à la fin du paramètre de la fonction => c'est appeler `rest parameters` et rassemble le reste de la liste des arguments dans un tableau.** - **Quand `...` se fait à la fin d'une appel de fonction ou similaire => c'est appeler `spread operator` et étend un tableau dans une liste.**
- **`Rest parameters` => Utilisés pour créer des fonctions acceptant un nombre quelconque d'arguments.**
- **`Spread operator` => Utilisé pour passer un tableau à des fonctions nécessitant normalement une liste d'arguments.**

- **À deux, ils permettent de voyager facilement entre une liste et un tableau de paramètres.**

## Closure :

[:question: :question:](closure.md)

Deux types de variables :

- **Variable globale.**
- **Variable locale.**

Environnement lexical :

- **Environnement Record (Enregistrement d'Environnement).**
- **Une référence à l'environnement lexical externe, celui associé au code externe.**

Quand on créer une fonction , deux environnement lexicaux se crée :

- **L'environnement interne.**
- **L'environnement externe.**

- **Lorsque le code veut accéder à une variable, l'environnement lexical interne est recherché en premier, puis l'environnement externe, puis l'environnement externe et ainsi de suite jusqu'à l'environnement global.**
- **Une fonction obtient les variables externes telles qu'elles sont maintenant, elle utilise les valeurs les plus récentes.**
- **Un appel-un environnement lexical => Une nouvelle fonction Environnement lexical est créée à chaque exécution d'une fonction. Et si une fonction est appelée plusieurs fois, chaque appel aura son propre environnement lexical, avec des variables locales et des paramètres spécifiques à cette exécution.**
- **Closure => Qui se souvient automatiquement de l'endroit où ils ont été créés à l'aide d'une propriété `[[Environment]]` cachée, et tous peuvent accéder aux variables externes. (Fonctions qui a accès a des variables externes)**
- **Un environnement lexical est créé lors de l’exécution d’un bloc de code (exactement pareil qu'une fonction) et contient des variables locales au bloc.**
- **Un environnement lexical est nettoyé et supprimé après l'exécution de la fonction ou du bout de code.**

## Différence entre `let` et `var` :

[:question: :question:](letVsVar.md)

**Deux différences principales entre `var` et `let`(/`const`) :**

- **Les variables `var` n'ont pas de portée de bloc, elles sont visibles au minimum au niveau de la fonction.**
- **Les déclarations var sont traitées au démarrage de la fonction (démarrage du script pour les globals).**

## Objet global :

[:question: :question:](globalObject.md)

- **L'objet global contient des variables qui devraient être disponibles partout.** _Ceci inclut les objets natifs de JS, tels que `Array` et des valeurs spécifiques à l'environnement, comme `window.innerHeight` - l'hauteur de la fenêtre dans le navigateur._
- **L'objet global porte un nom universel `globalThis`.** _…Mais il est plus souvent appelé par des noms spécifiques à l’environnement de la vieille école, comme `window` (navigateur) et `global` (Node.js). Comme `globalThis` est une proposition récente._
- **On doit seulement stocker des valeurs dans l'objet global si elles sont réellement globales pour un projet. Et on garde la quantité de ces valeurs à un minimum.**
- **Dans les navigateurs, à moins qu'on utilise des modules, les fonctions et variables globales déclarées avec `var` deviennent une propriété de l'objet global.**
- **Pour que nos code soit à l'épreuve du temps et plus facile à comprendre, on doit accéder les propriétés de l'objet global directement, en utilisant `window.x`.**

## L'objet Function, EFN :

[:question: :question:](objetFunction.md)

- **Les fonctions sont des objets.**

- **On as couvert leurs propriétés :**

* **`name` => le nom de la fonction. Habituellement tiré de la définition de la fonction, mais s'il n'en existe pas, JS essaie de le deviner à partir du contexte(par exemple, une affectation).**
* **`length` => le nombre d'arguments dans la définition de la fonction. Les `rest parameters` ne sont pas comptés.**

- **Si la fonction est déclarée en tant qu'expression de fonction et qu'elle porte `name`, elle est appelée expression de fonction nommée. Le nom peut être utilisé à l'intérieur pour se référencer, pour des appels récursifs ou autres.**

- **Les fonctions peuvent avoir des propriétés supplémentaires. De nombreuses bibliothèques JS bien connues font bon usage de cette fonctionnalité.**
