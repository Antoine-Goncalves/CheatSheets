# Agir sur une base de données

Pour retrouver une information d'une base de données, il faut :

```
SELECT nom_colonne FROM nom_table WHERE nom_colonne='valeur que l'on veut'
```

Pour trier les résultats, il faut :

```
SELECT * FROM nom_table ORDER BY nom_colonne (ASC ou DESC pour croissant ou décroissant)
```

Pour extraire les données distinctes, il faut :

```
SELECT DISTINCT nom_colonne
FROM nom_table
```

Pour retrouver une information selon des conditions précises, il faut :

```
SELECT * FROM nom_table WHERE nom_colonne='valeur que l'on veut' (possibilité de rajouter AND et/ou OR suivi nom_colonne='valeur que l'on veut')
```
