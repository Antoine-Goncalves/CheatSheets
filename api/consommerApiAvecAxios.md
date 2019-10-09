# Utiliser Axios pour consommer des API :

Lors de la création d'une application Web, il est fréquent qu'on souhaite utiliser et afficher les données provenant d'une API. On vas utiliser le plus populaire ici , [axios](https://github.com/axios/axios), un client HTTP basé sur les Promesses.

On doit dans un premier temps installer axios :

```
npm install axios

```

Il existe plusieurs manières de demander quelque chose à une API, mais il est préférable de d'abord connaitre la structure des données qu'elle renvoie afin de savoir ce qu'elle va afficher.

On commence donc par créer une donnée qui gardera les informations que l'on veut, puis on récupere les données et on les attribue à l'aide de l'étape `mounted` du cylce de vie :

```
new Vue({
  el: '#app',
  data () {
    return {
      info: null
    }
  },
  mounted () {
    axios
      .get('lien de l'api avec les info total')
      .then(response => (this.info = response))
  }
})

<div id="app">
  {{ info }}
</div>
```

On obtient la donnée qui nous intéresse.

## Utilisation des données :

Il est courant que les informations dont on as besoin se trouvent dans la réponse, juste il faut trier et prendre l'essentiel de ce qui nous intéresse. Du coup il faut le préciser dans notre demande :

```
axios
  .get('lien de l'api avec les info total')
  .then(response => (this.info = response.data.clé qui nous intéresse))
```

## Travailler avec des erreurs :

Parfois, on ne peut recevoir de données de l'API. Il peut y avoir plusieurs raisons :

- L'API est hors-service.
- La requête a mal été réalisée.
- L'API ne nous donne pas les informations dans le format attendu.

Quand on créer une requête, on peut vérifier si il y a un bug et pouvoir être informer pour traiter le bug. Avec axios, on peut le faire en utilisant `catch`.

```
axios
  .get('https://api.coindesk.com/v1/bpi/currentprice.json')
  .then(response => (this.info = response.data.bpi))
  .catch(error => console.log(error))
```

Cela permet de voir si quelque chose a planté lors de la requête à l'API.

```
new Vue({
  el: '#app',
  data () {
    return {
      info: null,
      loading: true,
      errored: false
    }
  },
  mounted () {
    axios
      .get('adresse API')
      .then(response => {
        this.info = response.data.bpi
      })
      .catch(error => {
        console.log(error)
        this.errored = true
      })
      .finally(() => this.loading = false)
  }
})


<div id="app">
  <h1>Bitcoin Price Index</h1>

  <section v-if="errored">
    <p>Nous sommes désolés, nous ne sommes pas en mesure de récupérer ces informations pour le moment. Veuillez réessayer ultérieurement.</p>
  </section>

  <section v-else>
    <div v-if="loading">Chargement...</div>

  </section>
</div>
```
