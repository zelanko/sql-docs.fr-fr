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
author: rothja
ms.author: jroth
ms.openlocfilehash: 770a67432868516e5023d1cf0ff819501b4c130e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85022879"
---
# <a name="sqlclosecursor"></a>SQLCloseCursor
  **SQLCloseCursor** remplace [SQLFreeStmt](sqlfreestmt.md) par une valeur d' *option* de SQL_CLOSE. À réception de **SQLCloseCursor**, le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client les lignes de jeu de résultats en attente. Notez que les liaisons de colonnes et de paramètres de l'instruction (s'il en existe) ne sont pas modifiés par **SQLCloseCursor**.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLCloseCursor](https://go.microsoft.com/fwlink/?LinkId=59331)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
