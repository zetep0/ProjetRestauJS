# ProjetRestauJS
Projet du cours de techno web


Ceci est le projet que j'ai réalisé pour le cours de Technologies Web.

Un point remarquable de ce projet est l'utilisation de l'API google maps.
J'ai utilisé cette API pour afficher l'emplacement des restaurants sur la carte ainsi que pour montrer une photo des restaurants.
Pour l'affichage du restaurant sur la carte, il m'a fallu faire une iframe dans laquelle je passe en paramètre une source. Cette dernière contient un lien vers l'API, ainsi qu'une API key et les coordonnées du lieu que l'ont veut afficher.
Pour ce qui est des coordonnées, il m'a fallu faire une fonction pour les récupérées dans le bon ordre. Dans cette fonction, j'ai fait un split pour différencier la longitude de la latitude. J'ai ensuite créé deux variables dans lesquelles je place la longitude (l'élément 1 du tableau créé après le split) et la latitude (l'élément 0 du tableau créé par le split).
Pour ce qui est de l'image, le fonctionnement est exactement le même. La seul différence est le nom des paramètres présents dans la source.
