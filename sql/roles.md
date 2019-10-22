# Rôles dans `PostgreSQL` :

Pour créer un rôle, on utilise la commande :

```
CREATE ROLE nom_utilisateur;
```

Pour supprimer un rôle existant, on utilise la commande :

```
DROP ROLE nom_utilisateur;
```

# Plusieurs attributs des rôles :

## droit de connexion :

Pour créer un rôle disposant du droit de connexion, on utilise la commande :

```
CREATE ROLE nom LOGIN;
CREATE USER nom;
```

_Note: `CREATE USER` est équivalent à `CREATE ROLE` sauf que `CREATE USER` utilise `LOGIN` par défaut alors que `CREATE ROLE` ne le fait pas_

## statut de superutilisateur :

Pour créer un nouveau superutilisateur, on utilise la commande :

```
CREATE ROLE nom SUPERUSER;
```

## création de bases de données :

Pour créer un tel rôle, on utilise la commande :

```
CREATE ROLE nom_utilisateur CREATEDB;
```

## création de rôle :

Pour créer un tel rôle, on utilise la commande :

```
CREATE ROLE nom CREATEROLE;
```

_Note: Un rôle disposant du droit `CREATEROLE` peut aussi modifier et supprimer d'autres rôles, ainsi que donner ou supprimer l'appartenance à ces rôles. Néanmoins, pour créer, modifier, supprimer ou changer l'appartenance à un rôle superutilisateur, le statut de superutilisateur est requis ; `CREATEROLE` n'est pas suffisant pour cela._

## initier une réplication :

Un rôle utilisé pour la réplication en flux doit avoir le droit LOGIN.

Pour créer un tel rôle, on utilise la commande :

```
CREATE ROLE nom REPLICATION LOGIN;
```

## mot de passe :

Pour créer cela, on utilise la commande :

```
CREATE ROLE nom_utilisateur PASSWORD 'mot_de_passe'
```

## Appartenance d'un rôle :

Il faut d'abord créer le rôle :

```
CREATE ROLE nom;
```

Pour détruire un rôle groupe, on utilise la commande :

```
DROP ROLE nom;
```

Une fois que ce rôle existe, on peut lui ajouter et lui supprimer des membres en utilisant les commandes :

```
GRANT role_groupe TO role1,...;
REVOKE role_groupe FROM role1,...;
```
