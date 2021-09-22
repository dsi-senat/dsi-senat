---
Weight: 400
title: "Développer autour des formats structurés"
date: 2021-06-09T17:24:06+02:00
lastmod : 2021-09-01T16:12:00+02:00
draft: false
cover: /img/code-html.jpg
author: SD
avatar: /dsi/sd.png
tags:
 - méthode
 - structure
categories:
 - organisation
---
Les ingénieurs du pôle documentaire utilisent le plus possible des formats
de données structurés de préférence aux formats bureautiques.

Quelle est la raison de cette stratégie et quelles en sont les illustrations ?
<!--more-->

Une structuration par les métadonnées
-------------------------------------

Les documents bureautiques produits grâce à un traitement de texte, bien qu’ils
soient encore très utilisés au Sénat, présentent des limites évidentes pour un
traitement automatisé des informations. Il leur manque en premier lieu les
éléments permettant de les situer dans un « contexte », ce qu’on appelle des
métadonnées. Un document est-il un projet de loi, un rapport, autre chose ?
Quels sont ses auteurs, sa thématique, etc. ? 

Notre la base de données Dosleg (qui répertorie l’ensemble documents produits
lors du processus législatif et transmis entre le Gouvernement, l’Assemblée
nationale et le Sénat) permet d’associer des métadonnées de ce type à chaque
texte de loi examiné au parlement.

Les applications concrètes de cette approche structurée, de type GED, sont
nombreuses. Dosleg permet par exemple de :

