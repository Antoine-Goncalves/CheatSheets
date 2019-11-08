# Boucle : `while` et `for` :

On doit souvent répéter des actions, les boucles sont un moyen de répeter plusieurs code multpiles.

La boucle `while` => syntaxe :

```
while (condition) {
    // code
    // corps de boucle
}
```

Tant que la condition est vrai, le code du bosy est exécuté.

Une simple exécution de la boucle body est appelée une itération.

## La boucle `do..while`:

Syntaxe =>

```
do {
    // loop body
} while (condition);
```

La boucle vas exécuter le body en prémier, ensuite check la condition, et, si c'est vrai, exécute encore et encore.

Forme de syntaxe utilisé si la boucle body s'exécute au moins une fois.

## La boucle `for` :

La boucle `for` est plus complexe, mais c'est aussi le plus courramment utilisé.

Syntaxe =>

```
for (begin; condition; step) {
    // loop body
}
```

Rompre une boucle :

Normalement, une boucle se quitte quand les conditions deviennent fausses. Mais on peut forcer à quitter à n'importe qu'elle moment en utilisant qu'elle moment en utilisant la directive spéciale `break`. La combinaison "boucle infiny + rompre si besoin" est bien pour une situation ou la condition d'une boucle doit être vérifiée mais au début ou à la fin de la boucle, mais au milieu ou même à plusieurs endroits de son corps.

Continuer à la prochaine itération :

Le `continue` est une version légère de `break`. Il ne stop pas la boucle en entier. Au lieu de ça, il stop l'itération courue et force la boucle à commencer une autre (si la condition est permis)

Labels pour `break`/`continue` :

Parfois, on doit sortir de plusieurs boucles imbriquées en même temps. On as besoin d'un moyen d'arrêter le processus si l'utilisateur annule la saisie. Le `label` prend son sens ici.

Un `label` est un identifiant avec `:` avant une boucle :

Syntaxe =>

```
nomLabel: for(...){

}
```

La déclaration `break <nomLabel>` dans la boucle en dessous se décompose:

Exemple:

```
outer: for (let i=0; i<3; i++>) {
    for(let j=0; j<3; j++>) {
        let input = prompt(`Value (${i},${j}),'');
        if (!input) break outer;
    }
}
alert('Done !')
```
