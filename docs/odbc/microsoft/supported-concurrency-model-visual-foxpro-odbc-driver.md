---
title: "Prise en charge le modèle d’accès concurrentiel (le pilote ODBC Visual FoxPro) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], concurrency
- concurrency models [ODBC]
- FoxPro ODBC driver [ODBC], concurrency
ms.assetid: c39ed963-3af1-4888-8631-6083692ddcd7
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e06adec755df6c412d13fd8c2b892db8977b3a53
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>Modèle d’accès concurrentiel pris en charge (le pilote ODBC Visual FoxPro)
Prend en charge par le pilote ODBC Visual FoxPro *concurrence en lecture seule*. Votre application peut appeler [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) avec une option SQL_CONCURRENCY de SQL_CONCUR_READ_ONLY.  
  
 Pour plus d’informations, consultez la [de référence du programmeur ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="read-only-concurrency"></a>concurrence d’accès en lecture seule  
 Le curseur ne peut pas être mis à jour.  
  
## <a name="row-versioning"></a>contrôle de version de ligne  
 Essentiellement timestamp prise en charge, dans la ligne qui les versions sont comparées au moment de la mise à jour.
