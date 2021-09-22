---
Weight: 20300
title: "Refondre la base des sénateurs"
date: 2021-07-15T21:08:04+02:00
lastmod: 2021-09-01T16:08:04+02:00
draft: false
cover: /img/refonte-arsen.png
author: PEL
avatar: /dsi/pel.png
tags:
 - application
 - SI
categories:
 - application
---

(illustration : Le schema de principe de la refonte)

L'application/base de données Arsen qui contient toutes les données biographiques
 des sénateurs est au cœur du système d'information du Sénat. Elle alimente
 plusieurs dizaines d'application. Comment la moderniser sans provoquer
 un big bang ?

<!--more-->

Mais pourquoi donc refondre ?
-----------------------------

Le projet trouve son origine à la confluence d’une demande métier un d’un
besoin IT pour IT : une application à l'ergonomie problématique reposant sur une
base de données ayant vaillamment servi pendant de nombreuses années,
mais accusant le coup du cumul des couches de maintenance, sa conception
datant de 20 ans. L'enchevêtrement des
choix fonctionnels et techniques successifs se faisant sentir dans la facilité
aussi bien à utiliser qu’à maintenir le tout, les conditions pour procéder à
une refonte base + application sont réunies.

C'est aussi une chance d’être à l’écoute de nos métiers et de mettre à jour les
fonctionnalités proposées pour correspondre au mieux à leur processus actuels,
tout en se séparant des contraintes héritées de l'applicatif existant, mais
sans justification au sens opérationnel.

Pourquoi est-ce difficile ?
---------------------------

La particularité de ce couple application/base est qu'il sert de référence pour
les personnes liées à l'activité du Sénat (sénateurs, ministres, députés...).,
et plus particulièrement pour
celles concernant les sénateurs. C'est lui qui est garant de l'exactitude de la
composition du Sénat, de la composition de ses organes (Bureau, Commissions,
Délégations, Groupes politiques, etc.) à n'importe quel instant. C'est lui
qui sert de référence pour toutes les applications qui ont besoin de ces
informations (aussi bien au sein des fonctions métiers que des fonctions
supports : Authentification, RH, de la fabrique des textes à l'application de
gestion des transports, etc.).

De plus, un de ses spécificités est de contenir les membres du Sénat sous ses
différentes formes au fil de l’Histoire de France, c'est-à-dire de gérer les
données "chaudes" d'une période qui s'étend du moment présent jusqu'à des
données historiques de la Chambre des pairs lors de la Restauration.

Avec cette place au carrefour des échanges au sein du Système d'Information du
Sénat, et en prenant en compte les autres projets en cours et les effectifs
contraints, la solution de fixer une date butoir à laquelle toutes les
applications auraient dû migrer leurs interfaces avant l'arrêt de
l'ancienne base n'était pas une option viable.

Comment comptons-nous nous y prendre ?
--------------------------------------

À la différence du projet de [modernisation d'Ameli](/posts/ameli/) nous ne pouvons
nous servir de la base de données comme pont entre les nouveaux et les anciens
développements, car nous souhaitons ici remanier profondément son schéma.

Pour découpler l'évolution de l'application et de la base et la ré-écriture des
interfaces avec les applications tierces, l'idée est de conserver l'ancienne base
en tant que quasi-esclave de la nouvelle (voir le schéma). On suppose que le
sens naturel de circulations des informations est celui qui va de la nouvelle
base à l'ancienne et que le sens inverse est peu fréquent. Ainsi, le métier
pourra utiliser une nouvelle application ergonomique et simple à maintenir et,
pendant toute la phase de transition, côté IT, les consommateurs de données
pourront organiser leur calendrier de migration en fonction de leurs propres
actualités et contraintes, passant ainsi de l’ancien actif, toujours maintenu à
jour en termes de données mais voué à terme à la disparition, au nouveau.

Plusieurs scénarios de synchronisation sont envisagés. Un POC devra être mis en
place pour étudier leurs faisabilités et leurs mérites respectifs et ainsi
sélectionner le plus adapté à nos besoins.

La migration des interfaces, étalée dans le temps, donnera lieu à une 
documentation précise qui participera à la cartographie des applicatifs du
Sénat.

L'équipe qui mène a bien ce projet est composée d'un ingénieur dédié à plein
temps et de deux ingénieurs qui maintiennent aussi d'autres applications.

Pile technologique envisagée
----------------------------

* Vue, 
* Twitter Bootstrap, 
* Java 11
* Spring Websocket
* Webpack
* Spring Boot
* Maven
* Liquibase
* Elasticsearch
* [Docker/Kubernetes](../docker/)

---

Illustration : (c) Sénat
