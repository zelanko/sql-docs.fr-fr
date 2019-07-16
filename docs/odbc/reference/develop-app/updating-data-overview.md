---
title: Vue d’ensemble des données de la mise à jour | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0701218b5ef489d1f8962ffadc9409986a0c36c7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942816"
---
# <a name="updating-data-overview"></a>Vue d’ensemble de la mise à jour des données
Les applications peuvent mettre à jour les données en exécutant des instructions SQL ou en appelant **SQLSetPos** ou **SQLBulkOperations**. **Mise à jour**, **supprimer**, et **insérer** instructions agir directement sur la source de données et sont généralement prises en charge par les pilotes. Rechercher les mises à jour et les instructions delete contient une spécification des lignes à modifier. Positionné de mise à jour et supprimer des instructions et **SQLSetPos** agissent sur la source de données via un curseur et sont moins couramment pris en charge.  
  
 Si les curseurs peuvent détecter les modifications apportées à l’ensemble de résultats avec les méthodes décrites dans cette section varie selon le type du curseur et comment il est implémenté. Curseurs avant uniquement et ne pas réexaminer les lignes et par conséquent ne détectent pas les modifications. Pour savoir si les curseurs avec défilement peuvent détecter des modifications, consultez [curseurs avec défilement](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Instructions UPDATE, DELETE et INSERT](../../../odbc/reference/develop-app/update-delete-and-insert-statements.md)  
  
-   [Instructions de mise à jour et de suppression positionnées](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)  
  
-   [Simulation d’instructions de mise à jour et de suppression positionnées](../../../odbc/reference/develop-app/simulating-positioned-update-and-delete-statements.md)  
  
-   [Détermination du nombre de lignes affectées](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)  
  
-   [Mise à jour de données avec SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)  
  
-   [Mise à jour de données avec SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)  
  
-   [Données de type Long, et SQLSetPos et SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)
