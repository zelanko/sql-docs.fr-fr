---
title: SQL_NO_DATA | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- application upgrades [ODBC], SQL_NO_DATA
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
- upgrading applications [ODBC], SQL_NO_DATA
ms.assetid: 07a4144a-a548-4578-b2be-715c3cf73bf8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4c42213c629c5fa79cd5c6522f4a36f29f36bd8c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlnodata"></a>SQL_NO_DATA
Lorsqu’une application ODBC 3. *x* application appelle **SQLExecDirect**, **SQLExecute**, ou **SQLParamData** dans une API ODBC 2. *x* pilote, pour exécuter une recherche de la mise à jour ou supprimez l’instruction qui n’affecte pas les lignes à la source de données, le pilote doit retourner SQL_SUCCESS, pas SQL_NO_DATA. Lorsqu’une application ODBC 2. *x* ou ODBC 3. *x* application utilisant une ODBC 3. *x* pilote appelle **SQLExecDirect**, **SQLExecute**, ou **SQLParamData** avec le même résultat, la version ODBC 3. *x* pilote doit retourner SQL_NO_DATA.

