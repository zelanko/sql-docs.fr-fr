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
author: rothja
ms.author: jroth
ms.openlocfilehash: 8d7a1e93d222e2b87058bc878f7eca85313b4108
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85018339"
---
# <a name="freeing-a-statement-handle"></a>Libération d'un descripteur d'instruction
  Il est plus efficace de réutiliser des descripteurs d'instruction que de les supprimer et d'en allouer de nouveaux. Avant d'exécuter une nouvelle instruction SQL sur un descripteur d'instruction, les applications doivent s'assurer que les paramètres de l'instruction actuelle sont appropriés. Cela inclut les attributs d'instruction, les liaisons de paramètres et les liaisons de jeux de résultats. En règle générale, les paramètres et les jeux de résultats de l’ancienne instruction SQL doivent être détachés en appelant [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) avec les options SQL_RESET_PARAMS et SQL_UNBIND, puis reliés pour la nouvelle instruction SQL.  
  
 Lorsque l’application a terminé d’utiliser l’instruction, elle appelle [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) pour libérer l’instruction. Notez que **SQLDisconnect** libère automatiquement toutes les instructions sur une connexion.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de requêtes &#40;ODBC&#41;](executing-queries-odbc.md)  
  
  
