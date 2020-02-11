---
title: Cache de la bibliothèque de curseurs | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68019061"
---
# <a name="cursor-library-cache"></a>Cache de la bibliothèque de curseurs
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande l’utilisation de la fonctionnalité de curseur du pilote.  
  
 Pour chaque ligne de données dans le jeu de résultats, la bibliothèque de curseurs met en cache les données pour chaque colonne liée, la longueur des données dans chaque colonne liée et l’état de la ligne. La bibliothèque de curseurs utilise les valeurs du cache pour revenir par **SQLFetch** et **SQLFetchScroll** et pour construire des instructions recherchées pour les opérations positionnées. Pour plus d’informations, consultez [construction d’instructions recherchées](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Données de la colonne](../../../odbc/reference/appendixes/column-data.md)  
  
-   [Longueur des données de colonne](../../../odbc/reference/appendixes/length-of-column-data.md)  
  
-   [État des lignes](../../../odbc/reference/appendixes/row-status.md)  
  
-   [Emplacement du cache](../../../odbc/reference/appendixes/location-of-cache.md)
