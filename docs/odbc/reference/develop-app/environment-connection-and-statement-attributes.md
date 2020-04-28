---
title: Attributs d’environnement, de connexion et d’instruction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- environment attributes [ODBC]
- connection attributes [ODBC]
- statement attributes [ODBC]
ms.assetid: 9e15b276-3b7a-428a-b72f-a3ddfe1ba1ce
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 86cecaf0b82c7b6d15b3f37262507d2cff0c3c10
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300929"
---
# <a name="environment-connection-and-statement-attributes"></a>Attributs d’environnement, de connexion et d’instruction
ODBC définit un certain nombre d’attributs qui sont associés à des environnements, des connexions ou des instructions.  
  
 Les attributs d’environnement affectent l’ensemble de l’environnement, par exemple si le regroupement de connexions est activé. Les attributs d’environnement sont définis avec **SQLSetEnvAttr** et récupérés avec **SQLGetEnvAttr**.  
  
 Les attributs de connexion affectent chaque connexion individuellement, par exemple la durée pendant laquelle un pilote doit attendre lors de la tentative de connexion à une source de données avant le dépassement du délai d’attente. Les attributs de connexion sont définis avec **SQLSetConnectAttr** et récupérés avec **SQLGetConnectAttr**. Pour plus d’informations sur les attributs de connexion, consultez [attributs de connexion](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Les attributs d’instruction affectent chaque instruction individuellement, par exemple si une instruction doit être exécutée de façon asynchrone. Les attributs d’instruction sont définis avec **SQLSetStmtAttr** et récupérés avec **SQLGetStmtAttr**. Quelques attributs d’instruction sont des attributs en lecture seule et ne peuvent pas être définis. Par exemple, l’attribut d’instruction SQL_ATTR_ROW_NUMBER, qui est utilisé pour récupérer le numéro de la ligne actuelle dans le curseur, est en lecture seule. Pour plus d’informations sur les attributs d’instruction, consultez [attributs d’instruction](../../../odbc/reference/develop-app/statement-attributes.md).  
  
 Outre les attributs définis par ODBC, un pilote peut définir ses propres attributs de connexion et d’instruction. Les attributs définis par le pilote doivent être inscrits auprès d’Open Group pour garantir que deux fournisseurs de pilotes n’assignent pas la même valeur entière à des attributs propriétaires différents. Pour plus d’informations, consultez [types de données spécifiques au pilote, types de descripteurs, types d’informations, types de diagnostics et attributs](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Pour obtenir la liste complète des attributs, consultez [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)et [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md). La plupart des attributs sont également décrits dans la description de la fonction ODBC qu’ils affectent.
