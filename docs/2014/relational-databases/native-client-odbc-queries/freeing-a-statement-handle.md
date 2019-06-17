---
title: Libération d’un descripteur d’instruction | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b1a155f7d2ee6cc5f92d46c2bb744168dc5ebc0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63200046"
---
# <a name="freeing-a-statement-handle"></a>Libération d'un descripteur d'instruction
  Il est plus efficace de réutiliser des descripteurs d'instruction que de les supprimer et d'en allouer de nouveaux. Avant d'exécuter une nouvelle instruction SQL sur un descripteur d'instruction, les applications doivent s'assurer que les paramètres de l'instruction actuelle sont appropriés. Cela inclut les attributs d'instruction, les liaisons de paramètres et les liaisons de jeux de résultats. En règle générale, les paramètres et le résultat définit pour l’ancienne instruction SQL doit être déliée en appelant [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) avec le SQL_RESET_PARAMS et SQL_UNBIND options et puis liés à nouveau pour la nouvelle instruction SQL.  
  
 Lorsque l’application a terminé d’utiliser l’instruction, elle appelle [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) pour libérer de l’instruction. Notez que **SQLDisconnect** libère automatiquement toutes les instructions sur une connexion.  
  
## <a name="see-also"></a>Voir aussi  
 [L’exécution de requêtes &#40;ODBC&#41;](executing-queries-odbc.md)  
  
  
