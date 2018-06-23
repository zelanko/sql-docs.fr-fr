---
title: La libération d’un descripteur d’instruction | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7da2fec15303e9c2d50fb7aa2e6dc40266a380d9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140732"
---
# <a name="freeing-a-statement-handle"></a>Libération d'un descripteur d'instruction
  Il est plus efficace de réutiliser des descripteurs d'instruction que de les supprimer et d'en allouer de nouveaux. Avant d'exécuter une nouvelle instruction SQL sur un descripteur d'instruction, les applications doivent s'assurer que les paramètres de l'instruction actuelle sont appropriés. Cela inclut les attributs d'instruction, les liaisons de paramètres et les liaisons de jeux de résultats. En règle générale, les paramètres et le résultat définit pour l’ancienne instruction SQL doit être déliée en appelant [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) avec le SQL_RESET_PARAMS et SQL_UNBIND options et puis liés à nouveau pour la nouvelle instruction SQL.  
  
 Lorsque l’application a terminé à l’aide de l’instruction, il appelle [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) pour libérer de l’instruction. Notez que **SQLDisconnect** libère automatiquement toutes les instructions sur une connexion.  
  
## <a name="see-also"></a>Voir aussi  
 [L’exécution de requêtes &#40;ODBC&#41;](executing-queries-odbc.md)  
  
  