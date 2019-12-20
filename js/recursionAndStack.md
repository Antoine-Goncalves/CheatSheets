# `recursion` et `stack`

**Recursion** est un programme de modélisation utile dans des situations où une tâche peut être naturellement divisée en plusieurs tâches du même type, mais plus simple.

Où quand une tâche peut-être simplifiée en une action facile plus une variante plus simple que la même tâche. Ou pour traiter avec certaines structures de données.

Quand une fonction résoud une tâche, dans un processus il peut appeler plusieurs fonctions. Un cas concret est quand une fonction s'appelle elle-même. Cela s'appelle `recursion`.

## 2 manières de penser

1. Pensée itérative : la boucle `for`.

Exemple:
```
function pow(x, n) {
  let result = 1;

  // multiply result by x n times in the loop
  for (let i = 0; i < n; i++) {
    result *= x;
  }

  return result;
}
```

2. Pensée récursive : simplifie la tâche et rappelle la fonction dans le code.

Exemple:
```
function pow(x, n) {
  if (n == 1) {
    return x;
  } else {
    return x * pow(x, n - 1);
  }
}
```

## Le contexte d'exécution et `stack`

Les informations sur le processus d'exécution d'une fonction en cours d'exécution sont stockées dans son contexte d'exécution.

Le contexte d'exécution est une structure de données interne qui contient les détails à propos de l'exécution d'une fonction. Un appel de fonction est associé à exactement un contexte d'exécution.

Quand une fonction effectue un appel imbriqué, cela produit :

*   La fonction en cours est stopée.
*   Le contexte d'exécution est associé et mémorisé dans une structure de données spéciale appelée contexte d'exécution `stack` .
*   L'appel imbriqué est exécuté.
*   Après tout ça, l'ancien contexte d'exécution est extrait du `stack`, et la fonction externe est reprend la où on l'as arrêtée.

**Toute récursion peut être réécrite sous forme de boucle. La variante de boucle peut généralement être rendue plus efficace**.

## Traversées récursive

On peut facilement voir le principe: pour `object {..}` des sous-appels sont effectués, alors que `array [..]` sont les "feuilles" de l'arbre de récurrence, ils donnent un résultat immédiat.

## Structures récursive

Une structure de données récursive (récursivité définie) est une structure qui se réplique en parties.

**L'élément de liste chainée** est récursivement définie comme un objet avec :

*   `value`.
*   propriété `next` référençant le prochain *élément de la liste chainée* ou `null` si c'est la fin.

Les listes peuvent être améliorées:

*   On peut ajouter la propriété `prev` en plus de `next` pour référencer l'élément précédent, pour revenir facilement en arrière.
*   On peut également ajouter une variable nommée `tail` qui référence le dernier élément de la liste (et la mettre à jour lors de l'ajout/la suppression d'éléments de la fin).
*   La structure des données peut varier en fonction de nos besoins.
