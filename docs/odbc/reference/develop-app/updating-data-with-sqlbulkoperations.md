---
title: Mise à jour des données avec SQLBulkOperations | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBulkOperations function [ODBC], updating data
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: 7645a704-341e-4267-adbe-061a9fda225b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9b96e3a43b8385910e4260cf51dea7e4ff508200
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298483"
---
# <a name="updating-data-with-sqlbulkoperations"></a>Mise à jour de données avec SQLBulkOperations
Les applications peuvent effectuer des opérations de mise à jour, de suppression, d’extraction ou d’insertion en bloc sur la table sous-jacente au niveau de la source de données à l’aide d’un appel à **SQLBulkOperations**. L’appel de **SQLBulkOperations** est une alternative pratique à la construction et à l’exécution d’une instruction SQL. Il permet à un pilote ODBC de prendre en charge les mises à jour positionnées même lorsque la source de données ne prend pas en charge les instructions SQL positionnées. Il fait partie du paradigme d’obtention d’un accès complet à la base de données au moyen d’appels de fonction.  
  
 **SQLBulkOperations** opère sur l’ensemble de lignes actuel et peut être utilisé uniquement après un appel à **SQLFetch** ou **SQLFetchScroll**. L’application spécifie les lignes à mettre à jour, à supprimer ou à actualiser en mettant en cache leurs signets. Le pilote récupère les nouvelles données pour les lignes à mettre à jour, ou les nouvelles données à insérer dans la table sous-jacente, à partir des mémoires tampons de l’ensemble de lignes.  
  
 La taille de l’ensemble de lignes à utiliser par **SQLBulkOperations** est définie par un appel à **SQLSetStmtAttr** avec un argument d' *attribut* de SQL_ATTR_ROW_ARRAY_SIZE. Contrairement à **SQLSetPos**, qui utilise une nouvelle taille d’ensemble de lignes uniquement après un appel à **SQLFetch** ou **SQLFetchScroll**, **SQLBulkOperations** utilise la nouvelle taille d’ensemble de lignes après l’appel à **SQLSetStmtAttr**.  
  
 Étant donné que la plupart des interactions avec les bases de données relationnelles s’effectuent par le biais de SQL, **SQLBulkOperations** n’est pas largement pris en charge. Toutefois, un pilote peut facilement l’émuler en construisant et en exécutant une instruction **Update**, **Delete**ou **Insert** .  
  
 Pour déterminer les opérations prises en charge par **SQLBulkOperation** , une application appelle **SQLGetInfo** avec l’option d’informations SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 ou SQL_STATIC_CURSOR_ATTRIBUTES1 (selon le type du curseur).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Mise à jour de lignes par signet avec SQLBulkOperations](../../../odbc/reference/develop-app/updating-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Suppression de lignes par signet avec SQLBulkOperations](../../../odbc/reference/develop-app/deleting-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Insertion de lignes avec SQLBulkOperations](../../../odbc/reference/develop-app/inserting-rows-with-sqlbulkoperations.md)  
  
-   [Extraction de lignes avec SQLBulkOperations](../../../odbc/reference/develop-app/fetching-rows-with-sqlbulkoperations.md)
