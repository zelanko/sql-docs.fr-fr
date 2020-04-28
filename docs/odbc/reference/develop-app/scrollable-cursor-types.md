---
title: Types de curseurs avec défilement | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: dbd32576-0453-4e90-ae45-1a81cee8259d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 63f29269ea209875a2e775cf8d523302fcb9a976
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304230"
---
# <a name="scrollable-cursor-types"></a>Types de curseurs avec défilement
Les quatre types de curseurs à défilement sont statiques, dynamiques, de jeu de clés et mixtes. Les curseurs statiques détectent peu ou pas de modifications, mais sont relativement peu coûteux à implémenter. Les curseurs dynamiques détectent toutes les modifications mais sont coûteux à implémenter. Les curseurs de jeu de clés et les curseurs mixtes se situent entre, en détectant la plupart des modifications, mais à moindre coût que les curseurs dynamiques.  
  
 Les termes suivants sont utilisés pour définir les caractéristiques de chaque type de curseur défilant :  
  
-   **Propres mises à jour, suppressions et insertions.** Mises à jour, suppressions et insertions effectuées par le biais du curseur, soit à l’aide d’un appel à **SQLBulkOperations** ou à **SQLSetPos** , soit à l’aide d’une instruction UPDATE ou DELETE positionnée.  
  
-   **Autres mises à jour, suppressions et insertions.** Mises à jour, suppressions et insertions non effectuées par le curseur, y compris celles apportées par d’autres opérations dans la même transaction, celles effectuées par d’autres transactions et celles effectuées par d’autres applications.  
  
-   **Member.** Ensemble de lignes dans le jeu de résultats.  
  
-   **Ordre.** Ordre dans lequel les lignes sont retournées par le curseur.  
  
-   **Valeurs.** Valeurs de chaque ligne du jeu de résultats.  
  
 Pour plus d’informations sur la mise à jour, la suppression et l’insertion de données, consultez [vue d’ensemble](../../../odbc/reference/develop-app/updating-data-overview.md)de la mise à jour des données.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Curseurs statiques dans ODBC](../../../odbc/reference/develop-app/odbc-static-cursors.md)  
  
-   [Curseurs dynamiques dans ODBC](../../../odbc/reference/develop-app/odbc-dynamic-cursors.md)  
  
-   [Curseurs de jeu de clés](../../../odbc/reference/develop-app/keyset-driven-cursors.md)  
  
-   [Curseurs mixtes](../../../odbc/reference/develop-app/mixed-cursors.md)
