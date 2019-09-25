# La destructuration en Javascript :

Les 2 structures de données les plus utilisées en js sont `Object` et `Array`.

**`Object` permet de créer une entité unique qui stocke des données d'éléments par clés, et `array` permet de recueillir des données d'élements dans une collection ordonée**.

**L'assignement de destructuration est une syntaxe spéciale qui permet de "débaler" un `array` ou un `object` dans un bouquet de variables.**

*La destructuration fonctionne bien avec les fonctions complexes qui ont beaucoup de paramètres, des valeurs par défaut, et plein d'autres.*

## Destructuration d'un `array` :

Exemple:

```
let arr = ["Antoine","Gonçalves"];
let [prenom,nom] = arr;

alert(prenom);	// Affiche Antoine.
alert(nom);	// Affiche Gonçalves.
```

*Note: "Destructuration ne veut pas dire "destructive", car il copie les élements dans des variables. Mais `array` lui-même n'est pas modifié.*

Si on veut obtenir les premières valeurs, mais également toute la suite, on peut ajouter un paramètre supplémentaire en utilisant `...rest`.

La valeur de `rest` est un `array` des éléments restants. Peut importe le nom qu'on lui donne , ne pas oublier les `...` c'est le plus important.

Une valeur par défaut peut-être ajoutée , si aucune valeur n'est définie. en utilisant `=`.

```
let [prenom = "Invité",nom = "Anonyme"] = ["Antoine"];

alert(prenom);	// Antoine car pris dans le tableau qu'on traite.
alert(nom);	// Anonyme (valeur par défaut).
```

## Destructuration d'un `Object` :

Elle fonctionne aussi avec les objets. La syntaxe de base est : `let {var1, var2} = {var1:..., var2...}`

Exemple:

```
let options = {
	titre: "Menu",
	largeur: 100,
	hauteur: 200,
};

let {titre, largeur, hauteur} = options;

alert(titre);	// Menu.
alert(largeur);	// 100.
alert(hauteur);	// 200.
```

Sachant que les propriétés `options.titre`, `options.largeur` et `options.hauteur` sont assignées à leurs variables correspondantes. L'ordre où on les appellent importe peu.

On peut modifier si on veut les variables mais pour ça il faut utiliser une syntaxe particulière: `{ source de la propriété: nom de variable ciblée}`.

Exemple:

```
let {largeur: l, hauteur: h, titre} = options;

alert(title);	// Menu.
alert(l);	// 100.
alert(h);	// 200.
```

Pour mettre en défaut , même chose que `array`, utiliser `=`.

## Destructuration imbriquée :

Si un `object` ou `array` contient d'autres objets ou tableaux imbriqués, on peut également faire le même principe qu'avant.

## Paramètres de la fonction intelligente :

Il arrive parfois qu'une fonction comporte de nombreux paramètres, dont la plupart sont facultatifs.

La syntaxe complète est la même que pour une affectation de déstructuration : `function({ propriété entrante: nom de variable = valeur de défaut ...})`.
