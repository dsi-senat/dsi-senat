---
Weight: 500
title: "Utiliser Gitlab, le couteau suisse de l'ingénieur Sénat"
date: 2021-07-15T18:39:00+02:00
lastmod: 2021-09-01T16:39:00+02:00
draft: false
cover: /img/Gitlab-14.3.0-pre-issue-tracker-08-25-21.png
author: LC
avatar: /dsi/lc.jpg
tags:
 - méthode
categories:
 - organisation
 - outil
---
L'organisation des développements s'appuie sur l'outil GitLab.

Comment est utilisé GitLab par l'équipe documentaire ?
<!--more-->

Tout d'abord, notre instance GitLab a vocation à devenir l'unique serveur Git centralisé pour l'ensemble de nos
développements. Les groupes permettent de refléter l'organisation interne de l'équipe en équipes et en projets
et les développeurs conservent une visibilité importante sur l'ensemble des projets pour faciliter la collaboration.

Ensuite, nous voyons GitLab avant tout comme une plateforme de communication autour du code ; chaque objet dans
GitLab (ticket, demande de fusion, page wiki…) est une occasion de discussion entre développeurs et chacune de ces 
conversations est enregistrée et devient de la documentation du projet. GitLab permet de soutenir chaque phase de
développement :

1. Les tickets sont le support de la fonctionnalité à développer. On y discute beaucoup cas d'utilisation, exemples ou
   cas aux limites, problématiques d'ergonomie, propositions de design et peu de problématiques techniques qui n'en
   seront que les conséquences (voir les demandes de fusion plus bas). Dans un objectif permanent de maximiser la valeur
   livrée à nos utilisateurs, les tickets purement techniques doivent être limités au maximum ; les évolutions
   techniques seront plutôt portées par des tickets fonctionnels qui nécessitent ces évolutions.
1. Les jalons (<span lang="en">_milestones_</span>) servent à documenter chaque itération. La description peut
   présenter les objectifs de l'itération, mais aussi documenter ce qui a été fait pour préparer la réunion avec les
   utilisateurs. Le point d'entrée principal pour les utilisateurs est le tableau Kanban
   (<span lang="en">_board_</span>) du jalon en cours, avec des colonnes _À faire_, _À définir_, _En cours_, _À valider_
   et _Terminé_. Pour chaque gros projet en cours de développement, ce tableau est aussi le support de la
   réunion quotidienne de l'équipe.
1. Les demandes de fusion (<span lang="en">_merge requests_</span>) sont le support des revues de code. On y discute 
   choix d'implémentation, architecture logicielle, problématiques techniques. Les possibilités offertes par Gitlab
   pour exprimer les contraintes (ne pas fusionner cette requête avant que tel ticket soit fermé,…) et les enchaînements
   (fusionner cette requête entraîne la fermeture de tel ticket…) sont utilisées.
1. La plateforme d'intégration continue compile le code à chaque fois qu'il est poussé sur un dépôt, lance et vérifie 
[les tests automatisés](/posts/tdd/), confronte le code avec la plateforme qualité [sonarqube](https://sonarqube.org). En cas de besoin, le
développeur responsable est contacté automatiquement par mail ou via notre
[rocket.chat](https://rocket.chat/)
interne.

GitLab est très flexible et permet à chaque équipe d'adapter le mode de travail à sa taille et à la complexité ou à la
criticité du projet.

## Perspectives

Notre instance GitLab est mise à jour dès que les nouvelles versions sortent et nous évaluons donc régulièrement les
nouveautés pour faire bouger nos pratiques. C'est ainsi que nous testons en ce moment l'utilité des itérations ou des
publications (<span lang="en">_releases_</span>).

Une fonctionnalité disponible depuis longtemps, coûteuse à implémenter, mais qui nous semble intéressante est la mise à
disposition à la volée d'environnement de test par branches. Depuis notre migration sur des 
[clusters Kubernetes](/posts/docker/), c'est une fonctionnalité qui semble désormais envisageable et que nous testerons.
De là, on pourra peut-être envisager des livraisons en continu (au moins sur les environnemnts de qualification).

La documentation d'une <abbr title="Direction des Systèmes d'Information">DSI</abbr> va plus loin que la simple
documentation du code des applications. Par souci de cohérence, les pages wiki des projets applicatifs sont donc
conservées sur [notre wiki interne](../wikitn/) ce qui limite les synergies avec le reste de GitLab. À l'avenir on
pourra étudier l'utilité de migrer toute la documentation sur GitLab ou peut-être une articulation entre certaines pages
sur WikITN et certaines pages sur le GitLab.

Enfin, notre instance GitLab est pour l'instant limitée aux développeurs, principalement pour des raisons de coût de
licence mais aussi d'IHM trop orientée vers les informaticiens. Avec les efforts pour 
[embarquer de plus en plus les utilisateurs dans la construction](/posts/coproduction/) de nos applications, ce modèle
atteint ses limites : sur certains projets, nous avons parfois une liste de tickets maintenue par les utilisateurs
sous Excel en parallèle de la liste sous GitLab. Nous étudions diverses pistes pour rationaliser ce fonctionnement,
comme l'utilisation du [<span lang="en">_Service Desk_</span>](https://docs.gitlab.com/ee/user/project/service_desk.html).

---
Illustration : [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) -
İsmail Arılık - "Own work" -
[Wikipedia](wikipedia)