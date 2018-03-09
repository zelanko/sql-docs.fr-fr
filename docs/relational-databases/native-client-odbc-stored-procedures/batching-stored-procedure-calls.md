---
title: "Le traitement par lot des appels de procédure stockée | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0f2015efa4e176865d3fa99c24b9bc7f9a616643
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="batching-stored-procedure-calls"></a>Traitement par lot des appels aux procédures stockées
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client traite automatiquement les appels de procédure stockée sur le serveur lorsque cela est approprié. Il le fait uniquement en cas d'utilisation de la séquence d'échappement ODBC CALL ; il ne le fait pas pour l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE. Le traitement par lot des appels aux procédures stockées peut réduire le nombre de boucles sur le serveur et augmenter considérablement les performances.  
  
 Le pilote traite par lot les appels de procédure sur le serveur lorsque vous exécutez un lot qui contient plusieurs séquences d'échappement ODBC CALL. Il traite également par lot les appels de procédure lorsque vous utilisez des tableaux de paramètres liés dans une séquence d'échappement ODBC CALL. Par exemple, si vous utilisez une liaison de paramètre selon les lignes ou colonnes pour lier un tableau avec cinq éléments aux paramètres d’une instruction ODBC CALL SQL, lorsque **SQLExecute** ou **SQLExecDirect** est appelée, le pilote transmet un lot unique avec cinq appels de procédure sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de procédures stockées](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
