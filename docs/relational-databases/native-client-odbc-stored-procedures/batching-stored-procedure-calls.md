---
title: Le traitement par lot des appels de procédure stockée | Microsoft Docs
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
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a22e9d3799fb0a4424e691093815f9647f094b76
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43086862"
---
# <a name="batching-stored-procedure-calls"></a>Traitement par lot des appels aux procédures stockées
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client traite automatiquement par lot des appels de procédure stockée sur le serveur lorsque cela est approprié. Il le fait uniquement en cas d'utilisation de la séquence d'échappement ODBC CALL ; il ne le fait pas pour l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE. Le traitement par lot des appels aux procédures stockées peut réduire le nombre de boucles sur le serveur et augmenter considérablement les performances.  
  
 Le pilote traite par lot les appels de procédure sur le serveur lorsque vous exécutez un lot qui contient plusieurs séquences d'échappement ODBC CALL. Il traite également par lot les appels de procédure lorsque vous utilisez des tableaux de paramètres liés dans une séquence d'échappement ODBC CALL. Par exemple, si vous utilisez l’option soit selon les lignes selon les lignes ou paramètre de liaison pour lier un tableau avec cinq éléments aux paramètres d’une instruction ODBC CALL SQL, lors de la **SQLExecute** ou **SQLExecDirect** est appelée, le pilote envoie un lot unique avec cinq appels de procédure sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de procédures stockées](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
