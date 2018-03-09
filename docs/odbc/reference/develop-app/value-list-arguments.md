---
title: Valeur des Arguments de la liste | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], value list
- value list arguments [ODBC]
ms.assetid: 863837be-603b-4c7a-8b96-b71014037ee5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 15604e317105982c5011b31096934e32bea98e11
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="value-list-arguments"></a>Arguments de liste de valeurs
Un argument de la liste valeur se compose d’une liste de valeurs séparées par des virgules à utiliser pour la correspondance. Il est argument de liste qu’une seule valeur dans les fonctions de catalogue ODBC : le *TableType* argument dans **SQLTables**. Paramètre *TableType* à un pointeur null est le même que si elle est définie à SQL_ALL_TABLE_TYPES, qui énumère tous les membres possibles de la liste de valeurs. Cet argument n’est pas affecté par l’attribut d’instruction SQL_ATTR_METADATA_ID. Pour plus d’informations, consultez la [SQLTables](../../../odbc/reference/syntax/sqltables-function.md) description de fonction.
