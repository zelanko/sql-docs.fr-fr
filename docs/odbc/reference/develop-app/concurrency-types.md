---
title: "Types d’accès concurrentiel | Documents Microsoft"
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
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
- locking concurrency control [ODBC]
- optimistic concurrency [ODBC]
- read-only concurrency control [ODBC]
ms.assetid: 46762ae5-17dd-4777-968e-58156f470fe1
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 737fadc881109457051cf30bfce9b493bd164f1c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="concurrency-types"></a>Types d’accès concurrentiel
Pour résoudre le problème de concurrence réduite dans les curseurs, ODBC expose quatre types d’accès concurrentiel au curseur :  
  
-   **En lecture seule** le curseur peut lire les données, mais ne peut pas mettre à jour ou supprimer des données. Il s’agit du type de concurrence par défaut. Bien que le SGBD risquent de verrouiller les lignes pour mettre en œuvre la Repeatable Read et niveaux d’isolement sérialisable, elle peut utiliser des verrous de lecture au lieu de verrous d’écriture. Cela entraîne une concurrence plus importante, car au moins peut lire les données.  
  
-   **Verrouillage** le curseur utilise le plus bas niveau de verrouillage nécessaire pour s’assurer qu’il peut mettre à jour ou supprimer des lignes dans le jeu de résultats. Cela entraîne généralement des niveaux de concurrence très faible, en particulier sur les niveaux d’isolation des transactions Repeatable Read et Serializable.  
  
-   **L’accès concurrentiel optimiste à l’aide de versions de ligne et accès concurrentiel optimiste à l’aide de valeurs** le curseur utilise l’accès concurrentiel optimiste : il met à jour ou supprime des lignes uniquement si elles n’ont pas changé depuis leur dernière lecture. Pour détecter les modifications, il compare les valeurs ou les versions de ligne. Il n’existe aucune garantie que le curseur sera en mesure de mettre à jour ou supprimer une ligne, mais l’accès simultané est beaucoup plus élevée que lorsque le verrouillage est utilisé. Pour plus d’informations, consultez la section suivante, [d’accès concurrentiel optimiste](../../../odbc/reference/develop-app/optimistic-concurrency.md).  
  
 Une application spécifie le type d’accès concurrentiel, il veut le curseur à utiliser avec l’attribut d’instruction SQL_ATTR_CONCURRENCY. Pour déterminer quels types sont pris en charge, il appelle **SQLGetInfo** avec l’option SQL_SCROLL_CONCURRENCY.

