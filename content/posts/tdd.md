---
Weight: 450
title: "Mettre en œuvre le Test driven Development"
date: 2021-07-15T18:39:00+02:00
lastmod: 2021-09-01T16:39:00+02:00
draft: false
cover: /img/cycle-global-tdd.png
author: LC
avatar: /dsi/lc.jpg
tags:
 - méthode
categories:
 - organisation
---
Pour ses développements, l'équipe documentaire s'efforce de mettre en place une
méthode de tests systématiques.

Pourquoi cela ? Et comment procédons-nous ?
<!--more-->

L'intérêt des tests automatisés dans le cadre d'applications métier qui vont évoluer et être maintenues pendant des
années n'est plus à démontrer :

- ils documentent les fonctionnalités métier de manière pratique et complète, et facilitent ainsi la rotation des
  développeurs et la capacité à intervenir sur du code qui n'est pas le sien,
- ils limitent les régressions fonctionnelles, toujours très mal supportées par les utilisateurs,
- ils encouragent des architectures de code maintenables : le découplage par exemple 

Cela fait quelque temps que la pratique est encouragée dans nos équipes de développement, avec un suivi
au niveau de [l'intégration continue](/posts/gitlab/) ou de 
[notre plateforme qualité sonarqube](https://www.sonarqube.org/). Et nous avons, comme d'autres, constaté certaines
difficultés avec nos jeux de tests. En particulier s'assurer de ne pas oublier de tester certaines fonctionnalités
essentielles, et surtout être sûr que nos tests sont bien écrits et vont vraiment nous avertir si le code applicatif
dérive dans le futur. Ce second point est beaucoup plus difficile qu'il n'y paraît et la seule assurance (au moins à
court terme) reste de changer le code applicatif pour voir le test planter avant de le remettre en place, ce qui est
évidemment chronophage et insatisfaisant. 

Depuis quelque temps, nous expérimentons le _développement piloté par les tests_ ou 
<span lang="en">_test driven development_</span>. Le principe consiste à **ne pas écrire de nouveau code applicatif
tant qu'on n'a pas au moins un test en échec**. Dit autrement, on ne change pas le code tant qu'on n'a pas un test qui
prouve la nécessité de le changer. Le processus d'écriture d'une nouvelle fonctionnalité va donc être le suivant :

1. écrire un test, qui doit être en échec : on se donne ainsi une chance que le test soit bien écrit et puisse
   nous alerter dans le futur si la fonctionnalité régresse,
1. écrire le code applicatif _le plus simple possible_ (c'est important !) pour que l'ensemble des tests déjà écrits
   passent. Il faut ici éviter d'anticiper sur les futurs tests pas encore écrits pour pouvoir les vérifier en
   erreur eux-aussi lors de leur écriture.
1. Une fois que l'ensemble du jeu de tests existant passe, on peut procéder au remaniement du code applicatif existant.

Ce nouveau mode d'écriture de code répond assez directement aux deux problématiques visées. Et nous avons pu constater
par ailleurs, ce que nous n'avions pas forcément envisagé, qu'il encourage une architecture de code plus simple en
insistant sur les petits pas progressifs plutôt que sur l'usine à gaz qui anticipe souvent des besoins qui ne viendront
jamais.

S'il est relativement facile à mettre en place lorsque les fonctionnalités sont assez bien balisées, il est parfois 
difficile à mettre en place lors d'expérimentations fonctionnelles. Dans ce cas, on peut avoir tendance à repasser sur
des tests _a posteriori_ mais on constate que la pratique du <abbr lang="en" title="Test Driven Development">TDD</abbr>
a quand même largement changé nos habitudes et que la vérification de ses tests en intervenant ponctuellement sur le
code applicatif est devenue plus naturelle.


---
Schéma : source
[Wikipedia](https://upload.wikimedia.org/wikipedia/commons/0/0b/TDD_Global_Lifecycle.png) - Xarawn - Own work - [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
