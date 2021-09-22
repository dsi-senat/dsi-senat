---
Weight: 300
title: "Faire vivre le système d'information"
date: 2021-06-09T17:24:06+02:00
lastmod: 2021-07-16T18:40:00+02:00
draft: false
cover: /img/sew-5034027_1280.png
author: SD
avatar: /dsi/sd.png
tags:
 - SI
categories:
 - Organisation
---
L'équipe documentaire a notamment pour mission de définir et
de faire vivre sur le long terme le système d'information, qui permet au Sénat
d'accomplir ses missions institutionnelles et de remplir son obligation de
publicité vis à vis des citoyens.

Comment se traduit concrètement cette nécessité de suivi sur la durée ?
<!--more-->

De nombreuse interfaces entres les applications et les bases de données
-----------------------------------------------------------------------

Dans le travail de l'équipe les développements ponctuels peu connectés avec le
reste du SI sont l'exception. Le plus souvent les application sont intégrées
dans un écosystème dont les diverses composantes (applications, bases de
données) jouent leur rôle dans une étroite interdépendance.

Assurer la cohérence du système d'information dans ces conditions implique de 
définir clairement les domaines de responsabilité de
chaque  application et d'anticiper l'impact de toute modification dans le schéma
global du SI. C'est le rôle du
[responsable de domaine](/posts/dsi/), mais aussi de chaque développeur.

L'intégration et la complexié croissantes du SI font par ailleurs de la
documentation des interfaces entre les applicatifs un enjeu de plus en plus
crucial. Sous
l'impulsion de [l'équipe développant les applications de gestion](/posts/dsi/),
notre équipe a démarré un descriptif complet des interfaces. Ce travail devra
être poursuivi dans les prochains mois.

Une gestion du parc applicatif dans le temps long
-------------------------------------------------

Outre le développement de nouvelles applications, les ingénieurs de l'équipe ont
pour mission d'assurer la maintenance courante de leurs applications
(25% de leur activité est consacré à cela).

La maintenance évolutive, c’est-à-dire l'évolution et la modernisation des applications tant du point de vue technique qu’ergonomique, constitue aussi un enjeu important et un aspect motivant du travail. 

Pour des raisons pratiques, les anciennes technologies ne peuvent être
immédiatement remplacées. Leur coexistence temporaire avec de
nouvelles qui représentent l'état de l'art informatique est un problème
difficile qui donne lieu à des solutions variées. Celles-ci dépendent du
contexte de chaque application. Les articles suivants montre cette diversité :

- [Ameli](/posts/ameli/)
- [Arsen](/posts/refonte-arsen/)
- [Scribe](/posts/scribe)
- [www.senat.fr](/posts/www.senat/)

Pour mener à bien ces évolutions, chaque ingénieur doit consacrer du
temps à la [veille technologique](/posts/veille/).

Des développements pensés pour facilité la maintenance des applications
-----------------------------------------------------------------------

Dans la mesure où nous devons suivre les applicatifs pendant des années, il est
essentiel que nos développements soient maintenables. C'est pourquoi à
la DSI du Sénat, des méthodes telles que le [Test Driven Development](/posts/tdd/)
ou encore [l'intégration continue](/posts/gitlab/) sont mises en œuvre.

Nous utilisons également un [Wiki](/posts/wikitn/) pour nos documentations, ce qui
permet un accès facile et une mise à jour par chacun peu coûteuse.

Ce Wiki est aussi
un support pour les FAQ qui permettent de répertorier les difficultés fréquentes
des utilisateurs et les solutions que nous pouvons proposer. Des
[wikis coproduits avec les utilisateurs](/posts/coproduction) accueillent par
ailleurs
les manuels utilisateurs et autres cahiers de procédure. Un produit de
ticketing basé sur Itop (le support de premier niveau est externalisé) et la
gestion des "Issues" dans [Gitlab](/posts/gitlab/) permettent également le suivi de
nos relations avec les utilisateurs.

---
Illustration : <a href="https://pixabay.com/fr/users/maky_orel-436253/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=5034027">Markéta Machová</a> de <a href="https://pixabay.com/fr/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=5034027">Pixabay</a>
