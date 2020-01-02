# Autres

## `BOOLEAN`

3 valeurs possibles :

-   `true`. (vrai)
-   `false`. (faux)
-   `null`. (inconnu)

On utilise le mot-clé `boolean` ou `bool` pour déclarer une colonne avec le type de données booléen.

## `ENUM`

Les types énumérés sont des types de données qui comprennent un ensemble statique, prédéfini de valeurs dans un ordre spécifique. Ils sont équivalents aux types `ENUM` dans de nombreux langages de programmation. Les jours de la semaine ou un ensemble de valeurs de statut pour un type de données sont de bons exemples de type `ENUM`.

Pour créer des types `ENUM` , on utilise la commande :

```javascript
CREATE TYPE humeur AS ENUM ('triste', 'ok', 'heureux');
```

Ils sont sensibles à la casse.
