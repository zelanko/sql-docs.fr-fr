---
title: Prise en charge des transactions dans les SGBD | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 72353e9917996ecacdc5971b4a11f9c73718ba43
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037634"
---
# <a name="transaction-support-in-dbmss"></a>Prise en charge des transactions dans les SGBD
Certaines bases de données, notamment les bases de données de bureau telles que dBASE, Paradox et Btrieve, ne prennent pas en charge les transactions. Même entre les bases de données qui prennent en charge les transactions, il existe des variations dans les types d’instructions SQL qui peuvent être dans une transaction. Pour plus d’informations, consultez l’option SQL_TXN_CAPABLE dans la description de la fonction [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) .