- produire les **dossiers législatifs**, tels que 
[celui du projet de loi 4D](https://www.senat.fr/dossier-legislatif/pjl20-588.html)
;
- présenter chaque rapport sénatorial sur le site internet en l’accompagnant
d’un bloc “Repères” (comme ce rapport
https://www.senat.fr/rap/l20-723/l20-723.html );
- enrichir automatiquement la 
[notice personnelle de chaque sénateur](https://www.senat.fr/senateur/darnaud_mathieu14259y.html ) d'un lien vers les rapports dont il est auteur - par exemple
https://www.senat.fr/rapports-senateur/darnaud_mathieu14259y.html ).

Une structuration du document lui-même
--------------------------------------

Pour aller plus loin, il faut considérer non plus le contexte, mais la
structure interne d'un document. Un texte est par exemple composé de phrases 
regroupées en alinéas, eux-même regroupés en articles, puis
en chapitres, etc. À l'intérieur d'une phrase, on peut aussi repérer
certaines
informations comme la référence à un texte de loi ou un code existant.

A partir d'une rédaction brute par l'utilisateur, notre application
[Monalisa](/posts/monalisa/) procède à cette identification de la structure interne
des textes législatifs. S'appuyant sur cette analyse, elle est capable
d'appliquer automatiquement les bonnes règles de légistique et les bonnes règles
typographiques aux textes législatifs - règles qui, appliquées manuellement,
sont fortement consommatrice de temps et sujettes à de nombreuses erreurs, tout
en apportant peu de valeur ajoutée sur le fond. C’est cette optimisation du
temps de rédaction qui a conduit de jury du CNEN/Lexis Nexis à
[primer notre application](/posts/prix2020/) face à d'autres produits développés
par l'État.

Un autre bénéfice permis par Monalisa est de produire ce que nous appelons le
tableau de
[la loi en construction](http://www.senat.fr/tableau-historique/pjl20-672.html) :
ce tableau permet en effet à tout en chacun de visualiser très simplement
l’ensemble des transformations de chaque loi au fur et à mesure de son examen
par le parlement et de relier ces transformations au contexte dans lequel elles
sont eu lieu. Monalisa offre notamment des liens systématiques vers les vidéos
des débats parlementaires ou vers les [amendements adoptés](/posts/ameli/) qui
conduisent aux modifications du texte.

Vers des éditeurs structurés ?
------------------------------

La détection automatique des structure peut être trop coûteuse voire impossible.
Dès lors se pose la question : quel outil utiliser pour permettre la saisie
d'un document structuré ?

Contre toute attente, on peut citer un traitement de texte traditionnel comme
Word qui permet d'utiliser des styles nommés (styles
de paragraphes ou style de caractères). On peut alors peut associer ces styles
à une certaine sémantique, par exemple décider que le Style "Article" doit être
utilisé pour rédiger le contenu d'un article. 
Avec Word, on peut aussi placer des champs personnalisés
dans le document, ce qui est une porte ouverte pour y insérer des données
provenant du reste du système d'information. Cette approche a d'ailleurs été
choisie
pour l'élaboration des comptes rendus intégraux. Elle présente l'avantage de
reposer sur des outils éprouvés, dont l'ergonomie a été peaufinée par de
nombreuses années de travail de l'éditeur du logiciel.

Elle a cependant des défaut importants :

- un traitement de texte est un outil générique dont l'adaptation au métier
spécifique du rédacteur est limitée;
- qui n'assure pas la cohérence structurelle, un style pouvant
toujours être utilisé à la place d'un autre par un rédacteur peu expérimenté,
peu attentif ou pressé. Les traitements ultérieurs du document peuvent dans ce
cas être fortement perturbés.

C'est pour cela qu'afin de répondre au mieux aux demandes exigeantes des
rédacteurs dans plusieurs directions, nous avons opté pour une approche plus
rigoureuse et adaptée bien que plus coûteuse en développant
un logiciel spécifique, qui est notre éditeur structuré de comptes rendus :
[scribe](/posts/scribe).

XML vs BDD
----------

Notre expérience de la structuration des documents qui a commencé à la fin des
années 1990 nous a conduit à considérer qu'au cœur des outils structurants une
base de données relationnelle sera plus efficace que des fichiers en XML.
Les bases de données sont en effet plus aptes à traiter les données dans
n'importe quel sens (texte linéaire, classement par sénateurs, classement
par projet de lois par exemple).

Lorsque le cœur repose du  XML, il est très souvent nécessaire de convertir
ce XML en structure en base de données pour disposer de la souplesse
d'exploitation nécessaire. Ainsi le système de publication
du compte rendu intégral des séances publiques en cours
de remplacement reposait sur l'utilisation de fichier XML, ce qui nous obligeait
à traiter en parallèle trois représentations distinctes du même document :

éditeur à l'écran --> fichier XML --> base de données

Alors que deux représentations auraient pu être suffisantes.

XML reste un choix pertinent pour échanger des données indépendamment des
architectures logicielles qui les produisent et les utilisent,
surtout si le format XML choisi repose
sur un standard, ce qui permet d'économiser à la fois sur la conception et sur
la création d'outils. Ainsi, [Monalisa](/posts/monalisa/),
bien que reposant sur une base
de données est tout a fait capable de produire des documents XML au format
international **Akoma Ntoso** sur la 
[plateforme opendata](https://data.senat.fr/les-donnees-dispositifs-des-textes-monalisa/)
du Sénat. Ces fichiers sont utilisés par le public, mais aussi par les logiciels
développés par le gouvernement pour préparer les discutions des textes au
Sénat.

Et la bureautique dans tout cela ?
----------------------------------

Les outils bureautiques sont très utilisés. Qui peut le
plus peut le moins. Autant il est difficile de créer de la structure à partir
du non-structuré, autant l'inverse est simple. La production de fichiers
bureautiques par nos applications apporte une vraie souplesse à nos
utilisateurs par rapport à la génération de formats figés (PDF par exemple).

Cette production repose sur une étroite collaboration avec la
[Cellule bureautique](/posts/dsi/).

---
Crédit photo : <a href="https://pixabay.com/fr/users/jamesmarkosborne-1640589/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=1076536">James Osborne</a> de <a href="https://pixabay.com/fr/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=1076536">Pixabay</a>
