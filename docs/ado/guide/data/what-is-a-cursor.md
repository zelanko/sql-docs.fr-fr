---
title: Qu’est qu’un curseur ? | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], about cursors
ms.assetid: 596eb4b6-c22f-4cde-b23f-172dd66c3161
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9ad683af9cea8ca4f5bc1736a48f0662656b6ef1
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66704517"
---
# <a name="what-is-a-cursor"></a>Qu’est qu’un curseur ?
Les opérations réalisées dans une base de données relationnelle s'exécutent sur un ensemble complet de lignes. L'ensemble de lignes retourné par une instruction SELECT contient toutes les lignes satisfaisant aux conditions de la clause WHERE de l'instruction. Cet ensemble complet de lignes retournées par l'instruction est appelé ensemble de résultats. Applications, en particulier celles qui sont interactifs et en ligne, ne peut pas toujours fonctionner efficacement l’ensemble de résultats en tant qu’unité. Ces applications ont besoin d'un mécanisme leur permettant de travailler avec une seule ligne ou avec un petit bloc de lignes à la fois. Les curseurs sont une extension des ensembles de résultats et fournissent ce mécanisme.  
  
 Un curseur est implémenté par une bibliothèque de curseurs. Une bibliothèque de curseurs est un logiciel, souvent implémenté en tant que partie d’un système de base de données ou d’une API, d’accès aux données qui est utilisé pour gérer les attributs des données retournées à partir d’une source de données (un jeu de résultats). Ces attributs incluent la gestion de l’accès concurrentiel, position du jeu de résultats, nombre de lignes retournées et si vous pouvez déplacer vers l’avant ou vers l’arrière (ou les deux) par le biais du résultat défini (capacité de défilement).  
  
 Un curseur effectue le suivi de la position dans le jeu de résultats et vous permet d’effectuer plusieurs opérations ligne par ligne par rapport à un jeu de résultats, avec ou sans renvoi à la table d’origine. En d’autres termes, les curseurs conçus pour renvoyer un jeu de résultats basé sur les tables dans les bases de données. Le curseur est ainsi nommé car il indique la position actuelle dans le jeu de résultats, tout comme le curseur à l’écran indique la position actuelle.  
  
 Il est important de vous familiariser avec le concept des curseurs avant de passer aux spécificités de son utilisation dans ADO.  
  
 Utilisation de curseurs, vous pouvez :  
  
-   Spécifier le positionnement sur des lignes spécifiques dans le jeu de résultats.  
  
-   Récupérer une ligne ou un bloc de lignes basé sur la position du jeu de résultats actuel.  
  
-   Modifier des données dans les lignes à la position actuelle dans le jeu de résultats.  
  
-   Définir différents niveaux de sensibilité aux modifications de données apportées par d’autres utilisateurs.  
  
 Par exemple, considérez une application qui affiche une liste des produits disponibles pour un acheteur potentiel. L’acheteur fait défiler la liste pour afficher les coûts et les détails du produit et enfin sélectionne un produit à l’achat. Défilement supplémentaires et la sélection se produit pour le reste de la liste. Point de vue de l’acheteur, les produits s’affichent à la fois, mais l’application utilise un curseur de défilement pour parcourir et vers le bas jusqu'à l’ensemble de résultats.  
  
 Vous pouvez utiliser les curseurs de façons différentes :  
  
-   Sans lignes du tout.  
  
-   Avec certaines ou toutes les lignes dans une table unique.  
  
-   Avec certaines ou toutes les lignes des tables jointes logiquement.  
  
-   Comme en lecture seule ou modifiables au niveau du curseur ou de champ.  
  
-   Comme avant uniquement ou avec défilement complet.  
  
-   Avec le curseur situé sur le serveur.  
  
-   Sensibles aux modifications de table sous-jacente a provoqué par d’autres applications (par exemple, l’appartenance, tri, des insertions, des mises à jour et suppressions).  
  
-   Existant sur le serveur ou le client.  
  
 Les curseurs en lecture seule permettent aux utilisateurs de parcourir le jeu de résultats et les curseurs peuvent implémenter des mises à jour de la ligne en lecture/écriture. Les curseurs complexes peuvent être définis avec les jeux de clés qui pointent vers les lignes de table de base. Bien que certains curseurs sont en lecture seule vers l’avant, d’autres peuvent avancer et reculer et permettent une actualisation dynamique du jeu de résultats selon les modifications apportées par les autres applications à la base de données.  
  
 Pas toutes les applications doivent utiliser les curseurs de données access ou mise à jour. Certaines requêtes ne nécessitent pas de la mise à jour de ligne directe à l’aide d’un curseur. Les curseurs doivent être les dernier recours pour récupérer des données- et, vous devez choisir le curseur d’impact le plus possible. Lorsque vous créez un jeu de résultats en utilisant une procédure stockée, le jeu de résultats n’est pas modifiable à l’aide du curseur modifier ou mettre à jour les méthodes.  
  
## <a name="concurrency"></a>Accès concurrentiel  
 Dans certaines applications multi-utilisateur, il est très important pour les données présentées à l’utilisateur final à être aussi actuelles que possible. Un exemple classique de ce système est un système de réservation de compagnies aériennes, où plusieurs utilisateurs peuvent être se disputent même siège sur un vol donné (et par conséquent, un enregistrement unique). Dans ce cas, la conception de l’application doit gérer des opérations simultanées sur un seul enregistrement.  
  
 Dans d’autres applications, la concurrence n’est pas aussi importante. Dans ce cas, les dépenses encourues pour conserver que les données en cours à tout moment ne peut pas être justifiée.  
  
## <a name="position"></a>Position  
 Un curseur conserve également le suivi de la position actuelle dans un jeu de résultats. Pensez à la position du curseur comme un pointeur vers l’enregistrement en cours, similaire à la façon dont un tableau points d’index à la valeur à cet emplacement précis dans le tableau.  
  
## <a name="scrollability"></a>Capacité de défilement  
 Le type de curseur utilisé par votre application affecte également la possibilité de déplacer vers l’avant et vers l’arrière dans les lignes d’un jeu de résultats ; Cela est parfois appelé capacité de défilement. La possibilité d’avancer *et* vers l’arrière à travers un résultat ensemble accroît la complexité du curseur et n’est donc plus coûteux à implémenter. Pour cette raison, vous devez demander un curseur avec cette fonctionnalité uniquement lorsque cela est nécessaire.
