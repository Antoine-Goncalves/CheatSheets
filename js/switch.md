# Fonctionnement de `switch`

La déclaration `switch` peut remplacer plusieurs `if`. Cela donne une manière plus descriptive pour comparer plusieurs variantes avec une valeur.

Le `switch` a une ou plusieurs `case` (blocs) et un défaut opptionnel.

Syntaxe =>

```javascript
switch(x) {
    case 'valeur1': // if (x === 'valeur1)
        ...
        break;
    case 'valeur2': // if (x === 'valeur2)
        ...
        break;
    ...
    default:
        break;
}
```

-   La valeur de `x` est vérifiée avec une égalité stricte pour la valeur du premier `case`, puis le second et ainsi de suite..
-   Si l'égalité est trouvée, `switch` commence à exécuter le code en commençant par le `case` correspondant, jusqu'au `break` le plus proche (ou jusqu'à la fin du `switch`).
-   Si aucune `case` est bonne, alors `default` est exécuté (si il existe).

_Note: :heavy_exclamation_mark: Si il n'y a pas de break, alors l'exécution continuera. :heavy_exclamation_mark:_

Groupement de `case` :

Plusieurs variante de `case` peuvent partager le même code.

Syntaxe =>

```javascript
switch (a) {
    case 4:
        alert('Vrai');
        break;

    case 3:
    case 5:
        alert('Faux');
}
```

l'aptitude à groupé les `cases` est un effet secondaire. Car il n'y a pas de pause.
