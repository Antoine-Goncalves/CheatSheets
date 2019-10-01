# `rest parameters` et `spread operator` :

## `Rest parameters ...` :

Une fonction peut être appeller avec n'importe quel arguments, peut importe comment il est défini.

Le reste des paramètres peut être inclue dans une fonction entre utilisant 3 points `...` suivi du nom du paramètre (généralement les paramètres restants dans un tableau).

## La variable `arguments` :

Il existe également un objet spécial de type tableau nommé `arguments` qui contient tous les arguments en fonction de leur index. Mais l’inconvénient est que ce n’est pas un tableau. Il ne supporte pas les méthodes de tableau.

## `Spread operator` :

On as vu comment obtenir un tableau de la liste des paramètres, parfois on as besoin de faire exactement l'inverse. Si on utilise 3 points `...` au début, on étend alors un tableau dans une liste.
