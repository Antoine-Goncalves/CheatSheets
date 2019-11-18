# Fonctionnement des fonctions :

Quelques fois on as besoin d'effectuer des actions similaires dans plusieurs endroit du script. Les fonctions sont le principal "construction de block" du programme. Ils permmettent au code d'être appeller plusieurs fois sans répétition.

Des exemples de fonctions déjà faites, comme `alert(msg)`, `prompt(msg,défaut)` et `confirm(question)`. Mais on peut créer nos propre fonction.

## Fonction Déclaration :

Pour créer une fonction, on utilise la déclaration de fonction.

La syntaxe est :

```
function showMessage() {
    alert('Hello everyone!');
}
```

Le mot-clé `function` arrive en premier, suivi du nom de la fonction, puis la liste des paramètres entre parenthèses (les `,` les sépare) et enfin le code de la fonction, appellé "corps de la fonction" avec des accolades `{}`.

Pour exécuter une fonction, il faut juste l'appeller.

Exemple:

```
showMessage();
```

## Variables locales :

Une variable déclarée dans une fonction est visible que dans celle-ci.

## Variables externes :

Une fonction peut avoir accès au variables externes.

```
let userName = 'Antoine';
function showMessage() {
    let msg = 'Salut, ' + userName;
    alert(msg);
}
```

showMessage(); // Salut, Antoine

La fonction as accès total aux variables externes. Ils peuvent même les modifier.

Elle est utilisé que si il n'y a pas de variables locales !

## Paramètres :

On peut transmettre des données arbitraire à des fonctions en utilisant des paramètres (également appellé fonction arguments).

```
Exemple: function message (from, text) {
    alert(from + ':' + text);
}
message('Antoine','Salut'); // Antoine:Salut!
```

Les fonctions change les variables mais pas visible à l'extérieur, car copie.

## Valeurs par défaut :

Si le paramètre n'est pas nommé, alors la valeur est `undefined`.

Ce n'est pas une erreur. Il n'y a pas de text, donc `undefined`. Si on veut un texte par "défaut".

## Retourner une valeur :

Une fonction peut retourner une valeur dans le code en renvoyant le résultat.

```
Exemple: function sum(a,b) {
    return a+b;
}
sum(1,2);   //3
```

La directive `return` peut se placer n'importe où. Quand l'éxecution est atteint, la fonction stop, et la veleur retourne ce qu'il y a après `return`.

## Nommée une fonction :

Il faut être bref, aussi précis que possible et décrire ce qu'elle fait. Les fonctions qui commence par :

- "show..." => montre quelque chose. `Exemple : showMessage`
- "calc..." => calcule quelque chose. `Exemple : calcSum`
- "get..." => retourne une valeur. `Exemple : getAge`
- "create..." => créer quelque chose. `Exemple : createForm`
- "check..." => vérifier quelque chose et retourner un booléen, etc.. `Exemple : checkPermission`

## Fonctions == Commentaires :

Fonctions doit être
