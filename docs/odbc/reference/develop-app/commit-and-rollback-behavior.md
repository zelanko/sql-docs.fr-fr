---
title: La validation et le comportement de restauration | Documents Microsoft
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
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 2ac8f012-e46d-41ca-81bb-e4a3246e3241
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8e2bf47aa43ad68871a1c69a7f8b97ca608f8175
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="commit-and-rollback-behavior"></a>La validation et le comportement de restauration
Un comportement commun entre le serveur SGBD consiste à fermer les curseurs et ignorer les instructions préparées lorsqu’une instruction est validée ou restaurée. Bases de données bureautiques sont plus susceptibles de conserver les curseurs ouverts et la conservation des instructions préparées. Pour plus d’informations, consultez les options SQL_CURSOR_COMMIT_BEHAVIOR et SQL_CURSOR_ROLLBACK_BEHAVIOR dans les [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) description de fonction et [effet des Transactions sur les curseurs et des instructions préparées](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).
