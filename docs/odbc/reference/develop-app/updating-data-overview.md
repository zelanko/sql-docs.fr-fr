---
description: Vue d’ensemble de la mise à jour des données
title: Présentation de la mise à jour des données | Microsoft Docs
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
ms.openlocfilehash: 2b1755ea75426030a96ed7b349cc82f0fc7e282a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424421"
---
# <a name="updating-data-overview"></a>Vue d’ensemble de la mise à jour des données
Les applications peuvent mettre à jour les données en exécutant des instructions SQL ou en appelant **SQLSetPos** ou **SQLBulkOperations**. Les instructions **Update**, **Delete**et **Insert** agissent directement sur la source de données et sont généralement prises en charge par les pilotes. Les instructions Update et Delete recherchées contiennent une spécification des lignes à modifier. Les instructions Update et DELETE positionnées et **SQLSetPos** agissent sur la source de données via un curseur et sont moins largement prises en charge.  
  
 Le fait que les curseurs puissent détecter les modifications apportées au jeu de résultats avec les méthodes décrites dans cette section dépend du type du curseur et de la façon dont il est implémenté. Les curseurs avant uniquement ne réexaminent pas les lignes et, par conséquent, ne détectent pas les modifications. Pour plus d’informations sur la possibilité de détecter les modifications, consultez [curseurs avec défilement](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Instructions UPDATE, DELETE et INSERT](../../../odbc/reference/develop-app/update-delete-and-insert-statements.md)  
  
-   [Instructions de mise à jour et de suppression positionnées](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)  
  
-   [Simulation d’instructions de mise à jour et de suppression positionnées](../../../odbc/reference/develop-app/simulating-positioned-update-and-delete-statements.md)  
  
-   [Détermination du nombre de lignes affectées](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)  
  
-   [Mise à jour de données avec SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)  
  
-   [Mise à jour de données avec SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)  
  
-   [Données de type Long, et SQLSetPos et SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)
