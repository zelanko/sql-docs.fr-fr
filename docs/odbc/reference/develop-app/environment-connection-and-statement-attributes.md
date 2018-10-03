---
title: Environnement, la connexion et les attributs d’instruction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e77be71458eb10e97a82c925d34141a7bcaf1dc4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47685930"
---
# <a name="environment-connection-and-statement-attributes"></a>Attributs d’environnement, de connexion et d’instruction
ODBC définit un nombre d’attributs qui sont associés à des environnements, des connexions ou des instructions.  
  
 Attributs d’environnement affectent tout l’environnement, telles que si le regroupement de connexions est activé. Attributs d’environnement sont définies avec **SQLSetEnvAttr** et récupérées avec **SQLGetEnvAttr**.  
  
 Attributs de connexion affectent chaque connexion individuellement, telles que la durée pendant laquelle un pilote doit attendre lorsque vous tentez de vous connecter à une source de données avant l’expiration. Attributs de connexion sont définis avec **SQLSetConnectAttr** et récupérées avec **SQLGetConnectAttr**. Pour plus d’informations sur les attributs de connexion, consultez [attributs de connexion](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Attributs d’instruction affectent chaque instruction individuellement, par exemple si une instruction doit être exécutée de façon asynchrone. Attributs d’instruction sont définis avec **SQLSetStmtAttr** et récupérées avec **SQLGetStmtAttr**. Quelques attributs d’instruction sont des attributs en lecture seule et ne peut pas être définies. Par exemple, l’attribut d’instruction SQL_ATTR_ROW_NUMBER, qui est utilisé pour récupérer le numéro de la ligne actuelle dans le curseur, est en lecture seule. Pour plus d’informations sur les attributs d’instruction, consultez [les attributs d’instruction](../../../odbc/reference/develop-app/statement-attributes.md).  
  
 En plus des attributs définis par ODBC, un pilote peut définir ses propres connexions et les attributs d’instruction. Attributs définis par le pilote doivent être inscrit avec Open Group pour vous assurer que les deux fournisseurs de pilote n’affectez pas de la même valeur d’entier à des attributs différents, propriétaires. Pour plus d’informations, consultez [les Types de données spécifiques au pilote, Types de descripteurs, Types d’informations, Types de diagnostics et attributs](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Pour obtenir une liste complète des attributs, consultez [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), et [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md). La plupart des attributs sont également décrits dans la description de la fonction ODBC qu’elles affectent.
