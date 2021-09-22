---
Weight: 20400
title: "Transformer les outils de comptes rendus"
date: 2021-07-16T11:03:00+02:00
lastmod: 2021-09-01T16:03:00+02:00
draft: false
cover: /img/scribe.png
author: LC
avatar: /dsi/lc.jpg
tags:
 - application
 - structure
categories:
 - application
---

SCRIBE est la nouvelle application unifiant tous les outils de compte rendu du
Sénat. Déjà en production pour les comptes rendus de commission, elle intégrera
les comptes rendus de séance publique prochainement. Elle permet,
avec l'abandon de Word, d'avoir
[une approche beaucoup plus structurée](/posts/structure) et donc plus fiable
pour mettre en valeur le travail des sénateurs sur le site du Sénat et dans le
_Journal Officiel_.

Quels outils ont-ils été utilisés pour sa réalisation ?
<!--more-->

## État des lieux

Jusqu’à présent, chaque type de compte rendu (compte rendu de commission, 
compte rendu analytique de séance, compte rendu intégral de séance) était
rédigé avec un modèle Word plus ou moins outillé et les pratiques divergeaient grandement entre les
différentes catégories d'utilisateurs. Par ailleurs, la technologie Visual Basic était un frein pour
répondre à des demandes d'automatisation et d'homogénéisation grandissantes.

Les objectifs du projet Scribe sont de :

- mettre en place un outil unique de compte rendu commun à l'ensemble des
comptes rendus tout en respectant les spécificités de chacun ;
- mieux intégrer  les comptes rendu dans le reste du
[SI](/posts/si/) (les comptes rendus peuvent exploiter des informations déjà
saisies ailleurs dans le SI et inversement) ;
- parvenir à une plus grande homogénéité entre les prises : les même cas de
séance doivent avoir le même rendu final ;
- rendre les documents plus accessibles (par exemple en terme HTML) et ce
faisant mieux mettre en valeur les comptes rendus et donc le travail du Sénat ;
- mettre en place une stack technique moderne et maintenable, plus centrée sur
les compétences de la DSI.

## Organisation du projet

Le projet est développé en mode agile avec un comité utilisateurs qui rencontre l'équipe projet toutes les
3 à 4 semaines. Toutes les directions utilisatrices sont représentées, avec des référents désignés. Les mises
à jour en production ont lieu au même rythme.

L'équipe projet constituée de quatre ingénieurs dont un seul est à plein temps
sur le projet, utilise [GitLab](/posts/gitlab/) pour :

