---
title: SQLSTATE (ODBC Error Codes) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- ODBC error handling, cause information
- messages [ODBC], cause information
- SQLSTATEs
- errors [ODBC], cause information
ms.assetid: 84cce528-edb0-473f-a85f-3eb87fbe2cf3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8c7f3fbdf690989830cff2a41028ee0c1e2c9f37
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291519"
---
# <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (codes d'erreur ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQLSTATE fournit des informations détaillées à propos de la cause d'un avertissement ou d'une erreur. Pour les erreurs qui se produisent dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source de données détectée et retournée par , le conducteur de l’ODBC du client autochtone cartographie le numéro d’erreur natif retourné au SQLSTATE approprié. Si un numéro d’erreur natif n’a pas de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] code d’erreur ODBC à cartographier, le conducteur de Native Client ODBC renvoie SQLSTATE 42000 (« erreur de syntaxe ou violation d’accès »). Pour les erreurs détectées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le conducteur, le conducteur de Native Client ODBC génère le SQLSTATE approprié.  
  
 Pour plus d'informations sur les codes d'erreur d'état, consultez les rubriques suivantes :  
  
-   [Annexe A : Codes d’erreur ODBC](https://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [Mappages SQLSTATE](https://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs et des messages](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
