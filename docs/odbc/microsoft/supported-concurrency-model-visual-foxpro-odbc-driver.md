---
title: Modèle de concurrence pris en charge (Visual FoxPro ODBC Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], concurrency
- concurrency models [ODBC]
- FoxPro ODBC driver [ODBC], concurrency
ms.assetid: c39ed963-3af1-4888-8631-6083692ddcd7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 253a6dd86f6dc974d53dd151636bb8b8132e4d02
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307715"
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>Modèle d’accès concurrentiel pris en charge (pilote ODBC Visual FoxPro)
Le Visual FoxPro ODBC Driver prend en charge *la concurrence de lecture seulement*. Votre application peut appeler [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) avec une option SQL_CONCURRENCY de SQL_CONCUR_READ_ONLY.  
  
 Pour plus d’informations, consultez la [référence du programmeur de l’ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="read-only-concurrency"></a>la concurrence de lecture-seulement  
 Le curseur ne peut pas être mis à jour.  
  
## <a name="row-versioning"></a>contrôle de version de ligne  
 Essentiellement support timetamp, dans lequel les versions de ligne sont comparées au temps de mise à jour.
