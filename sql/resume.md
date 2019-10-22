# SQL :

## Base de données :

[:question: :question:](baseDonnees.md)

- **Une base de données est un endroit où l'on peut :**

- **Stocker de la données**.
- **Manipuler de la données**.
- **Récupèrer de la données**.

## `SQL` :

[:question: :qestion:](sql.md)

- **Structured Query Language.**
- **Syntaxe :**

```
SELECT prénom FROM personne
       Nom COLONNE Nom TABLEAU
```

- **Il gére les données contenues dans une base de données relationnelle.**

- **La donnée est stocké dans des tableaux.**
- **Ce même tableau est composé de :**
  - **Colonne**
  - **Ligne**

## `PostgreSQL` :

[:question: :question:](postgresql.md)

- **C'est un système de gestion de base de données relationnelle-objet.**

- **Pour ouvrir `postgreSQL` :**

```
sudo -u postgres psql
```

## Création/Suppression de comptes utilisateurs :

[:question: :question:](creerSupp.md)

```
CREATE USER nom_utilisateur;
```

```
DROP USER nom_utilisateur;
```

## Création/Suppression de bases de données :

[:question: :question:](creerSuppDd.md)

```
CREATE DATABASE nom_db;
```

```
DROP DATABASE nom_db;
```

## Rôles dans `PostgreSQL` :

[:question: :question:](roles.md)

```
CREATE ROLE nom_utilisateur;
```

```
DROP ROLE nom_utilisateur;
```

- **Il y a plusieurs attributs pour les rôles :**

  - **droit de connexion =>**

  ```
  CREATE ROLE nom LOGIN;
  CREATE USER nom;
  ```

  - **status de superutilisateur=>**

  ```
  CREATE ROLE nom SUPERUSER;
  ```

  - **création de bases de données =>**

  ```
  CREATE ROLE nom_utilisateur CREATEDB;
  ```

  - **création de rôle =>**

  ```
  CREATE ROLE nom CREATEROLE;
  ```

  - **mot de passe =>**

  ```
  CREATE ROLE nom_utilisateur PASSWORD 'mot_de_passe'
  ```

- **On peut lui ajouter et lui supprimer des membres en utilisant les commandes :**

```
GRANT role_groupe TO role1,...;
REVOKE role_groupe FROM role1,...;
```
