# SQL

## Base de données

[:question: :question:](baseDonnee.md)

**Une base de données est un endroit où l'on peut :**

- **Stocker de la données**.
- **Manipuler de la données**.
- **Récupèrer de la données**.

## `SQL`

[:question: :question:](sql.md)

- **Structured Query Language.**
- **Syntaxe :**

```javascript
SELECT prénom FROM personne
       Nom COLONNE Nom TABLEAU
```

- **Il gére les données contenues dans une base de données relationnelle.**
- **La donnée est stocké dans des tableaux.**
- **Ce même tableau est composé de :**
- **Colonne**
- **Ligne**

## `PostgreSQL`

[:question: :question:](postgresql.md)

- **C'est un système de gestion de base de données relationnelle-objet.**
- **Pour ouvrir `postgreSQL` :**

```javascript
sudo -u postgres psql
```

## Création/Suppression de comptes utilisateurs

[:question: :question:](creerSupp.md)

```javascript
CREATE USER nom_utilisateur;
```

```javascript
DROP USER nom_utilisateur;
```

## Création/Suppression de bases de données

[:question: :question:](creerSuppDd.md)

```javascript
CREATE DATABASE nom_db;
```

```javascript
DROP DATABASE nom_db;
```

## Rôles dans `PostgreSQL`

[:question: :question:](roles.md)

```javascript
CREATE ROLE nom_utilisateur;
```

```javascript
DROP ROLE nom_utilisateur;
```

- **Il y a plusieurs attributs pour les rôles :**
- **droit de connexion =>**

```javascript
CREATE ROLE nom LOGIN;
CREATE USER nom;
```

- **status de superutilisateur=>**

```javascript
CREATE ROLE nom SUPERUSER;
```

- **création de bases de données =>**

```javascript
CREATE ROLE nom_utilisateur CREATEDB;
```

- **création de rôle =>**

```javascript
CREATE ROLE nom CREATEROLE;
```

- **mot de passe =>**

```javascript
CREATE ROLE nom_utilisateur PASSWORD 'mot_de_passe'
```

- **On peut lui ajouter et lui supprimer des membres en utilisant les commandes :**

```javascript
GRANT role_groupe TO role1,...;
REVOKE role_groupe FROM role1,...;
```

## Différence entre le `SQL` et le `NoSQL`

[:question: :question:](sqlVsNosql.md)

- **`SQL` =>**
- **Bases de données relationnelle.**
- **Basées sur les tables.**
- **Schéma prédéfini.**
- **Évolutives verticalement.**
- **`NoSQL` =>**
- **Bases de données non relationnelle.**
- **Basées sur des paires clés-valeurs.**
- **Schéma dynamique pour les données non structurées.**
- **Évolutives horizontalement.**

## Les types numériques :

[:question: :question:](typesNumeriques.md)

- **3 principaux =>**
- **`INT` => Entier signé sur 4 octets.**
- **`NUMERIC` => Nombre exact dont la précision peut être spécifiée.**
- **`SERIAL` => Entier sur 4 octets à incrémentation automatique.**

## Les types chaînes de caractères :

[:question: :question:](typesChaines.md)

- **3 types =>**
- **`CHAR` => Longueur fixe, complété par des espaces.**
- **`VARCHAR` => Longueur variable avec limite.**
- **`TEXT` => Longueur variable illimitée.**

## Les types dates :

[:question: :question:](typesDates.md)

- **3 types =>**
- **`TIME` => Stocke les dates uniquement au format AAAA-MM-JJ.**
- **`DATE` => Stocke les valeurs de l'heure du jour au format HH:MM:SS.**
- **`TIMESTAMP` => Stocke les valeurs de date et d'heure.**

## Autres :

[:question: :question:](autres.md)

- **3 valeurs =>**
- `true`. (vrai)
- `false`. (faux)
- `null`. (inconnu)
- **Créer des types `ENUM` :**

```javascript
CREATE TYPE humeur AS ENUM ('triste', 'ok', 'heureux');
```

## Restaurer une base de données :

[:question: :question:](restaurerBaseDeDonnees.md)

- **Restaurer une base de données =>**

```javascript
\i chemin_du_fichier (aller dans le fichier puis faire pwd pour avoir le chemin)
```

- **Restaurer le schéma d'une base de donnée uniquement =>**

```javascript
\d nom_du_fichier
```

- **Retrouver une ou plusieurs tables d'une base de données =>**

```javascript
SELECT * FROM nom_du_fichier

SELECT nom_colonne FROM nom_du_fichier
```

## Agir sur une base de données

[:question: :question:](agirSurBaseDeDonnes.md)

- **Retrouver une information d'une base de données =>**

```javascript
SELECT nom_colonne FROM nom_table WHERE nom_colonne='valeur que l'on veut'
```

- **Trier les résultats d'une base de données =>**

```javascript
SELECT DISTINCT nom_colonne FROM nom_table ORDER BY nom_colonne (ASC ou DESC pour croissant ou décroissant)
```

- **Extraire les données distinctes =>**

```javascript
SELECT DISTINCT nom_colonne
FROM nom_table
```

- **Retrouver une information selon des conditions précises =>**

```javascript
SELECT * FROM nom_table WHERE nom_colonne='valeur que l'on veut' (possibilité de rajouter AND et/ou OR suivi nom_colonne='valeur que l'on veut')
```
