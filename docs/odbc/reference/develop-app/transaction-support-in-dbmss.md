---
title: Prise en charge de la transaction dans le SGBD | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 0fc2ae34-4748-4120-9fc3-bb28c8ed867e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4dea29ad82564aa30bdc0c4dbacd3e560ff7e271
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="transaction-support-in-dbmss"></a>Prise en charge de la transaction dans le SGBD
Certaines bases de données, en particulier bureau comme dBASE, Paradox et Btrieve, ne gèrent pas les transactions. Même entre les bases de données qui prennent en charge des transactions, il est une variation de types d’instructions SQL qui peuvent être dans une transaction. Pour plus d’informations, consultez l’option SQL_TXN_CAPABLE dans le [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) description de fonction.
