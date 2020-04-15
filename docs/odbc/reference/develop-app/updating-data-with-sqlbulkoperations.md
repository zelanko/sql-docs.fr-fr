---
title: Mise à jour des données avec SQLBulkOperations (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298483"
---
# <a name="updating-data-with-sqlbulkoperations"></a>Mise à jour de données avec SQLBulkOperations
Les applications peuvent effectuer des opérations de mise à jour, de suppression, d’aller chercher ou d’insertion en vrac sur la table sous-jacente à la source de données avec un appel à **SQLBulkOperations**. Appeler **SQLBulkOperations** est une alternative pratique à la construction et à l’exécution d’une déclaration SQL. Il permet à un conducteur ODBC de prendre en charge les mises à jour positionnées même lorsque la source de données ne prend pas en charge les déclarations SQL positionnées. Il fait partie du paradigme de l’accès complet de base de données au moyen d’appels de fonction.  
  
 **SQLBulkOperations** fonctionne sur le ramset actuel et ne peut être utilisé qu’après un appel à **SQLFetch** ou **SQLFetchScroll**. L’application spécifie les lignes pour mettre à jour, supprimer ou rafraîchir en cachant leurs signets. Le conducteur récupère les nouvelles données pour que les lignes soient mises à jour, ou les nouvelles données à insérer dans le tableau sous-jacent, à partir des tampons encastrés.  
  
 La taille de la ligne à utiliser par **SQLBulkOperations** est réglée par un appel à **SQLSetStmtAttr** avec un argument *d’attribut* de SQL_ATTR_ROW_ARRAY_SIZE. Contrairement à **SQLSetPos**, qui utilise une nouvelle taille de rowset seulement après un appel à **SQLFetch** ou **SQLFetchScroll**, **SQLBulkOperations** utilise la nouvelle taille rowset après l’appel à **SQLSetStmtAttrAttr**.  
  
 Étant donné que la plupart des interactions avec les bases de données relationnelles se font par l’intermédiaire de **SQL, SQLBulkOperations** n’est pas largement soutenue. Cependant, un pilote peut facilement l’imiter en construisant et en exécutant une **mise À JOUR**, **SUPPRIMER**, ou **insert** statement.  
  
 Pour déterminer quelles opérations **SQLBulkOperation** prend en charge, une application appelle **SQLGetInfo** avec la SQL_DYNAMIC_CURSOR_ATTRIBUTES1, la SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, la SQL_KEYSET_CURSOR_ATTRIBUTES1 ou SQL_STATIC_CURSOR_ATTRIBUTES1 option d’information (selon le type de curseur).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Mise à jour de lignes par signet avec SQLBulkOperations](../../../odbc/reference/develop-app/updating-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Suppression de lignes par signet avec SQLBulkOperations](../../../odbc/reference/develop-app/deleting-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Insertion de lignes avec SQLBulkOperations](../../../odbc/reference/develop-app/inserting-rows-with-sqlbulkoperations.md)  
  
-   [Extraction de lignes avec SQLBulkOperations](../../../odbc/reference/develop-app/fetching-rows-with-sqlbulkoperations.md)
