---
title: SQLCloseCursor | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLCloseCursor function
ms.assetid: e7134d65-5c1c-4ae2-b119-d9b4b9a42483
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26b00c4781624bf653ad9a8200a219951dc793c7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48097159"
---
# <a name="sqlclosecursor"></a>SQLCloseCursor
  **SQLCloseCursor** remplace [SQLFreeStmt](sqlfreestmt.md) avec un *Option* valeur de SQL_CLOSE. À la réception du **SQLCloseCursor**, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client ignore les lignes du jeu de résultats en attente. Notez que les liaisons de colonnes et de paramètres de l'instruction (s'il en existe) ne sont pas modifiés par **SQLCloseCursor**.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLCloseCursor](http://go.microsoft.com/fwlink/?LinkId=59331)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
