# Polyfills et leur utilité :

Le langage JavaScript évolue constamment, de nouvelles propositions aux langages apparaissent régulièrement, ils sont analyser et, si elles sont considèrer louable, elles sont ajoutés à la liste ECMA262 et proposé dans la spécification.

L'équipe dèrierre JavaScript imagine leurs propres idées pour implémenté en premier. Ils décident d'implémenter des propositions d'idée vu avec des équipes et reporté des choses qui sont déjà dans la spécification, car moins intéressant ou juste difficile à faire.

Donc c'est assez commun par un moteur d'implémenter seulement la partie du standard. (la norme).

# Unité de Babel :

Quand on utilise les caractéristiques moderne d'un langage, certain moteur ne supporte pas le code. Toutes les caractéristiques ne sont pas implémenter partout. C'est la que Babel vient à la rescousse.

**Babel est un transpilateur**. Il réecrit le code moderne JavaScript dans la norme précédente. Actuellement, il y a 2 parties dans Babel :

-   Le programme de transpilation, qui réecris le code. Le développeur met en route son ancien pc, il réecrit du code dans l'ancienne norme. Puis le code est délivré au site pour les utilisateurs. Des projets modernes construit des systèmes (ex: webpack) qui permet de transpiler automatiquement à chaque changement de code.

Vient ensuite les polyfills :

Les nouvelles fonctionnalités de langages permettent d'inclure des nouvelles fonctions et des constructions de syntaxe. **Le transpilateur réecrit le code, transforme la structure des syntaxes dans les anciennes**. Mais pour les nouvelles fonctions créer, on as besoin de les implémenter.

Le Javascript est un langage hautement dynamique, les scripts peuvent ajouter/modifier n'importe quelles fonctions, donc il s'accorde au moderne standard. Un script qui met à jour/ajouter des nouvelles fonctions est appellés "polyfill". Il "comble le vide et ajoute des implémentations.

Il y a 2 intéressant polyfills :

-   Core.js qui supporte beaucoup, permet d'inclure unique les fonctionnalités utile.
-   Polyfill.io, c'est un service qui fournit un script avec des polyfills, en fonction des fonctionnalités d'un langage moderne, un transpilateur et un polyfill sont nécessaire.
