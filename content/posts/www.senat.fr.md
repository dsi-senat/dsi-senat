---
Weight: 20500
title: "Moderniser www.senat.fr"
date: 2021-07-16T11:29:00+02:00
date: 2021-09-01T16:29:00+02:00
draft: false
cover: /img/www.senat.fr.png
author: SD
avatar: /dsi/sd.png
tags:
 - Application
categories:
 - application
---

Le Sénat a été une des premières institutions publiques françaises à ouvrir 
son site
web en 1995. La dernière refonte date de 2010 et le site a besoin d'un sérieux
rajeunissement.

À quoi consiste ce projet de migration d'un site comportant 2 millions de
pages ?
<!--more-->

L'existant
----------

Le site actuel utilise le CMS [Typo3](https://typo3.org/) qui permet de produire
la _home page_ et la plupart des pages de navigation dans
le site, ainsi que les pages à rédaction libre comme, par exemple, les
[pages d'actualité](https://www.senat.fr/actualites/index.html). Le CMS ne gère
que 2% des pages du site, mais ces pages sont particulièrement consultées.

Les autres pages du site sont générées par nos applicatifs.

Le frontal est constitué de deux serveurs Apache qui servent des
pages statiques. Cette architecture permet une maintenance peu coûteuse tout en
assurant une bonne sécurité (peu de surface d'attaque) et une bonne réactivité
(le serveur étant essentiellement un serveur de fichiers).

Le site utilise aussi un moteur de recherche basé sur le logiciel Intuition,
qui permet l’accès en recherche à nos principales bases documentaires :
documents des dossiers législatifs, rapports et textes européens,
questions parlementaires, comptes rendus (voir [Scribe](/posts/scribe/)), etc.

Les objectifs
-------------

Il s'agit de moderniser le CMS, de simplifier la navigation, d’optimiser la
consultation sur tout type de terminal grâce à un design "_responsive_", de
rendre le graphisme plus attrayant et, en définitive, de mieux mettre en valeur
la richesse documentaire de ce site de référence sur les thématiques juridiques.

L'organisation du projet
------------------------

Si la mise en place d’un CMS, la mise au point de la charte graphique et la
fourniture de modèles pour les applicatifs seront confié à une société
extérieure dans le cadre d’une procédure d’appel d’offre, notre équipe jouera
cependant un rôle essentiel. Il lui appartiendra de gérer les relations
techniques avec la société sélectionnée par l’appel d’offre, de coordonner les
développeurs de l'équipe qui doivent adapter leurs applicatifs au nouveau site
et de créer et mettre en place en coordination avec  l'[équipe système](/posts/dsi)
le nouveau système de publication.Enfin, les ingénieurs de l’équipe en charge du projet apporteront une aide technique à la Direction de la communication pour tout le travail nécessaire à la maîtrise du CMS et du nouveau site.

---
Illustration : l'actuelle page de démarrage du site https://www.senat.fr/
