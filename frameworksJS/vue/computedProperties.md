# Intérêt des `computed properties` :

Les expressions sont uniquement destinées à des opérations simples.

Exemple:

```
<div id="example">
  <p>Message original : "{{ message }}"</p>
  <p>Message inversé calculé : "{{ reversedMessage }}"</p>
</div>

var vm = new Vue({
  el: '#example',
  data: {
    message: 'Bonjour'
  },
  computed: {
    // un accesseur (getter) calculé
    reversedMessage: function () {
      // `this` pointe sur l'instance vm
      return this.message.split('').reverse().join('')
    }
  }
})
```

Vous pouvez lier des données aux `computed properties` dans les templates comme une propriété normale. Vue est au courant que `vm.reversedMessage` dépend de `vm.message`, donc il mettra à jour toutes les liaisons qui dépendent de `vm.reversedMessage` lorsque `vm.message` changera. Ce qui est cool c'est qu'on as créé cette relation de dépendance de façon déclarative : la fonction de l’accesseur calculé n’a pas d’effets secondaires, ce qui la rend facile à tester et à raisonner.

Les `computed properties` dans `computed` sont mises en cache selon leurs dépendances.

Vue fournit une façon plus générique d'observer et de réagir aux changements de données sur une instance de Vue: les propriétés `watch`.

Les propriétés calculées ont par défaut uniquement un accesseur, mais on peut également fournir un mutateur (setter) quand on en a besoin