- le suivi de la réalisation ;
- les interactions (avec le [Rocket.chat](https://rocket.chat/) du Sénat pour
les discussions synchrones) ;
- la gestion du code (avec [le wiki de la DSI](/posts/wikitn/) pour la
documentation du projet).

Les utilisateurs pouvant être amenés à travailler à des horaires où le support de la DSI n'est pas présent,
avec des délais courts et une obligation de résultat (le compte rendu analytique de séance doit être publié
dans la nuit, quel que soit l'horaire de levée de séance), il a été décidé
d'investir particulièrement sur la
qualité de cette application. Ainsi, il a par exemple été décidé que chaque ligne code poussée dans le dépôt
doit avoir été revue par au moins un autre développeur de l'équipe. Cette revue de code est réalisée à l'aide
des _demandes de fusion_ (ou _merge requests_) de [GitLab](../gitlab/).

Par ailleurs, dans une démarche qui devient généralisée sur les projets, [les tests automatisés](/posts/tdd/) sont
devenus la norme.

## Un peu de technique

SCRIBE est décomposée entre :

- une collection de services Web REST, codés en java et hébergés sur Tomcat. Ces services web font éventuellement
appel à d'autres composants de notre [SI](/posts/si/) (LDAP, bases de données,
applications métier…), voire à des applications
externes comme un correcteur orthographique et grammatical en SaaS ;
- une interface utilisateur en Javascript chargée dans le navigateur de
l'utilisateur.

### Services web

La base technique est un _J2EE-light_ avec CDI ([weld](http://weld.cdi-spec.org/)), JPA
([hibernate](https://hibernate.org/)), JAX-RS ([resteasy](https://resteasy.github.io/)) et JAXB
([jackson](https://github.com/FasterXML/jackson)). La programmation déclarative facilitée par les différentes
annotations de J2EE est privilégiée pour la lisibilité qu'elle apporte. Parmi toutes les bibliothèques utilisées sur
cette application, on peut aussi distinguer [deltaspike](https://deltaspike.apache.org/) pour les petits plus (en
particulier [configuration](https://deltaspike.apache.org/documentation/configuration.html),
[data](https://deltaspike.apache.org/documentation/data.html) et
[scheduler](https://deltaspike.apache.org/documentation/scheduler.html)) très bien intégrés aux différents modules J2EE
et [lombok](https://projectlombok.org/) qui évite de diluer tout le code métier au milieu de plomberie sans valeur
ajoutée.

Pour faciliter la reproductibilité des tests et la capacité à travailler en mode déconnecté, un environnement complet
bouchonnant l'ensemble des systèmes externes a été mis en place : [base de données embarquée h2](http://h2database.com/),
[annuaire embarqué unboundID](https://docs.ldap.com/ldap-sdk/docs/)…

L'intégration continue exécute systématiquement notre jeu de tests unitaires et de tests d'intégration (qui font office
de tests fonctionnels dans le cadre de services web). Pour l'écriture des tests automatisés, nous avons privilégié
[junit 4](https://junit.org/junit4/) qui a largement fait ses preuves avec 
[assertj](https://joel-costigliola.github.io/assertj/) et [mockito](https://site.mockito.org/) qui facilitent grandement
l'écriture et la lisibilité.

### Interface Utilisateur

Côté navigateur, c'est le système [vue.js](https://vuejs.org/v2/guide/) qui a été choisi (avec les classiques
[vuex](https://vuex.vuejs.org/guide/) et [router](https://router.vuejs.org/guide/)) suite à diverses expérimentations en
interne : sa courbe d'apprentissage et son équilibre simplicité/puissance ont été appréciés. Au cœur d'une application
de rédaction de compte rendu, c'est [quill](https://quilljs.com/) a été retenu sur la recommandation d'un prestataire
pour l'éditeur de texte : nous avons fait le pari de ne pas prendre la librairie la plus connue ou utilisée parce que
Quilljs est simple, avec une API très puissante et venait avec un
[système de commande intégré](https://github.com/afry/quill-mention) très intéressant pour nos utilisateurs.

Pour les composants graphiques, nous sommes très contents de [bootstrap-vue](https://bootstrap-vue.js.org/docs/) et,
en ce qui concerne les librairies complémentaires, nous apprécions
[axios](https://github.com/axios/axios) pour les requêtes vers nos
services web ou encore [date-fns](https://date-fns.org/), très légère pour une gestion néanmoins très puissante des
dates.

La frontière est floue entre tests unitaires et tests d'intégration avec 
[vue-test-utils](https://vue-test-utils.vuejs.org/) mais ils sont, classiquement, codés et exécutés avec
[jest](https://jestjs.io/docs/en/getting-started). Pour ce qui est des tests fonctionnels, les premières
expérimentations ont été réalisées avec [nightwatch](https://nightwatchjs.org/) mais demanderaient à être complétées
pour devenir vraiment utiles.

### Hébergement

SCRIBE est hébergée sur des conteneurs Docker dans [nos clusters Kubernetes internes](/posts/docker/). Ils sont sans état
(_stateless_) pour le maximum de résilience : redémarrage automatique en cas de perte d'un nœud, capacité à augmenter le
nombre de conteneurs pour faire face à une charge exceptionnelle…

## Feuille de route

Une phase intermédiaire a démarré durant laquelle SCRIBE est en production et permet de rédiger et corriger des comptes
de rendu de commission. La publication finale du 
[bulletin des commissions](https://www.senat.fr/seances/comptes-rendus.html#commissions) (sur le site web et _via_
l'imprimeur) se fait toujours via l'ancien système, ce qui permet de faciliter la transition et la montée en charge.

Le travail avance désormais sur les comptes rendus de séance, tout en continuant à ajouter de nouvelles fonctionnalités
au compte rendu de commission. Les comités utilisateurs continuent à se tenir à intervalles réguliers, ce qui permet de
réorienter certains choix en fonction des retours terrain. 

À terme, la publication sera entièrement réalisée dans SCRIBE. Il deviendra alors possible de gagner en fiabilité et en
cohérence, en échangeant directement des données structurées avec nos partenaires, comme le _Journal Officiel_.