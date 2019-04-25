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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 958514adc02452cdc75a05e7ad28cd31f4e8e0e6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62632442"
---
# <a name="updating-data-with-sqlbulkoperations"></a>Mise à jour de données avec SQLBulkOperations
Applications peuvent effectuer des opérations de mise à jour, suppression, fetch ou d’insertion en bloc sur la table sous-jacente à la source de données avec un appel à **SQLBulkOperations**. Appel **SQLBulkOperations** est une alternative pratique à la construction et l’exécution d’une instruction SQL. Il permet à un pilote ODBC prend en charge les mises à jour positionnées même lorsque la source de données ne prend pas en charge les instructions SQL positionnées. Il fait partie du paradigme de la réalisation d’accès de base de données complète au moyen d’appels de fonction.  
  
 **SQLBulkOperations** opère sur l’ensemble de lignes en cours et peut être utilisé uniquement après un appel à **SQLFetch** ou **SQLFetchScroll**. L’application spécifie les lignes à supprimer, mettre à jour ou actualiser en mettant en cache leurs signets. Le pilote récupère les nouvelles données pour les lignes à mettre à jour ou les nouvelles données à insérer dans la table sous-jacente, à partir de mémoires tampons de l’ensemble de lignes.  
  
 La taille de l’ensemble de lignes à utiliser par **SQLBulkOperations** est défini par un appel à **SQLSetStmtAttr** avec un *attribut* argument de SQL_ATTR_ROW_ARRAY_SIZE. Contrairement aux **SQLSetPos**, qui utilise une nouvelle taille de l’ensemble de lignes uniquement après un appel à **SQLFetch** ou **SQLFetchScroll**, **SQLBulkOperations** utilise le nouvelle taille d’ensemble de lignes après l’appel à **SQLSetStmtAttr**.  
  
 Étant donné que la plupart des interactions avec les bases de données relationnelles sont effectuée via SQL, **SQLBulkOperations** n’est pas largement pris en charge. Toutefois, un pilote peut il émuler facilement en créant et en exécutant un **mise à jour**, **supprimer**, ou **insérer** instruction.  
  
 Pour déterminer quelles opérations **SQLBulkOperation** prend en charge, une application appelle **SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR _ATTRIBUTES1 ou l’option d’informations SQL_STATIC_CURSOR_ATTRIBUTES1 (selon le type du curseur).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Mise à jour de lignes par signet avec SQLBulkOperations](../../../odbc/reference/develop-app/updating-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Suppression de lignes par signet avec SQLBulkOperations](../../../odbc/reference/develop-app/deleting-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Insertion de lignes avec SQLBulkOperations](../../../odbc/reference/develop-app/inserting-rows-with-sqlbulkoperations.md)  
  
-   [Extraction de lignes avec SQLBulkOperations](../../../odbc/reference/develop-app/fetching-rows-with-sqlbulkoperations.md)
