---
title: Prise en charge le modèle d’accès concurrentiel (le pilote ODBC Visual FoxPro) | Documents Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], concurrency
- concurrency models [ODBC]
- FoxPro ODBC driver [ODBC], concurrency
ms.assetid: c39ed963-3af1-4888-8631-6083692ddcd7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 18f555f32ed05914d325ba4664e952d4488f787b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>Modèle d’accès concurrentiel pris en charge (le pilote ODBC Visual FoxPro)
Prend en charge par le pilote ODBC Visual FoxPro *concurrence en lecture seule*. Votre application peut appeler [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) avec une option SQL_CONCURRENCY de SQL_CONCUR_READ_ONLY.  
  
 Pour plus d’informations, consultez la [de référence du programmeur ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="read-only-concurrency"></a>concurrence d’accès en lecture seule  
 Le curseur ne peut pas être mis à jour.  
  
## <a name="row-versioning"></a>contrôle de version de ligne  
 Essentiellement timestamp prise en charge, dans la ligne qui les versions sont comparées au moment de la mise à jour.
