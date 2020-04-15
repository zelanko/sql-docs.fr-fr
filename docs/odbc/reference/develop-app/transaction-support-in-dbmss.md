---
title: Support transactionnel dans les DBMS (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 0fc2ae34-4748-4120-9fc3-bb28c8ed867e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b6da6fdc819d8852aadcd7b672ef06e99d46c0ea
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298004"
---
# <a name="transaction-support-in-dbmss"></a>Prise en charge des transactions dans les SGBD
Certaines bases de données, en particulier les bases de données de bureau telles que dBASE, Paradox et Btrieve, ne prennent pas en charge les transactions. Même parmi les bases de données qui prennent en charge les transactions, il y a une variation dans les types d’instructions SQL peuvent être dans une transaction. Pour plus d’informations, consultez l’option SQL_TXN_CAPABLE dans la description de la fonction [SQLGetInfo.](../../../odbc/reference/syntax/sqlgetinfo-function.md)
