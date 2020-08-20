---
description: Prise en charge des transactions dans les SGBD
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b8e0b3433e0f666af100cce5e72e36b685533b1d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487452"
---
# <a name="transaction-support-in-dbmss"></a>Prise en charge des transactions dans les SGBD
Certaines bases de données, notamment les bases de données de bureau telles que dBASE, Paradox et Btrieve, ne prennent pas en charge les transactions. Même entre les bases de données qui prennent en charge les transactions, il existe des variations dans les types d’instructions SQL qui peuvent être dans une transaction. Pour plus d’informations, consultez l’option SQL_TXN_CAPABLE dans la description de la fonction [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) .
