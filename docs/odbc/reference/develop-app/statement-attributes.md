---
title: Attributs d’instruction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e669f02eeb76ba529c75851ce8bf6ff9a7831a9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149104"
---
# <a name="statement-attributes"></a>Attributs d'instruction
Attributs d’instruction sont caractéristiques de l’instruction. Par exemple, s’il faut pour utiliser des signets et ce que type de curseur à utiliser avec le résultat de l’instruction sont des attributs d’instruction.  
  
 Attributs d’instruction sont définis avec **SQLSetStmtAttr** et leurs paramètres actuels sont récupérés avec **SQLGetStmtAttr**. Il n’est pas nécessaire qu’une application définir des attributs d’instruction ; tous les attributs d’instruction ont des valeurs par défaut, dont certaines sont spécifiques au pilote.  
  
 Lorsqu’un attribut d’instruction peut être défini dépend de l’attribut lui-même. Les attributs d’instruction SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR et SQL_ATTR_USE_BOOKMARKS doivent être définis avant l’exécution de l’instruction. Les attributs d’instruction SQL_ATTR_ASYNC_ENABLE et SQL_ATTR_NOSCAN peuvent être définies à tout moment, mais ne sont pas appliquées jusqu'à ce que l’instruction est utilisée à nouveau. Attributs d’instruction SQL_ATTR_MAX_LENGTH et SQL_ATTR_MAX_ROWS SQL_ATTR_QUERY_TIMEOUT peuvent être définies à tout moment, mais il est spécifique au pilote qu’ils sont appliqués avant l’instruction est utilisée à nouveau. Les attributs d’instruction restants peuvent être définis à tout moment.  
  
> [!NOTE]  
>  La possibilité de définir des attributs d’instruction au niveau de la connexion en appelant **SQLSetConnectAttr** a été déconseillée dans ODBC 3. *x*. ODBC 3. *x* applications ne doivent jamais définir les attributs d’instruction au niveau de la connexion. ODBC 3. *x* pilotes doivent prennent uniquement en charge cette fonctionnalité si elles doivent fonctionner avec ODBC 2. *x* applications. Pour plus d’informations, consultez [SQLSetConnectOption mappage](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md) dans g : annexe Instructions de pilote pour la compatibilité descendante.  
>   
>  Une exception concerne les attributs SQL_ATTR_METADATA_ID et SQL_ATTR_ASYNC_ENABLE, qui sont des attributs de connexion et les attributs d’instruction et peuvent être définies au niveau de la connexion ou le niveau de l’instruction.  
>   
>  Aucun des attributs d’instruction introduites dans ODBC 3. *x* (à l’exception SQL_ATTR_METADATA_ID) peut être définie au niveau de la connexion.  
  
 Pour plus d’informations, consultez le [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) description de fonction.
