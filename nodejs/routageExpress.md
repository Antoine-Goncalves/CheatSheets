# Routage de base :

**Le routage** consiste à déterminer comment une application répond à une demande client adressée à un point de terminaison particulier, à savoir un URI (ou chemin) et une méthode de requête HTTP spécifique (GET, POST, etc.).

Chaque route peut avoir une ou plusieurs fonctions de gestionnaire, qui sont excutées lorsque la route est appariée.

La définition d'itinéraire prend la structure suivante :

```
app.METHOD(PATH, HANDLER)
```

Où:

- `app` est une instance de `express`.
- `METHOD` est une méthode de requête HTTP, en minuscule.
- `PATH` est un chemin sur le seveur.
- `HANDLER` est la fonction exécutée lorsque la route est mise en correspondance.

Les exemples suivants montrent des itinéraires simples :

Répondre `Hello World!` sur la page d'accueil:

```
app.get('/', function (req, res) { res.send('Hello World!') })
```

Répondre à la demande `POST` sur la route racine ( / ), la page d'accueil de l'application:

```
app.post('/', function (req, res) { res.send('Got a POST request') })
```

Répondre à une demande `PUT` à la route /user :

```
app.put('/user', function (req, res) { res.send('Got a PUT request at /user') })
```

Répondre à une demande `DELETE` à la route /user :

```
app.delete('/user', function (req, res) { res.send('Got a DELETE request at /user') })
```
