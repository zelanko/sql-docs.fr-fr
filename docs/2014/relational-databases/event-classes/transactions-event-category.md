---
title: Transactions, catégorie d’événement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Transactions event category
- event classes [SQL Server], Transactions event category
- Transactions event category [SQL Server]
ms.assetid: bfc75c5b-7115-49d8-9148-a0c84ee66a9a
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8c58f6393cc722eed061e83299bff1e825d47a93
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052180"
---
# <a name="transactions-event-category"></a>Catégorie d'événements Transactions
  Les classes d’événements **Transactions** permettent de surveiller l’état des transactions. Les noms de classes d’événements portant le préfixe **TM:** sont utilisées pour assurer le suivi des opérations liées aux transactions qui sont envoyées à travers l’interface de gestion des transactions.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[DTCTransaction, classe d’événements](dtctransaction-event-class.md)|Assure le suivi des transactions coordonnées par [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC). Ce sont les transactions distribuées entre plusieurs bases de données ou instances du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Classe d'événements SQLTransaction](sqltransaction-event-class.md)|Surveille les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] BEGIN TRAN, COMMIT TRAN, SAVE TRAN et ROLLBACK TRAN.|  
|[Classe d'événements TM: Begin Tran Completed](tm-begin-tran-completed-event-class.md)|Indique qu'une demande BEGIN TRANSACTION est terminée.|  
|[Classe d'événements TM: Begin Tran Starting](tm-begin-tran-starting-event-class.md)|Indique qu'une demande BEGIN TRANSACTION démarre.|  
|[Classe d'événements TM: Commit Tran Completed](tm-commit-tran-completed-event-class.md)|Indique qu'une demande COMMIT TRANSACTION est terminée.|  
|[Classe d'événements TM: Commit Tran Starting](tm-commit-tran-starting-event-class.md)|Indique qu'une demande COMMIT TRANSACTION démarre.|  
|[Classe d'événements TM: Promote Tran Completed](tm-promote-tran-completed-event-class.md)|Indique qu'une demande PROMOTE TRANSACTION est terminée.|  
|[Classe d'événements TM: Promote Tran Starting](tm-promote-tran-starting-event-class.md)|Indique qu'une demande PROMOTE TRANSACTION démarre.|  
|[Classe d'événements TM: Rollback Tran Completed](tm-rollback-tran-completed-event-class.md)|Indique qu'une demande ROLLBACK TRANSACTION est terminée.|  
|[Classe d'événements TM: Rollback Tran Starting](tm-rollback-tran-starting-event-class.md)|Indique qu'une demande ROLLBACK TRANSACTION démarre.|  
|[Classe d'événements TM: Save Tran Completed](tm-save-tran-completed-event-class.md)|Indique qu'une demande SAVE TRANSACTION est terminée.|  
|[Classe d'événements TM: Save Tran Starting](tm-save-tran-starting-event-class.md)|Indique qu'une demande SAVE TRANSACTION démarre.|  
|[Classe d'événements TransactionLog](transactionlog-event-class.md)|Assure le suivi du moment où les transactions sont écrites dans un journal des transactions de la base de données.|  
  
  