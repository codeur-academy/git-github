

## Travail de gestion de version


## Les systèmes de gestion de version locaux

<!-- g layout : 12-2 12-7 p-40 -->

La méthode courante pour la gestion de version est généralement de recopier les fichiers dans le même répertoire ou dans un autre répertoire.
   
![recopier les fichiers dans le même répertoire](../images/slides/gestion-version/gestion-historique-modification.png)
*Recopier les fichiers dans le même répertoire*

<!-- note --> 

Cette méthode est la plus courante parce que c'est la plus simple, mais c'est aussi la moins fiable. Il est facile d'oublier le répertoire dans lequel vous êtes et d'écrire accidentellement dans le mauvais fichier ou d'écraser des fichiers que vous vouliez conserver.

<!-- end note -->  

***

<!-- new slide -->

<!-- g layout : 12 p-30 -->

<!-- note --> 

Pour traiter ce problème, les programmeurs ont développé il y a longtemps des VCS locaux qui utilisaient une base de données simple pour conserver les modifications d'un fichier.

<!-- end note --> 

![gestion de version locale](../images/local.png)
*Gestion de version locale*

<!-- note --> 

Cet outil fonctionne en conservant des ensembles de patchs (c'est-à-dire la différence entre les fichiers) d'une version à l'autre dans un format spécial sur disque ; il peut alors restituer l'état de n'importe quel fichier à n'importe quel instant en ajoutant toutes les différences.

<!-- end note -->  

## Les systèmes de gestion de version centralisés

<!-- g layout : 12 p-30 -->

<!-- note -->

Le problème majeur que les gens rencontrent est qu'ils ont besoin de collaborer avec des développeurs sur d'autres ordinateurs.

Pour traiter ce problème, les systèmes de gestion de version centralisés CVCS (Centralized Version Control Systems) ont été développés.

<!-- end note -->

![Diagramme de gestion de version centralisée](../images/centralized.png)
*Gestion de version centralisée*

<!-- note -->

Ces systèmes mettent en place un serveur central qui contient tous les fichiers sous gestion de version, et des clients qui peuvent extraire les fichiers de ce dépôt central.

Pendant de nombreuses années, cela a été le standard pour la gestion de version.

<!-- end note -->



<!-- new slide -->

<!-- g layout : 6 6  -->

<!-- note -->

### Avantage et inconvénient

Ce schéma offre de nombreux avantages par rapport à la gestion de version locale.

<!-- end note -->

Avantage

- Par exemple, chacun sait jusqu'à un certain point ce que tous les autres sont en train de faire sur le projet.
- Les administrateurs ont un contrôle fin des permissions et il est beaucoup plus facile d'administrer un CVCS que de gérer des bases de données locales.

<!-- note -->

Cependant, ce système a aussi de nombreux défauts.Le plus visible est le [point de défaillance unique](https://fr.wikipedia.org/wiki/Point_de_d%C3%A9faillance_unique) que le serveur centralisé représente.

<!-- end note -->

<!-- new zone -->

Inconvénient

- Si ce serveur est en panne pendant une heure, alors durant cette heure, aucun client ne peut collaborer ou enregistrer les modifications issues de son travail.

<!-- note -->

- Si le disque dur du serveur central se corrompt, et s'il n'y a pas eu de sauvegarde, vous perdez absolument tout de l'historique du projet en dehors des sauvegardes locales que les gens auraient pu réaliser sur leurs machines locales.

Les systèmes de gestion de version locaux souffrent du même problème — dès qu'on a tout l'historique du projet sauvegardé à un endroit unique, on prend le risque de tout perdre.

<!-- end note -->

## Les systèmes de gestion de version distribués

<!-- g layout : 12  -->

<!-- note -->

C'est à ce moment que les systèmes de gestion de version distribués DVCS (Distributed Version Control Systems) entrent en jeu.

Dans un DVCS (tel que Git), les clients n'extraient plus seulement la dernière version d'un fichier, mais ils dupliquent complètement le dépôt. De cette façon, si le serveur disparaît et si les systèmes des clients collaboraient via ce serveur, n'importe quel dépôt d'un des clients peut être copié sur le serveur pour le restaurer.

Chaque extraction devient une sauvegarde complète de toutes les données.

<!-- end note -->

![Gestion de version distribuée](../images/distributed.png)
*Gestion de version distribuée*

