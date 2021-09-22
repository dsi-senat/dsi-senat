---
Weight: 20100
title: "Moderniser l'application Ameli"
date: 2021-07-16T10:22:00+02:00
lastmod: 2021-09-01T16:22:00+02:00
draft: false
cover: /img/ameli.png
author: MHe
tags:
 - Application
categories:
 - application
---

Ameli est une application essentielle au travail du parlement : c'est elle qui
permet la gestion des amendements, propositions faites par les sénateurs ou le
gouvernement de modifications des textes de loi soumis au parlement.
L'application développée il y a 20 ans est en cours de modernisation.

Comment effectuer cette modernisation sans perturber l'utilisation quotidienne
de cette application ?

<!--more-->

Assurer la coexistence de l'ancien et du nouveau
------------------------------------------------

Les nouveaux développements ont été découpés en
plusieurs modules qui sont mis en
production suivant un calendrier 
[co-construit avec les utilisateurs](/posts/coproduction/). À chaque mise en
production d'un module du nouvel Ameli, nous supprimons la ou les
fonctionnalités correspondantes dans l’ancien Ameli. À terme, l'ensemble de
l'applicatif aura migré.

Le lien entre les deux faces de l'applicatif est assuré via la base de données
relationnelle, dont la structure reste stable. L'approche est donc différente
de celle mise en œuvre pour la [refonte d'Arsen](/posts/refonte-arsen/).

Une double connexion transparente assure une navigation fluide entre le nouvel
Ameli et le nouveau.

Ameli 2020, une architecture modernisée
---------------------------------------

La modernisation consiste à optimiser le logiciel par des évolutions de code,
d’architecture, fonctionnelles, etc... Elle est menée à bien par trois
ingénieurs qui sont aussi en charge d'autres applicatifs importants.

Elle met aussi en œuvre des méthodes et des outils (
[Test Driven Developpement](/posts/tdd/), utilisation de [GitLab](/posts/gitlab/),
[Docker/Kubernetes](/posts/docker/), ...)
qui n'existaient pas encore au moment de la création initiale.

Il s'agit d'un travail important mais nécessaire, car nous souhaitons disposer
d’une application plus performante et plus ergonomique tout en réduisant les
coûts de maintenance et en tirant parti des nouvelles technologies.

Pile technologique
------------------

* Java 11,
* Spring,
* Spring Data JPA + Hibernate,
* Oracle,
* VueJS,
* Vuetify,
* Vuex,
* Axios,
* Hibernate, ...

---
Illustration : un module du nouvel Ameli (c) Sénat