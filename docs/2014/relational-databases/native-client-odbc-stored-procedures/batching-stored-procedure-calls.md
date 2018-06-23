---
title: Le traitement par lot des appels de procédure stockée | Documents Microsoft
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
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fd3d7fca3dc22d20c9aeadfc3b60fa41fa64f895
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051040"
---
# <a name="batching-stored-procedure-calls"></a>Traitement par lot des appels aux procédures stockées
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client traite automatiquement les appels de procédure stockée sur le serveur lorsque cela est approprié. Il le fait uniquement en cas d'utilisation de la séquence d'échappement ODBC CALL ; il ne le fait pas pour l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE. Le traitement par lot des appels aux procédures stockées peut réduire le nombre de boucles sur le serveur et augmenter considérablement les performances.  
  
 Le pilote traite par lot les appels de procédure sur le serveur lorsque vous exécutez un lot qui contient plusieurs séquences d'échappement ODBC CALL. Il traite également par lot les appels de procédure lorsque vous utilisez des tableaux de paramètres liés dans une séquence d'échappement ODBC CALL. Par exemple, si vous utilisez une liaison de paramètre selon les lignes ou colonnes pour lier un tableau avec cinq éléments aux paramètres d’une instruction ODBC CALL SQL, lorsque **SQLExecute** ou **SQLExecDirect** est appelée, le pilote envoie un lot unique avec cinq appels de procédure sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de procédures stockées](running-stored-procedures.md)  
  
  