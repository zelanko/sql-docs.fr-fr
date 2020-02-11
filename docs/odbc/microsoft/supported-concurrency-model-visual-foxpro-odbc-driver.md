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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 597d1022fa6946e0ae768cb9600a3f4534c67a25
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68080693"
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>Modèle d’accès concurrentiel pris en charge (pilote ODBC Visual FoxPro)
Le pilote ODBC Visual FoxPro prend en charge l' *accès concurrentiel en lecture seule*. Votre application peut appeler [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) avec l’option SQL_CONCURRENCY SQL_CONCUR_READ_ONLY.  
  
 Pour plus d’informations, consultez [Guide de référence du programmeur ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="read-only-concurrency"></a>accès concurrentiel en lecture seule  
 Impossible de mettre à jour le curseur.  
  
## <a name="row-versioning"></a>contrôle de version de ligne  
 Prise en charge des horodateurs, dans laquelle les versions de ligne sont comparées au moment de la mise à jour.
