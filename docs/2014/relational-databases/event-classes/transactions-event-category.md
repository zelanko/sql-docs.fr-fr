---
title: Transactions, catégorie d’événement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Transactions event category
- event classes [SQL Server], Transactions event category
- Transactions event category [SQL Server]
ms.assetid: bfc75c5b-7115-49d8-9148-a0c84ee66a9a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 076e68de4dc5d4e25f6cabe6b39ac4a61a05033a
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52801101"
---
# <a name="transactions-event-category"></a>Catégorie d'événements Transactions
  Les classes d’événements **Transactions** permettent de surveiller l’état des transactions. Les noms de classes d’événements portant le préfixe **TM:** sont utilisées pour assurer le suivi des opérations liées aux transactions qui sont envoyées à travers l’interface de gestion des transactions.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[DTCTransaction, classe d’événements](dtctransaction-event-class.md)|Assure le suivi des transactions coordonnées par [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC). Ce sont les transactions distribuées entre plusieurs bases de données ou instances du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Classe d'événements SQLTransaction](sqltransaction-event-class.md)|Surveille les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] BEGIN TRAN, COMMIT TRAN, SAVE TRAN et ROLLBACK TRAN.|  
|[TM : BEGIN Tran Completed, classe d’événements](tm-begin-tran-completed-event-class.md)|Indique qu'une demande BEGIN TRANSACTION est terminée.|  
|[TM : BEGIN Tran Starting, classe d’événements](tm-begin-tran-starting-event-class.md)|Indique qu'une demande BEGIN TRANSACTION démarre.|  
|[TM : COMMIT Tran Completed, classe d’événements](tm-commit-tran-completed-event-class.md)|Indique qu'une demande COMMIT TRANSACTION est terminée.|  
|[TM : COMMIT Tran Starting, classe d’événements](tm-commit-tran-starting-event-class.md)|Indique qu'une demande COMMIT TRANSACTION démarre.|  
|[TM : Promote Tran Completed, classe d’événements](tm-promote-tran-completed-event-class.md)|Indique qu'une demande PROMOTE TRANSACTION est terminée.|  
|[TM : Promote Tran Starting, classe d’événements](tm-promote-tran-starting-event-class.md)|Indique qu'une demande PROMOTE TRANSACTION démarre.|  
|[TM : ROLLBACK Tran Completed, classe d’événements](tm-rollback-tran-completed-event-class.md)|Indique qu'une demande ROLLBACK TRANSACTION est terminée.|  
|[TM : ROLLBACK Tran Starting (événement classe)](tm-rollback-tran-starting-event-class.md)|Indique qu'une demande ROLLBACK TRANSACTION démarre.|  
|[TM : Save Tran Completed, classe d’événements](tm-save-tran-completed-event-class.md)|Indique qu'une demande SAVE TRANSACTION est terminée.|  
|[TM : Save Tran Starting, classe d’événements](tm-save-tran-starting-event-class.md)|Indique qu'une demande SAVE TRANSACTION démarre.|  
|[Classe d'événements TransactionLog](transactionlog-event-class.md)|Assure le suivi du moment où les transactions sont écrites dans un journal des transactions de la base de données.|  
  
  
