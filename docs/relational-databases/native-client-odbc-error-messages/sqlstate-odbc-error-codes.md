---
title: SQLSTATE (Codes d’erreur ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- ODBC error handling, cause information
- messages [ODBC], cause information
- SQLSTATEs
- errors [ODBC], cause information
ms.assetid: 84cce528-edb0-473f-a85f-3eb87fbe2cf3
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 40ff6e7e20eab35aabeddec634aa2939484cfdd2
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414928"
---
# <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (codes d'erreur ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  SQLSTATE fournit des informations détaillées à propos de la cause d'un avertissement ou d'une erreur. Pour les erreurs qui se produisent dans les données source détecté et retourné par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client mappe le numéro d’erreur natif retourné avec le SQLSTATE approprié. Si un numéro d’erreur natif n’a pas un code d’erreur ODBC mappé, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client retourne SQLSTATE 42000 (« syntaxe ou violation d’accès »). Les erreurs sont détectées par le pilote, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client génère le SQLSTATE approprié.  
  
 Pour plus d'informations sur les codes d'erreur d'état, consultez les rubriques suivantes :  
  
-   [Annexe A : Codes d’erreur ODBC](http://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [Mappages de SQLSTATE](http://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs et des messages](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
