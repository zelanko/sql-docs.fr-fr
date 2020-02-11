---
title: Mise à jour des données avec SQLSetPos | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
- SQLSetPos function [ODBC], updating data
ms.assetid: e9625b59-06a0-4883-b155-b932ba7528d9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d2895ec765df3910dbbaa1e76ba1579e4afe5cca
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68091653"
---
# <a name="updating-data-with-sqlsetpos"></a>Mise à jour de données avec SQLSetPos
Les applications peuvent mettre à jour ou supprimer n’importe quelle ligne de l’ensemble de lignes avec **SQLSetPos**. L’appel de **SQLSetPos** est une alternative pratique à la construction et à l’exécution d’une instruction SQL. Il permet à un pilote ODBC de prendre en charge les mises à jour positionnées même lorsque la source de données ne prend pas en charge les instructions SQL positionnées. Il fait partie du paradigme d’obtention d’un accès complet à la base de données au moyen d’appels de fonction.  
  
 **SQLSetPos** fonctionne sur l’ensemble de lignes actuel et peut être utilisé uniquement après un appel à **SQLFetchScroll**. L’application spécifie le numéro de la ligne à mettre à jour, à supprimer ou à insérer, et le pilote récupère les nouvelles données pour cette ligne à partir des mémoires tampons de l’ensemble de lignes. **SQLSetPos** peut également être utilisé pour désigner une ligne spécifiée comme ligne actuelle ou pour actualiser une ligne particulière de l’ensemble de lignes à partir de la source de données.  
  
 La taille de l’ensemble de lignes est définie par un appel à **SQLSetStmtAttr** avec un argument d' *attribut* de SQL_ATTR_ROW_ARRAY_SIZE. **SQLSetPos** utilise une nouvelle taille d’ensemble de lignes, toutefois, uniquement après un appel à **SQLFetch** ou **SQLFetchScroll**. Par exemple, si la taille de l’ensemble de lignes est modifiée, **SQLSetPos** est appelé, puis **SQLFetch** ou **SQLFetchScroll** est appelé, et l’appel à **SQLSetPos** utilise l’ancienne taille de l’ensemble de lignes tandis que **SQLFetch** ou **SQLFetchScroll** utilise la nouvelle taille de l’ensemble de lignes.  
  
 La première ligne de l'ensemble de lignes porte le numéro 1. L’argument *RowNumber* dans **SQLSetPos** doit identifier une ligne dans l’ensemble de lignes ; autrement dit, sa valeur doit être comprise entre 1 et le nombre de lignes récupérées le plus récemment (ce qui peut être inférieur à la taille de l’ensemble de lignes). Si *RowNumber* a la valeur 0, l’opération s’applique à chaque ligne de l’ensemble de lignes.  
  
 Étant donné que la plupart des interactions avec les bases de données relationnelles s’effectuent par le biais de SQL, **SQLSetPos** n’est pas largement pris en charge. Toutefois, un pilote peut facilement l’émuler en construisant et en exécutant une instruction **Update** ou **Delete** .  
  
 Pour déterminer les opérations que **SQLSetPos** prend en charge, une application appelle **SQLGetInfo** avec l’option d’informations SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 ou SQL_STATIC_CURSOR_ATTRIBUTES1 (selon le type du curseur).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Mise à jour de lignes dans l’ensemble de lignes avec SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)  
  
-   [Suppression de lignes dans l’ensemble de lignes avec SQLSetPos](../../../odbc/reference/develop-app/deleting-rows-in-the-rowset-with-sqlsetpos.md)
