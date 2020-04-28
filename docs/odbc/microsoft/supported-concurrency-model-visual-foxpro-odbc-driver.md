---
title: Modèle d’accès concurrentiel pris en charge (pilote ODBC Visual FoxPro) | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307715"
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>Modèle d’accès concurrentiel pris en charge (pilote ODBC Visual FoxPro)
Le pilote ODBC Visual FoxPro prend en charge l' *accès concurrentiel en lecture seule*. Votre application peut appeler [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) avec l’option SQL_CONCURRENCY SQL_CONCUR_READ_ONLY.  
  
 Pour plus d’informations, consultez [Guide de référence du programmeur ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="read-only-concurrency"></a>accès concurrentiel en lecture seule  
 Impossible de mettre à jour le curseur.  
  
## <a name="row-versioning"></a>contrôle de version de ligne  
 Prise en charge des horodateurs, dans laquelle les versions de ligne sont comparées au moment de la mise à jour.
