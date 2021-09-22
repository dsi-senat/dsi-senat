---
Weight: 20200
title: "Mettre l'IA au service de la fabrication de la loi"
date: 2021-07-15T20:44:04+02:00
lastmod: 2021-09-01T16:44:04+02:00
draft: false
cover: /img/loi-en-construction.png
author: FP
avatar: /dsi/fp.jpg
tags:
 - Application
 - Structure
categories:
 - application
---

(illustration : Le tableau de la loi en construction qui permet de suivre
précisément l'apport du Parlement sur les textes de loi est une des nombreuses
applications de Monalisa)

Monalisa est l'application de référence pour tout ce qui concerne l'élaboration
des textes de loi par le Parlement et plus particulièrement par le Sénat.

Quelles sont ses caractéristiques techniques et fonctionnelles importantes ?

<!--more-->
Monalisa permet le montage des projets de loi à partir des amendements en
respectant les règles légistiques. Elle permet également de construire les
tableaux de la loi en construction qui fournissent une comparaison automatique
entre les différentes rédactions d'un texte à travers la navette parlementaire.
Enfin, elle sait repérer les références aux dispositions en vigueur et les
rechercher dans le Journal officiel numérique Légifrance pour comprendre
l'impact d'un projet de loi.

Écrite en java, Monalisa se fonde sur des outils avancés de traitement de la
langue naturelle comme les bibliothèques Deep Learning for Java ou Stanford
Core NLP. En particulier, les dernières avancées sur les réseaux de neurones
sont utilisées pour rapprocher les alinéas de sens voisin entre deux rédactions
d'un texte.

Développée par deux ingénieurs de l'équipe documentaires (en plus de leurs
autres activités) sur une infrastructure [Docker / Kubernetes](/posts/docker/) et en
intégration continue avec des outils de génie logiciel comme
[GitLab](/posts/gitlab/), Monalisa constitue l'application la plus avancée en
matière de respect des normes légistiques couronné par un
[prix en 2020](/posts/prix2020/) décerné par le Conseil national d’évaluation des
normes et la revue juridique LexisNexis.

Monalisa participe à [l'approche structurée](/posts/structure/) qui caractérise
la plupart des développements de l'équipe documentaire.

---
Illustration : source https://www.senat.fr/