# Concentration : `focus` et `blur` :

Un élément reçoit une concentration (`focus`) soit quand l'utilisateur clique dessus ou alors en utilisant la touche `Tab` du clavier. Il existe également un attribut HTML `autofocus` qui place la concentration dans un élément par défaut lors du chargement d’une page, ainsi que d’autres moyens d’obtenir une mise au point.

**La concentration d'un élément signifie généralement: "prépare à accepter de la donnée ici"**.

Le moment où l'on perds la concentration (`blur`) peut être encore plus important. C'est quand l'utilisateur clique autre part ou entrer `Tab` pour aller au champ de formulaire suivant.

**Perdre la concentration signifie généralement: "la donnée a été entré"**.

## Événements `focus` et `blur` :

L'événement `focus` est appellé quand l'élément est concentré, et `blur` quand l'élément perd la concentration.

## Méthodes `focus` et `blur` :

Les méthodes `elem.focus()` et `elem.blur()` active/désactive la mise au point sur l'élément.

## Permet de se concentrer sur n'importe quel objet => `tabindex` :

Par défaut plusieurs éléments ne supporte pas la concentration.

Ça change en fonction des navigateurs, mais une chose est toujours correct: `focus` et `blur` fonctionne avec les éléments ou le visiteur peut interagir: `<button>`, `<input>`, `<select>`, `<a>` et plein d'autre...

D'une autre part, les éléments qui existe pour formater quelque chose, comme `<div>`,`<span>`,`<table>` sont non concentré par défaut.

**La méthode `elem.focus()` ne fonctionne pas sur eux, et les événements `focus` et `blur` sont jamais déclenché**.

**On peut concentré n'importe quel élément avec `tabindex`. La valeur de l'attribut est l'ordre du numéro de l'élément quand `Tab` est utilisé pour changer entre eux**.

Il y a 2 valeurs spéciales :

* **`tabindex = "0"` met un élément parmi ceux sans `tabindex`. C'est à dire que si on change d'éléments, les éléements avec tabindex = "0" vont au numéro suivant (tabindex >=1)**.

* **`tabindex = "-1"` permet uniquement de se concentré programmatique sur un élément. La touche `Tab` ignore ces éléments, mais la méthode `elem.focus()` fonctionne**.

## Délégation: `focusin` et `focusout` :

Les événements `focus` et `blur` ne font pas `bubble`.

Deux moyens pour y remédier :

1. **`focus` et `blur` ne font pas `bubble`, mais se propage à la phase de capture.**
2. **Il y a des événements de `focusin` et de `focusout` => exactement les mêmes que ceux de `focus` et `blur` , mais ils font `bubble`.

*Note: Ils doit être assignés en utilisant `elem.addEventListener` , pas `on<event>`*.
