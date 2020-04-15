---
title: Attributs de l’environnement, de la connexion et de l’énoncé . Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300929"
---
# <a name="environment-connection-and-statement-attributes"></a>Attributs d’environnement, de connexion et d’instruction
ODBC définit un certain nombre d’attributs associés à des environnements, des connexions ou des énoncés.  
  
 Les attributs de l’environnement affectent l’ensemble de l’environnement, par exemple si la mise en commun des connexions est activée. Les attributs de l’environnement sont définis avec **SQLSetEnvAttr** et récupérés avec **SQLGetEnvAttr**.  
  
 Les attributs de connexion affectent chaque connexion individuellement, comme la durée d’attente d’un pilote tout en essayant de se connecter à une source de données avant de le moment. Les attributs de connexion sont définis avec **SQLSetConnectAttr** et récupérés avec **SQLGetConnectAttr**. Pour plus d’informations sur les attributs de connexion, voir [Attributs de connexion](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Les attributs de déclaration affectent chaque instruction individuellement, par exemple si une déclaration doit être exécutée asynchronement. Les attributs de déclaration sont définis avec **SQLSetStmtAttr** et récupérés avec **SQLGetStmtAttr**. Quelques attributs de déclaration sont des attributs de lecture seulement et ne peuvent pas être définis. Par exemple, l’attribut SQL_ATTR_ROW_NUMBER déclaration, qui est utilisé pour récupérer le nombre de la rangée actuelle dans le curseur, est lu uniquement. Pour plus d’informations sur les attributs des relevés, voir [Attributs d’énoncé .](../../../odbc/reference/develop-app/statement-attributes.md)  
  
 En plus des attributs définis par ODBC, un conducteur peut définir ses propres attributs de connexion et de déclaration. Les attributs définis par le conducteur doivent être enregistrés auprès d’Open Group pour s’assurer que deux fournisseurs de pilotes n’attribuent pas la même valeur integer à des attributs propriétaires différents. Pour plus d’informations, consultez [les types de données spécifiques au conducteur, les types descripteurs, les types d’information, les types de diagnostic et les attributs](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Pour une liste complète des attributs, voir [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), et [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md). La plupart des attributs sont également décrits dans la description de la fonction ODBC qu’ils affectent.
