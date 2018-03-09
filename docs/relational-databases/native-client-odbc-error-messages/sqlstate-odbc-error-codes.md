---
title: "SQLSTATE (Codes d’erreur ODBC) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-error-messages
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- ODBC error handling, cause information
- messages [ODBC], cause information
- SQLSTATEs
- errors [ODBC], cause information
ms.assetid: 84cce528-edb0-473f-a85f-3eb87fbe2cf3
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e078b1e51d1259ff03af84a0b556318b8b36318a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (codes d'erreur ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  SQLSTATE fournit des informations détaillées à propos de la cause d'un avertissement ou d'une erreur. Pour les erreurs qui se produisent dans les données source est détecté et retourné par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client mappe le numéro d’erreur natif retourné avec le SQLSTATE approprié. Si un numéro d’erreur natif n’a pas un code d’erreur ODBC mappé, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client retourne SQLSTATE 42000 (« syntaxe ou violation d’accès »). Les erreurs sont détectées par le pilote, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client génère le SQLSTATE approprié.  
  
 Pour plus d'informations sur les codes d'erreur d'état, consultez les rubriques suivantes :  
  
-   [Annexe A : Codes d’erreur ODBC](http://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [Mappages de SQLSTATE](http://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs et des messages](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
