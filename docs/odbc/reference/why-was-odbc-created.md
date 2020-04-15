---
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
ms.openlocfilehash: 22173b0ad3dd8abf2d168b41a16a03bc414022ce
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302780"
---
# <a name="why-was-odbc-created"></a>Pourquoi ODBC a-t-il été créé ?
Historiquement, les entreprises utilisaient un seul DBMS. Tous les accès aux bases de données ont été effectués soit par l’avant de ce système, soit par le biais d’applications écrites pour fonctionner exclusivement avec ce système. Cependant, à mesure que l’utilisation des ordinateurs augmentait et que de plus en plus de matériel informatique et de logiciels devenaient disponibles, les entreprises ont commencé à acquérir différents DBMS. Les raisons étaient nombreuses: Les gens ont acheté ce qui était le moins cher, ce qui était le plus rapide, ce qu’ils savaient déjà, ce qui était le plus récent sur le marché, ce qui fonctionnait le mieux pour une seule application. D’autres raisons étaient les réorganisations et les fusions, où les ministères qui avaient auparavant un seul DBMS en avaient maintenant plusieurs.  
  
 La question est devenue encore plus complexe avec l’avènement des ordinateurs personnels. Ces ordinateurs ont introduit une foule d’outils pour interroger, analyser et afficher des données, ainsi qu’un certain nombre de bases de données peu coûteuses et faciles à utiliser. Dès lors, une seule société disposait souvent de données dispersées sur une myriade de ordinateurs de bureau, de serveurs et de mini-ordinateurs, stockées dans une variété de bases de données incompatibles et accessibles par un grand nombre d’outils différents, dont peu pouvaient obtenir toutes les données.  
  
 Le dernier défi est venu avec l’avènement de l’informatique client /serveur, qui cherche à faire l’utilisation la plus efficace des ressources informatiques. Les ordinateurs personnels peu coûteux (les clients) s’assoient sur le bureau et fournissent à la fois une extrémité avant graphique aux données et un certain nombre d’outils peu coûteux, tels que des feuilles de calcul, des programmes de cartographie et des constructeurs de rapports. Les mini-ordinateurs et les ordinateurs centraux (les serveurs) hébergent les DBMS, où ils peuvent utiliser leur puissance de calcul et leur emplacement central pour fournir un accès rapide et coordonné aux données. Comment le logiciel front-end a-t-il été connecté aux bases de données back-end ?  
  
 Un problème similaire a été confronté à des éditeurs de logiciels indépendants (ISV). Les fournisseurs qui rédigent des logiciels de base de données pour les mini-ordinateurs et les cadres centraux étaient généralement obligés d’écrire une version d’une application pour chaque DBMS ou d’écrire un code spécifique à DBMS pour chaque DBMS à laquelle ils souhaitaient accéder. Les fournisseurs qui rédigent des logiciels pour ordinateurs personnels devaient écrire des routines d’accès aux données pour chaque DBMS différent avec lequel ils voulaient travailler. Cela signifiait souvent qu’une énorme quantité de ressources étaient consacrées à la rédaction et à la conservation des routines d’accès aux données plutôt qu’aux applications, et les applications étaient souvent vendues non pas sur leur qualité, mais sur la question de savoir si elles pouvaient accéder aux données dans un DBMS donné.  
  
 Les deux ensembles de développeurs avaient besoin d’un moyen d’accéder aux données dans différents DBMS. Le groupe de mainframe et mini-ordinateur avait besoin d’un moyen de fusionner les données de différents DBMS dans une seule application, tandis que le groupe d’ordinateurs personnels avait besoin de cette capacité ainsi que d’un moyen d’écrire une seule application qui était indépendante de n’importe quel DBMS. En bref, les deux groupes avaient besoin d’un moyen interopérable d’accéder aux données; ils avaient besoin d’une connectivité de base de données ouverte.
