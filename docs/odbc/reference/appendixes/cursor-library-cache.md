---
title: "Cache de bibliothèque de curseurs | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: d6a91cd6-3905-4e3a-98ab-37fce893dbe1
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 06b893a857f87c2d6c3911e3d81fd0cd02d89668
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="cursor-library-cache"></a>Cache de bibliothèque de curseurs
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Pour chaque ligne de données dans le jeu de résultats, la bibliothèque de curseurs met en cache les données pour chaque colonne dépendante, la longueur des données dans chaque colonne dépendante et l’état de la ligne. La bibliothèque de curseurs utilise les valeurs dans le cache retournée via **SQLFetch** et **SQLFetchScroll** et pour construire des instructions pour les opérations positionnées recherchées. Pour plus d’informations, consultez [construire des instructions recherché](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Données de la colonne](../../../odbc/reference/appendixes/column-data.md)  
  
-   [Longueur des données de colonne](../../../odbc/reference/appendixes/length-of-column-data.md)  
  
-   [État de la ligne](../../../odbc/reference/appendixes/row-status.md)  
  
-   [Emplacement du Cache](../../../odbc/reference/appendixes/location-of-cache.md)

