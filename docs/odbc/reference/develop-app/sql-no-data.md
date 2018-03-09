---
title: SQL_NO_DATA | Documents Microsoft
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
- SQL_NO_DATA [ODBC]
- application upgrades [ODBC], SQL_NO_DATA
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
- upgrading applications [ODBC], SQL_NO_DATA
ms.assetid: 07a4144a-a548-4578-b2be-715c3cf73bf8
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: da9e5ffc19d884d2cb182190e11ba4dcf0a915bd
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sqlnodata"></a>SQL_NO_DATA
Lorsqu’une application ODBC 3. *x* application appelle **SQLExecDirect**, **SQLExecute**, ou **SQLParamData** dans une API ODBC 2. *x* pilote, pour exécuter une recherche de la mise à jour ou supprimez l’instruction qui n’affecte pas les lignes à la source de données, le pilote doit retourner SQL_SUCCESS, pas SQL_NO_DATA. Lorsqu’une application ODBC 2. *x* ou ODBC 3. *x* application utilisant une ODBC 3. *x* pilote appelle **SQLExecDirect**, **SQLExecute**, ou **SQLParamData** avec le même résultat, la version ODBC 3. *x* pilote doit retourner SQL_NO_DATA.
