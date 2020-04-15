---
title: Types de curseurs défilants (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304230"
---
# <a name="scrollable-cursor-types"></a>Types de curseurs avec défilement
Les quatre types de curseurs défilementables sont statiques, dynamiques, pilotés par les clés et mélangés. Les curseurs statiques détectent peu ou pas de changements, mais sont relativement bon marché à mettre en œuvre. Les curseurs dynamiques détectent tous les changements mais sont coûteux à mettre en œuvre. Les curseurs mixtes et à clé se trouvent entre les deux, détectant la plupart des changements, mais à moindre coût que les curseurs dynamiques.  
  
 Les termes suivants sont utilisés pour définir les caractéristiques de chaque type de curseur défilementable :  
  
-   **Propres mises à jour, suppressions et inserts.** Mises à jour, suppressions et inserts effectués par le curseur, soit avec un appel à **SQLBulkOperations** ou **SQLSetPos** ou avec une mise à jour ou supprimer l’instruction.  
  
-   **Autres mises à jour, suppressions et inserts.** Mises à jour, suppressions et encarts non effectués par le curseur, y compris ceux effectués par d’autres opérations dans la même transaction, ceux effectués par le biais d’autres transactions, et ceux effectués par d’autres applications.  
  
-   **Adhésion.** L’ensemble de lignes dans l’ensemble de résultat.  
  
-   **commande.** L’ordre dans lequel les rangées sont retournées par le curseur.  
  
-   **Valeurs.** Les valeurs dans chaque rangée dans l’ensemble de résultat.  
  
 Pour plus d’informations sur la façon de mettre à jour, supprimer et insérer des données, voir [Mise à jour de l’aperçu des données](../../../odbc/reference/develop-app/updating-data-overview.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Curseurs statiques dans ODBC](../../../odbc/reference/develop-app/odbc-static-cursors.md)  
  
-   [Curseurs dynamiques dans ODBC](../../../odbc/reference/develop-app/odbc-dynamic-cursors.md)  
  
-   [Curseurs de jeu de clés](../../../odbc/reference/develop-app/keyset-driven-cursors.md)  
  
-   [Curseurs mixtes](../../../odbc/reference/develop-app/mixed-cursors.md)
