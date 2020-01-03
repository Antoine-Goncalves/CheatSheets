# Les types chaînes de caractères

**`PostgreSQL` fournit trois types de données de caractères :**

- `CHAR(n)` est le caractère de longueur fixe avec espace complété. Si on insére une chaîne plus courte que la longueur de la colonne, `PostgreSQL` comble les espaces. Si on insére une chaîne plus longue que la longueur de la colonne, `PostgreSQL` émettra une erreur.
- `VARCHAR(n)` est la chaîne de caractères de longueur variable. Avec `VARCHAR(n)` , on peut stocker jusqu'à `n` caractères. `PostgreSQL` ne remplit pas les espaces lorsque la chaîne stockée est plus courte que la longueur de la colonne.
- `TEXT` est la chaîne de caractères de longueur variable. Théoriquement, les données de texte sont une chaîne de caractères avec une longueur illimitée.
