---
title: Prise en charge (le pilote ODBC Visual FoxPro) des signets | Documents Microsoft
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
- FoxPro ODBC driver [ODBC], bookmarks
- Visual FoxPro ODBC driver [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: feb7ec20-3e0c-4a47-8feb-7dd9f23efdf6
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2e9d9816240836ee2b8b5c69ae49559a1fe6d625
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="bookmark-support-visual-foxpro-odbc-driver"></a>Prise en charge des signets (le pilote ODBC Visual FoxPro)
Le pilote ODBC Visual FoxPro prend en charge les signets simples. Lorsque vous appelez [SQLGetInfo](../../odbc/microsoft/sqlgetinfo-visual-foxpro-odbc-driver.md) avec la SQL_BOOKMARK_PERSISTENCE *InfoType*, la valeur de retour est SQL_BP_SCROLL.  
  
 Pour plus d’informations sur les signets, consultez [signets (ODBC)](../../odbc/reference/develop-app/bookmarks-odbc.md).
