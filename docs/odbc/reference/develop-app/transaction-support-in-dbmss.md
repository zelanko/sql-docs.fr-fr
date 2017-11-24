---
title: Prise en charge de la transaction dans le SGBD | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 0fc2ae34-4748-4120-9fc3-bb28c8ed867e
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5785d2df5e9b1a3dccef92b8cf3e7996e88e6056
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="transaction-support-in-dbmss"></a>Prise en charge de la transaction dans le SGBD
Certaines bases de données, en particulier bureau comme dBASE, Paradox et Btrieve, ne gèrent pas les transactions. Même entre les bases de données qui prennent en charge des transactions, il est une variation de types d’instructions SQL qui peuvent être dans une transaction. Pour plus d’informations, consultez l’option SQL_TXN_CAPABLE dans le [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) description de fonction.
