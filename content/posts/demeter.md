---
Weight: 20600
title: "Imaginer les outils de dématérialisation du travail parlementaire"
date: 2021-07-29T11:29:00+02:00
lastmod: 2021-09-01T16:29:00+02:00
draft: false
cover: /img/demeter.png
author: CP
avatar: /dsi/cp.jpg
tags:
 - Application
categories:
 - application
---

Demeter est l'application de dématérialisation des travaux des commissions et
délégations du Sénat. Elle permet aux utilisateurs de suivre tous les types de
réunion : examen de texte, audition, présentation de rapport...

Pourquoi et comment cette application a-t-elle été développée ?
<!--more-->

## Une approche pragmatique

Le projet de dématérialisation des travaux en réunion début en 2016 sous
l’impulsion du président de la commission du développement durable.

Notre équipe se tourne d’abord vers un produit sur étagère :
[LeadingBoards](https://www.dilitrust.com/solution/dilitrust-governance-digitalisation-des-instances/).
Ce produit très qualitatif, basé sur la visualisation de PDF annotables, se
révèle cependant insuffisant. Il ne permettait pas, par exemple, de visualiser
un projet de loi et ses amendements (proposition de modifications proposées par
les sénateurs) sur un même écran et était peu performant sur les gros textes de
loi. Par ailleurs, l’interconnexion avec le
[système d'information](/posts/si/) qui aurait permis de fournir automatiquement les
informations nécessaires à la tenue des réunions était difficile voire
impossible.

C'est pourquoi il a été décidé de développer une application "maison",
utilisable sur tablette et ordinateur, bien plus adaptée au travail
parlementaire. Demeter permet de suivre des réunions de commission  tant
législatives (fabrication de la loi) que non non législatives. Sur son écran
d’accueil (voir la copie d'écran en entête du présent article) se trouvent les
réunions du jour et leurs différents points d’ordre du jour, classées par
organisme du Sénat (commission ou délégation).

La réalisation de cette application nous a conduits à mieux formaliser les
différentes activités réalisées lors d'une réunion de commission notamment en
mettant au point une carte mentale que nous appelons
familièrement 
["_La Pieuvre_"](/img/Carte-mentale-reunions-commission-AMELI.png) (extrait du
[wiki de la DSI](/posts/wikitn/)) et qui schématise l’ensemble des cas de figure
susceptibles de se produire dans une réunion. Cela montre la nécessité pour
nos développeurs d’acquérir une solide connaissance du travail parlementaire.

## Le résultat

Voici quelques écrans qui illustrent une partie du fonctionnement de l'
application.

### L'examen des amendements

Lors d'une réunion législative, les sénateurs examinent les amendements déposés
sur un texte. Cela peut être en vue de son élaboration (dans ce cas-là, la
commission va adopter les amendements), ou pour émettre un avis sur ces
amendements (en vue de la séance publique par exemple).
La principale force de Demeter est qu'elle permet de suivre l'examen des
amendements en mettant en regard l'amendement et la portion du texte imputée.

![Examen des amendements](/img/demeter-examen-amendements.png)

Ceci est rendu possible grâce aux [données structurées](/posts/structure/) : le
texte entré dans [Monalisa](/posts/monalisa/) n'est pas juste du texte brut. Les
informations sur les articles, les alinéas... sont sauvegardées en base de
données. Lorsqu'un amendement est créé dans [Ameli](/posts/ameli/), on précise sur
quelle portion du texte il porte exactement. Via une API, Demeter récupère
ces informations et permet de mettre en regard le texte et l'amendement.

Par ailleurs, toujours grâce à l'API d'Ameli, les avis et sorts saisis sur les
amendements apparaissent dans Demeter en temps réel.

Soulignons qu'un sénateur peut annoter le texte ou les amendements, 
soit via le clavier, soit via le stylet de la tablette.

### Le suivi d'une réunion non législative

Lors d'une réunion non législative, les utilisateurs vont plutôt utiliser
Demeter pour consulter les documents mis en ligne par les personnels des
commissions et des délégations. Cela peut-être par exemple une courte
biographie d'une personne auditionnée.

![Réunion non législative](/img/demeter-reunion-non-legislative.png)

## Sous le capot : la pile technologique utilisée

- Java, Spring Boot, Hibernate,
- PostgreSQL,
- VueJS, Bootstrap,
- Docker / Kubernetes.

---

Illustrations : (c) Sénat
