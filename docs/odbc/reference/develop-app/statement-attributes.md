---
title: Attributs de déclarations Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], statement attributes
- statement attributes [ODBC]
ms.assetid: 4c59cd8e-a713-4095-9065-20d5bdeafe43
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec24cc43e8c57e47ddda9f20fac1807f42453e84
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299642"
---
# <a name="statement-attributes"></a>Attributs d'instruction
Les attributs de l’énoncé sont les caractéristiques de l’énoncé. Par exemple, s’il faut utiliser des signets et quel type de curseur utiliser avec l’ensemble de résultats de l’instruction sont des attributs de déclaration.  
  
 Les attributs d’énoncé sont définis avec **SQLSetStmtAttr** et leurs paramètres actuels récupérés avec **SQLGetStmtAttr**. Il n’est pas nécessaire qu’une demande définisse des attributs de déclaration; tous les attributs de déclaration ont des défauts, dont certains sont spécifiques au conducteur.  
  
 Quand un attribut d’instruction peut être défini dépend de l’attribut lui-même. Les attributs de SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR et SQL_ATTR_USE_BOOKMARKS doivent être définis avant l’exécution de la déclaration. Les attributs SQL_ATTR_ASYNC_ENABLE et SQL_ATTR_NOSCAN instruction peuvent être définis à tout moment, mais ne sont pas appliqués jusqu’à ce que l’instruction soit utilisée à nouveau. SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS et SQL_ATTR_QUERY_TIMEOUT attributs de déclaration peuvent être définis à tout moment, mais il est spécifique au conducteur s’ils sont appliqués avant que l’instruction soit utilisée à nouveau. Les attributs restants peuvent être définis à tout moment.  
  
> [!NOTE]  
>  La possibilité de définir les attributs de déclaration au niveau de connexion en appelant **SQLSetConnectAttr** a été amortie dans ODBC 3. *x*. ODBC 3. *x* les applications ne doivent jamais définir les attributs de l’instruction au niveau de connexion. ODBC 3. *x* les conducteurs n’ont besoin de prendre en charge cette fonctionnalité que s’ils doivent travailler avec ODBC 2. *x* applications. Pour plus d’informations, consultez [SQLSetConnectOption Mapping](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md) dans l’annexe G: Driver Guidelines for Backward Compatibility.  
>   
>  Une exception à cela est le SQL_ATTR_METADATA_ID et SQL_ATTR_ASYNC_ENABLE attributs, qui sont à la fois attributs de connexion et attributs de déclaration et peuvent être définis soit au niveau de connexion ou au niveau de l’instruction.  
>   
>  Aucun des attributs de déclaration introduits dans ODBC 3. *x* (sauf pour SQL_ATTR_METADATA_ID) peut être réglé au niveau de connexion.  
  
 Pour plus d’informations, consultez la description de la fonction [SQLSetStmtAttr.](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)
