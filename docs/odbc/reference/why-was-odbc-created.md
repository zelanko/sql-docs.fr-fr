---
description: Pourquoi ODBC a-t-il été créé ?
title: Pourquoi ODBC a-t-il été créé ? | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], about ODBC
ms.assetid: ba6eb993-316b-4650-bab8-d76583c00e53
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6ce24a4856c3bae6d271712a948e1ae5e2ceecbf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428791"
---
# <a name="why-was-odbc-created"></a>Pourquoi ODBC a-t-il été créé ?
Historiquement, les entreprises utilisaient un SGBD unique. Tout accès à la base de données a été effectué par le biais de la partie frontale de ce système ou par le biais d’applications écrites pour fonctionner exclusivement avec ce système. Toutefois, au fur et à mesure que l’utilisation d’ordinateurs a évolué et que le matériel et les logiciels informatiques sont devenus disponibles, les entreprises ont commencé à acquérir différents SGBD. Les raisons sont nombreuses : les gens ont acheté ce qui était le moins cher, ce qui était le plus rapide, ce qu’ils connaissaient déjà, ce qui était le plus récent sur le marché, ce qui fonctionnait le mieux pour une seule application. D’autres raisons étaient des réorganisations et des fusions, où les départements possédaient auparavant un SGBD unique en avait maintenant plusieurs.  
  
 Le problème a augmenté encore plus complexe avec l’avènement des ordinateurs personnels. Ces ordinateurs ont introduit un certain nombre d’outils permettant d’interroger, d’analyser et d’afficher des données, ainsi qu’un certain nombre de bases de données peu onéreuses et faciles à utiliser. À partir de là, une seule entreprise possédait souvent des données disséminées sur une multitude de postes de travail, de serveurs et d’mini-ordinateurs, stockés dans différentes bases de données incompatibles et accessibles par un grand nombre d’outils différents, dont certains peuvent accéder à toutes les données.  
  
 Le défi final vient de l’avènement de l’informatique client/serveur, qui cherche à tirer le meilleur parti des ressources informatiques. Les ordinateurs personnels peu coûteux (les clients) se trouvent sur le bureau et fournissent un frontal graphique aux données et un certain nombre d’outils économiques, tels que des feuilles de calcul, des programmes graphiques et des générateurs de rapports. Les ordinateurs minisite et ordinateurs centraux (les serveurs) hébergent les SGBD, où ils peuvent utiliser leur puissance de calcul et leur emplacement central pour fournir un accès aux données rapide et coordonné. Comment les logiciels frontaux étaient-ils ensuite connectés aux bases de données principales ?  
  
 Un problème similaire A été rencontré avec des éditeurs de logiciels indépendants. Les fournisseurs qui écrivent des logiciels de base de données pour les miniordinateurs et les macroordinateurs étaient généralement obligés d’écrire une version d’une application pour chaque SGBD ou d’écrire du code spécifique au SGBD pour chaque SGBD auquel ils veulent accéder. Les fournisseurs qui écrivent des logiciels pour les ordinateurs personnels devaient écrire des routines d’accès aux données pour chaque SGBD avec lequel ils voulaient travailler. Cela signifiait souvent qu’une grande quantité de ressources était passée à écrire et à gérer des routines d’accès aux données plutôt qu’à des applications, et que les applications étaient souvent vendues en dehors de leur qualité, mais qu’elles pouvaient accéder aux données d’un SGBD donné.  
  
 Les deux jeux de développeurs nécessaires étaient un moyen d’accéder aux données dans différents SGBD. Le groupe de macroordinateurs et de mini-ordinateurs a besoin d’un moyen de fusionner les données de différents SGBD dans une même application, tandis que le groupe d’ordinateurs personnels avait besoin de cette possibilité, ainsi qu’un moyen d’écrire une application unique indépendante d’un SGBD. En bref, les deux groupes devaient disposer d’un moyen interopérable pour accéder aux données. ils nécessitaient une connectivité Open Database.
