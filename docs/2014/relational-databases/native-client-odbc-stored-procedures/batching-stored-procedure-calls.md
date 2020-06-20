---
title: Traitement par lot des appels de procédure stockée | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
author: rothja
ms.author: jroth
ms.openlocfilehash: a0df58ce59853ee15b863cbc7bce34041c37fee4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85039508"
---
# <a name="batching-stored-procedure-calls"></a>Traitement par lot des appels aux procédures stockées
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client regroupe automatiquement les appels de procédure stockée au serveur, le cas échéant. Il le fait uniquement en cas d'utilisation de la séquence d'échappement ODBC CALL ; il ne le fait pas pour l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE. Le traitement par lot des appels aux procédures stockées peut réduire le nombre de boucles sur le serveur et augmenter considérablement les performances.  
  
 Le pilote traite par lot les appels de procédure sur le serveur lorsque vous exécutez un lot qui contient plusieurs séquences d'échappement ODBC CALL. Il traite également par lot les appels de procédure lorsque vous utilisez des tableaux de paramètres liés dans une séquence d'échappement ODBC CALL. Par exemple, si vous utilisez une liaison de paramètre selon les lignes ou les colonnes pour lier un tableau avec cinq éléments aux paramètres d’une instruction ODBC CALL SQL, lorsque **SQLExecute** ou **SQLExecDirect** est appelé, le pilote envoie un seul lot avec cinq appels de procédure au serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de procédures stockées](running-stored-procedures.md)  
  
  
