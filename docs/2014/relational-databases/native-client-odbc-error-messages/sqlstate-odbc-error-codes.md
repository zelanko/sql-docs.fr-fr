---
title: SQLSTATE (codes d’erreur ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: rothja
ms.author: jroth
ms.openlocfilehash: ff3ec0a5cdc8f24f34e42849f7c8f6d1d9d41478
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85019908"
---
# <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (codes d'erreur ODBC)
  SQLSTATE fournit des informations détaillées à propos de la cause d'un avertissement ou d'une erreur. Pour les erreurs qui se produisent dans la source de données détectées et retournées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client mappe le numéro d’erreur native retourné au SQLSTATE approprié. Si aucun code d’erreur ODBC n’est mappé à un numéro d’erreur natif, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client retourne SQLSTATE 42000 (« erreur de syntaxe ou violation d’accès »). Pour les erreurs détectées par le pilote, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client génère le SQLSTATE approprié.  
  
 Pour plus d'informations sur les codes d'erreur d'état, consultez les rubriques suivantes :  
  
-   [Annexe A : Codes d’erreur ODBC](https://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [Mappages SQLSTATE](https://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs et des messages](handling-errors-and-messages.md)  
  
  
