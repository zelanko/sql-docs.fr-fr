---
title: Plusieurs instructions actives et connexions | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], multiple active statements and connections
- multiple active statements and connections [ODBC]
ms.assetid: a6571356-b23e-4f10-a17b-bce09460b71e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 76b74ff748a62a401955e4ea4a995f507314124e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67942826"
---
# <a name="multiple-active-statements-and-connections"></a>Instructions et connexions multiples actives simultanément
Certains pilotes et SGBD limitent le nombre d’instructions et de connexions qui peuvent être actives en même temps. Ces nombres peuvent être aussi petits qu’un seul. Pour plus d’informations, consultez les options SQL_MAX_CONCURRENT_ACTIVITIES et SQL_MAX_DRIVER_CONNECTIONS dans la description de la fonction [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) , et les [Handles d’instructions](../../../odbc/reference/develop-app/statement-handles.md) et les [Handles de connexion](../../../odbc/reference/develop-app/connection-handles.md).
