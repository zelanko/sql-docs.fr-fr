---
title: Cache de la bibliothèque curseur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: d6a91cd6-3905-4e3a-98ab-37fce893dbe1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 597abe268979852d754e2e3e86ae81daa8f3fed8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019061"
---
# <a name="cursor-library-cache"></a>Cache de la bibliothèque de curseurs
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Pour chaque ligne de données dans le jeu de résultats, la bibliothèque de curseurs met en cache les données pour chaque colonne dépendante, la longueur des données dans chaque colonne dépendante et l’état de la ligne. La bibliothèque de curseurs utilise les valeurs dans le cache à retourner via **SQLFetch** et **SQLFetchScroll** et pour construire des instructions pour les opérations positionnées recherchées. Pour plus d’informations, consultez [construisant des instructions recherché](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Données de colonne](../../../odbc/reference/appendixes/column-data.md)  
  
-   [Longueur des données de colonne](../../../odbc/reference/appendixes/length-of-column-data.md)  
  
-   [État des lignes](../../../odbc/reference/appendixes/row-status.md)  
  
-   [Emplacement du cache](../../../odbc/reference/appendixes/location-of-cache.md)
