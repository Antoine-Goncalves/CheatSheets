# Opérateurs conditionnels : `→f` et `?` :

# L'opérateur `if` :

Le if(..) évalue une condition entre parenthèse et, si le résultat est `true`, il exécute un bloc de code.

Exemple :

```
let year = prompt('Quelle année somme-nous?','');
if (year==2019) alert('Exact!');
```

Si on veut exécuter plus d'une déclarations, on doit englober notre code dans {..}.

Il est recommandé, pour la visibilité, d'écrire entre {..} si on utilise l'opérateur `if`.

## Conversion Booléenne :

L'opérateur `if {..}` évalue l'expression entre parenthèses et convertie le résultat en booléen.

- _Le nombre 0, chaîne vide "", `null`, `undefined` and `NaN` deviennent `false`. Car ils sont appellées les valeurs fausses._
- _Toutes les autres valeurs deviennent `true`, et sont appelées les vrais_
