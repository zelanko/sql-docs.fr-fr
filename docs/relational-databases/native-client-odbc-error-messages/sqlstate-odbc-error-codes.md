---
title: SQLSTATE (codes d’erreur ODBC) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 162f6ff15a95c1839ef59b10c659935b687aeb59
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73783213"
---
# <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (codes d'erreur ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQLSTATE fournit des informations détaillées à propos de la cause d'un avertissement ou d'une erreur. Pour les erreurs qui se produisent dans la source de données détectées et retournées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client mappe le numéro d’erreur native renvoyé à la valeur SQLSTATE appropriée. Si un numéro d’erreur natif n’a pas de code d’erreur ODBC à mapper, le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client retourne SQLSTATE 42000 (« erreur de syntaxe ou violation d’accès »). Pour les erreurs détectées par le pilote, le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client génère le SQLSTATE approprié.  
  
 Pour plus d'informations sur les codes d'erreur d'état, consultez les rubriques suivantes :  
  
-   [Annexe A : Codes d’erreur ODBC](https://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [Mappages de SQLSTATE](https://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs et des messages](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
