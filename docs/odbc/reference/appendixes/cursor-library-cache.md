---
title: Cache de bibliothèque de curseurs | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: d6a91cd6-3905-4e3a-98ab-37fce893dbe1
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f60c04e1022c34e77a4c3c4d4dc5d54f048d449a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="cursor-library-cache"></a>Cache de bibliothèque de curseurs
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Pour chaque ligne de données dans le jeu de résultats, la bibliothèque de curseurs met en cache les données pour chaque colonne dépendante, la longueur des données dans chaque colonne dépendante et l’état de la ligne. La bibliothèque de curseurs utilise les valeurs dans le cache retournée via **SQLFetch** et **SQLFetchScroll** et pour construire des instructions pour les opérations positionnées recherchées. Pour plus d’informations, consultez [construire des instructions recherché](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Données de colonne](../../../odbc/reference/appendixes/column-data.md)  
  
-   [Longueur des données de colonne](../../../odbc/reference/appendixes/length-of-column-data.md)  
  
-   [État des lignes](../../../odbc/reference/appendixes/row-status.md)  
  
-   [Emplacement du cache](../../../odbc/reference/appendixes/location-of-cache.md)
