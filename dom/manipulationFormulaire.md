# Manipulation des formulaires dans le `DOM`

Les formulaires et les éléments de contrôle, tels que `<input>` possèdent de nombreuses propriétés et événements spéciaux.

## Navigation : `form` et `elements`

Les formulaires de document sont membres de la collection spéciale `document.forms`.

C'est ce qu'on appelle une "collection nommée": c'est à la fois nommé et ordonné. On peut utiliser le nom ou le numéro du document pour obtenir le formulaire.

- **`document.forms.nom` => `form` avec le name="nom"**.
- **`document.forms[0]` => le premier `form` dans le document**.

Lorsqu'on as un formulaire, tout élément est disponible dans la collection nommée `form.elements`.

Il peut y avoir plusieurs éléments qui ont le même nom, ce qui est souvent le cas avec les boutons `radio`.

**Dans ce cas, `form.elements[name]` est une collection**.

**Notation plus courte => au lieu de `form.elements.login` --> `form.login`**.

## Référence arrière : `element.form`

Pour tout élément, le formulaire est disponible sous la forme `element.form`. Ainsi, un formulaire fait référence à tous les éléments, et les éléments font référence au formulaire.

## `Form elements`

`input` et `textarea` :

On peut accéder à leur valeur comme `input.value` (chaîne) ou `input.checked`(booléen) pour les cases à cocher.

_Note: On utilise `textarea.value`, pas `textarea.innerHTML`_.

`select` et `option` :

L'élément `<select>` a 3 propriétés importantes:

1.  **`select.options` => la collection de sous-éléments `<option>`**.
2.  **`select.value` => la valeur de `<option>` actuellement sélectionnée**.
3.  **`select.selectedIndex` => le numéro de `<option>` actuellement sélectionnée**.

3 façons de définir la valeur d'un `<select>`, qui font la même chose:

1.  Recherche l'élément `<option>` correspondant et définit `option.selected` sur `true`.
2.  Définit `select.value` sur la valeur.
3.  Définit `select.selectedIndex` sur le numéro de l'option.

## `new Option`

Il existe une syntaxe pour créer des éléments `<option>` :

```javascript
option = new Option(text, value, defaultSelected, Selected);
```

Paramètres:

- **`text` => le texte à l'intérieur de l'option**.
- **`value` => l'option `value`**.
- **`defaultSelected` => si `true`, l'attribut HTML `selected` est crée**.
- **`selected` => si `true`, l'option est sélectionnée**.

Les éléments d'option ont des propriétés:

- **`option.selected` => l'option est-ele sélectionnée?**.
- **`option.index` => le numéro de l'option parmi les autres dans ses `<select>`**.
- **`option.text` => contenu textuel de l'option (vu par le visiteur)**.
