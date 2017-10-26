---
title: "Vue d’ensemble des données de mise à jour | Documents Microsoft"
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
- updating data [ODBC], about updating data
- data updates [ODBC]
- updating data [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 062036a4-cda6-4aaa-9765-f1ec3e0b31b1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3da35917f3979b041d6eb5b61d6554d4ef4c4585
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="updating-data-overview"></a>Vue d’ensemble des données de mise à jour
Les applications peuvent mettre à jour les données en exécutant des instructions SQL ou en appelant **SQLSetPos** ou **SQLBulkOperations**. **Mise à jour**, **supprimer**, et **insérer** instructions agir directement sur la source de données et sont généralement prises en charge par les pilotes. Recherche des mises à jour et les instructions delete contient une spécification des lignes à modifier. Positionné mise à jour et supprimer des instructions et **SQLSetPos** agissent sur la source de données via un curseur et sont moins couramment pris en charge.  
  
 Si les curseurs peuvent détecter les modifications apportées à un jeu de résultats avec les méthodes décrites dans cette section varie selon le type du curseur et comment il est implémenté. Les curseurs avant uniquement ne pas réexaminer des lignes et par conséquent, ne détectent pas les modifications. Pour savoir si les curseurs de défilement peuvent détecter des modifications, consultez [curseurs permettant le défilement](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Les instructions INSERT, DELETE et UPDATE](../../../odbc/reference/develop-app/update-delete-and-insert-statements.md)  
  
-   [Mise à jour positionnée et les instructions Delete](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)  
  
-   [Simulation d’instructions Delete et mise à jour positionnée](../../../odbc/reference/develop-app/simulating-positioned-update-and-delete-statements.md)  
  
-   [Déterminer le nombre de lignes affectées](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)  
  
-   [Mise à jour des données avec SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)  
  
-   [Mise à jour des données avec SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)  
  
-   [Données de type long et SQLSetPos et SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)

