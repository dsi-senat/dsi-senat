---
Weight: 20000
title: "Déployer sur Docker / Kubernetes"
date: 2021-05-07T18:30:04+02:00
lastmod: 2021-09-01T16:30:04+02:00
draft: false
cover: /img/docker.jpg
author: MHi
avatar: /dsi/mhi.jpg
tags:
 - SI
categories:
 - outil
---

Docker / Kubernetes, mise en place récemment, est la plateforme cible de nos
applications. Cette plateforme est sous la responsabilité d'une équipe devops
constituée par des ingénieurs des équipes de développement et de l'équipe
système.

Comment est-elle organisée ?

<!--more-->
Mis en place depuis 2020, l'infrastructure Kubernetes du Sénat est composée de 3
environnements, un environnement de production, un environnement de
qualification et un environnement de bac à sable à destination de l'équipe en
charge de la plateforme.

Cette équipe s'occupe de :

* la maintenance de nos briques systèmes
* fournir des images de bases à jour et qui prennent en compte les spécificités
du système d'information du Sénat
* fournir des outils aux développeurs
* de former l'ensemble des informaticiens et les assister dans l'usage
de la plateforme
* faire de la veille technologique autour de Docker et de Kubernetes

Les développeurs ont la responsabilité du déploiement de leurs applications.
Les déploiements se font à l'aide d'outils comme Helm fournis par l'équipe
"Docker".

Détails techniques :

* 35 nœuds répartis sur 3 clusters
* Déploiement des applications avec Helm
* Déploiement des briques d'infrastructure avec Kustomize
* Utilisation de Traefik pour les flux HTTPS
* Monitoring de la plateforme et des applications avec Prometheus et Grafana
* Collecte des logs dans un puits de logs

---
Illustration : La mascotte Docker de la DSI, fabriquée avec une imprimante 3D
montre l'avance prise sur la migration des applications par l'équipe des
développeurs du pôle Gestion (en blanc) - (c) Sénat
