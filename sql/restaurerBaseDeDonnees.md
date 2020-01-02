# Restaurer une base de données / schéma d'une base de donnée uniquement / une ou plusieurs tables d'une base de données

Avec `Mockaroo`, on peut générer une base de données.

Pour la restaurer, il faut télécharger la data, puis :

```javascript
\i chemin_du_fichier (aller dans le fichier puis faire pwd pour avoir le chemin)
```

Pour restaurer le schéma d'une base de donnée uniquement, il faut :

```javascript
\d nom_du_fichier
```

Pour pouvoir retrouver une ou plusieurs tables d'une base de données, il faut :

```javascript
SELECT * FROM nom_du_fichier

SELECT nom_colonne FROM nom_du_fichier
```
