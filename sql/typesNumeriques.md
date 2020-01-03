# Les types numériques

**Il existe trois types d'entiers dans `postgreSQL :**

-   Le petit entier `SMALLINT` est un entier signé de 2 octets compris entre -32 768 et 32 767.
-   Entier `INT` est un entier de 4 octets compris entre -2 147 483 648 et 2 147 483 647.
-   `SERIAL` est identique au nombre entier mais à incrémentation automatique.

**Il existe trois principaux types de nombres à virgule flottante:**

-   `float(n)` est un nombre à virgule flottante dont la précision, au moins n, peut atteindre 8 octets au maximum.
-   `real` ou `float8` est un nombre à virgule flottante de 4 octets.
-   `numeric` ou `numeric(p,s)` est un nombre réel avec p chiffres avec s nombre après le point décimal. Le `numeric(p,s)` est le nombre exact.
