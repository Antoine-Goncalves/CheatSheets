# Polyfills et leur utilité :

Le langage JavaScript évolue constamment, de nouvelles propositions aux langages apparaissent régulièrement, ils sont analyser et, si elles sont considèrer louable, elles sont ajoutés à la liste ECMA262 et proposé dans la spécification. L'équipe dérierre JavaScript imagine leurs propres idées pour implémenté en premier. Ils décident d'implémenter des propositions d'idée vu avec des équipes et reporté des choses qui sont déjà dans la spécification, car moins intéressant ou juste difficile à faire.

Donc c'est assez commun par un moteir d'implémenter seulement la partie du standard. (la norme).

# Unité de Babel :

Quand on utilise les caractéristiques moderne d'un langage, certain moteur ne supporte pas le code. Toutes les caractéristiques ne sont pas implémenter partout. C'est la que Babel vient à la rescousse.

**Babel est un transpilateur**. Il réecrit le code moderne JavaScript dans la norme précédente. Actuellement, il y a 2 parties dans Babel :

- Le programme de transpilation, qui réecris le code. Le développeur met en route son ancien pc, il réecrit du code dans l'ancienne norme. Puis le code est délivré au site pour les utilisateurs. Des projets modernes construit des systèmes (ex: webpack) qui permet de transpiler automatiquement à chaque changement de code.
