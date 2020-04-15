---
title: Mise à jour de l’aperçu des données (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], about updating data
- data updates [ODBC]
- updating data [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 062036a4-cda6-4aaa-9765-f1ec3e0b31b1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9972ab61f041385ae4ca616df093ae63ad7a47d9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300385"
---
# <a name="updating-data-overview"></a>Vue d’ensemble de la mise à jour des données
Les applications peuvent mettre à jour les données soit en exécutant des relevés SQL, soit en appelant **SQLSetPos** ou **SQLBulkOperations**. **UPDATE**, **DELETE**, et **insert** déclarations agissent directement sur la source de données et sont généralement pris en charge par les conducteurs. Les instructions de mise à jour et de suppression recherchées contiennent une spécification des lignes à modifier. Mises à jour et suppressions de relevés positionnés et **SQLSetPos** agissent sur la source de données par l’intermédiaire d’un curseur et sont moins largement pris en charge.  
  
 La question de savoir si les curseurs peuvent détecter les modifications apportées à l’ensemble de résultats avec les méthodes décrites dans cette section dépend du type de curseur et de la façon dont il est implémenté. Les curseurs avant-seulement ne revisitent pas les lignes et ne détectent donc aucun changement. Pour savoir si les curseurs défilementables peuvent détecter les changements, voir [Cursesors défilants](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Instructions UPDATE, DELETE et INSERT](../../../odbc/reference/develop-app/update-delete-and-insert-statements.md)  
  
-   [Instructions de mise à jour et de suppression positionnées](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)  
  
-   [Simulation d’instructions de mise à jour et de suppression positionnées](../../../odbc/reference/develop-app/simulating-positioned-update-and-delete-statements.md)  
  
-   [Détermination du nombre de lignes affectées](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)  
  
-   [Mise à jour de données avec SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)  
  
-   [Mise à jour de données avec SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)  
  
-   [Données de type Long, et SQLSetPos et SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)
