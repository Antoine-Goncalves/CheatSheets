# Les évènements basés sur le clavier

## `keydown` et `keyup`

**Les événements `keydown` se produisent quand une touche est enfoncée, puis `keyup` quand elle est relâchée**.

### `event.code` et `event.key`

La propriété `key` de l'objet `event` permet d'obtenir le caractère, tandis que la propriété `code` de l'objet `event` permet d'obtenir le «code de clé physique».

Exemple:

La touche `Z` peut être enfoncée avec ou sans `Maj`. Cela nous donne deux caractères différents: `z` minuscule et `z` majuscule.

**`event.key` => `z` / `Z`** tandis que **`event.code` => KeyZ pour les deux**.

Chaque touche a un code qui dépend de son emplacement sur le clavier :
* **Les lettres => "Key<lettre>"**.
* **Les nombres => "Digit<nombre>"**.
* **Touches spéciales => par leurs noms**.

Quand choisir l'un ou l'autre ?

**Si on veut gérer des clés dépendantes de la disposition => `event.key`**.

**Si on veut un raccourci clavier même après un changement de langue => `event.code`**.

## Répétition automatique

Si une touche est enfoncée longtemps, elle se répéter automatiquement: `keydown` se déclenche encore et encore, et lorsqu'elle se relâche, on obtient enfin `keyup` . Pour les événements déclenchés par répétition automatique, la propriété `event.repeat` objet événement est définie sur `true` .

## Actions par défaut

Les actions par défaut varient, car de nombreuses actions peuvent être initiées par le clavier.

* **Un caractère apparaît à l'écran (résultat le plus logique)**.
* **Un caractère est supprimé => `Suppr`.**
* **La page défile => `PageDown`**.
* **Le navigateur ouvre le dialogue "Enregister la page" => `Ctrl + S`**.
* **Etc...**
