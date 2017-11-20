---
title: Plusieurs instructions actives et connexions | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [ODBC], multiple active statements and connections
- multiple active statements and connections [ODBC]
ms.assetid: a6571356-b23e-4f10-a17b-bce09460b71e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 97976df0d7f0a237abd2e67ed71202ba4d518f3b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="multiple-active-statements-and-connections"></a>Plusieurs instructions actives et connexions
Des pilotes et un SGBD limite le nombre de connexions qui peuvent être actives en même temps et des instructions. Ces numéros peuvent être aussi petit qu’une. Pour plus d’informations, consultez les options SQL_MAX_CONCURRENT_ACTIVITIES et SQL_MAX_DRIVER_CONNECTIONS dans les [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) description, de fonction et [instruction gère](../../../odbc/reference/develop-app/statement-handles.md) et [Handles de connexion](../../../odbc/reference/develop-app/connection-handles.md).

