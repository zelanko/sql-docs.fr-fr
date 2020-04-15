---
title: Mise à jour des données avec SQLSetPos (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 16476a1e1007905f34ec2e70ce6032eb8d81fe7a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286159"
---
# <a name="updating-data-with-sqlsetpos"></a>Mise à jour de données avec SQLSetPos
Les applications peuvent mettre à jour ou supprimer n’importe quelle ligne dans le rowset avec **SQLSetPos**. Appeler **SQLSetPos** est une alternative pratique à la construction et à l’exécution d’une déclaration SQL. Il permet à un conducteur ODBC de prendre en charge les mises à jour positionnées même lorsque la source de données ne prend pas en charge les déclarations SQL positionnées. Il fait partie du paradigme de l’accès complet de base de données au moyen d’appels de fonction.  
  
 **SQLSetPos** fonctionne sur le rowset actuel et ne peut être utilisé qu’après un appel à **SQLFetchScroll**. L’application précise le nombre de lignes à mettre à jour, supprimer ou insérer, et le pilote récupère les nouvelles données pour cette ligne à partir des tampons rowset. **SQLSetPos** peut également être utilisé pour désigner une rangée spécifiée comme la ligne actuelle, ou pour rafraîchir une rangée particulière dans le rame de la source de données.  
  
 La taille de Rowset est réglée par un appel à **SQLSetStmtAttr** avec un argument *d’attribut* de SQL_ATTR_ROW_ARRAY_SIZE. **SQLSetPos** utilise toutefois une nouvelle taille de rowset, seulement après un appel à **SQLFetch** ou **SQLFetchScroll**. Par exemple, si la taille de l’aviron est modifiée, **SQLSetPos** est appelé, puis **SQLFetch** ou **SQLFetchScroll** est appelé, et l’appel à **SQLSetPos** utilise l’ancienne taille de rowset tandis que **SQLFetch ou** **SQLFetchScroll** utilise la nouvelle taille de ramset.  
  
 La première ligne de l'ensemble de lignes porte le numéro 1. *L’argument de RowNumber* dans **SQLSetPos** doit identifier une rangée dans le rangée; c’est-à-dire que sa valeur doit être de l’ordre de 1 à 1 et du nombre de rangées qui ont été récupérées le plus récemment (ce qui peut être inférieur à la taille du rowset). Si *RowNumber* est 0, l’opération s’applique à chaque rangée dans le ramage.  
  
 Étant donné que la plupart des interactions avec les bases de données relationnelles se font par l’intermédiaire de SQL, **SQLSetPos** n’est pas largement pris en charge. Cependant, un pilote peut facilement l’imiter en construisant et en exécutant une **déclaration UPDATE** ou **DELETE.**  
  
 Pour déterminer quelles opérations **SQLSetPos** prend en charge, une application appelle **SQLGetInfo** avec la SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 ou SQL_STATIC_CURSOR_ATTRIBUTES1 option d’information (selon le type de curseur).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Mise à jour de lignes dans l’ensemble de lignes avec SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)  
  
-   [Suppression de lignes dans l’ensemble de lignes avec SQLSetPos](../../../odbc/reference/develop-app/deleting-rows-in-the-rowset-with-sqlsetpos.md)
