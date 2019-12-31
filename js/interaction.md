# Interaction

3 types :

## `alert`

**Syntaxe => `alert(message);`**

Il affiche le message et met en "pause" jusqu'à temps qu'on presse `OK`, _la mini-fenêtre avec le message s'appelle une_ **fenêtre modale.** On ne peut rien faire sauf presser `OK`.

## `prompt`

**Syntaxe => `prompt(titre, [défaut]);`**

Il affiche une fenêtre modale avec un message texte, un champ de saisie pour les visiteurs, et les bouttons `Annuler` et `OK`.

argument `titre` : le texte montré par le visiteur.
argument `défaut` : le second paramètre optionnel, un champ de saisie pour les visiteurs.

Le visiteur à 2 choix, écrire quelque chose et taper `OK` ou `Annuler`.

_Note: On peut faire un défaut vide._

## `confirm`

Il affiche une fenêtre modale avec une question et 2 choix : `OK` ou `Annuler`. Le résultat est vrai si `OK`, faux sinon.
