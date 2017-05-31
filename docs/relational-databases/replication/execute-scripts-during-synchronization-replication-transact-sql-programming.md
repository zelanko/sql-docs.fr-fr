---
title: "Exécuter des scripts pendant la synchronisation (programmation Transact-SQL de la réplication) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- synchronization [SQL Server replication], scripts
- scripts [SQL Server replication], synchronization and
- sp_addscriptexec
ms.assetid: b58a0877-4e43-4fab-a281-24e6022d3fb1
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: deef18b1b37375e659dd0412dd7b69f10b8a3bdf
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="execute-scripts-during-synchronization-replication-transact-sql-programming"></a>Exécuter des scripts pendant la synchronisation (programmation Transact-SQL de la réplication)
  La réplication prend en charge l'exécution de script à la demande pour les Abonnés à des publications transactionnelles et de fusion. Cette fonctionnalité copie le script vers le répertoire de travail de réplication puis utilise **sqlcmd** pour appliquer le script à l'Abonné. Par défaut, en cas d'échec lors de l'application du script pour un abonnement à une publication transactionnelle, l'Agent de distribution s'arrêtera. Vous pouvez spécifier un script [!INCLUDE[tsql](../../includes/tsql-md.md)] à exécuter par programme à l'aide des procédures stockées de réplication.  
  
### <a name="to-specify-a-script-to-run-for-all-subscribers-to-a-snapshot-transactional-or-merge-publication"></a>Pour spécifier un script à exécuter pour tous les Abonnés à une publication d'instantané, transactionnelle ou de fusion  
  
1.  Composez et testez le script [!INCLUDE[tsql](../../includes/tsql-md.md)] qui sera exécuté à la demande.  
  
2.  Enregistrez le fichier de script dans un emplacement accessible à l'Agent d'instantané pour la publication.  
  
3.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addscriptexec &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql.md). Spécifiez **@publication**, le nom du fichier de script avec le chemin d'accès complet UNC créé à l'étape 2 pour **@scriptfile**et l'une des valeurs suivantes pour **@skiperror**:  
  
    -   **0** – l'agent arrêtera d'exécuter le script en cas d'erreur.  
  
    -   **1** – l'agent enregistrera les erreurs rencontrées et continuera à exécuter le script.  
  
4.  Le script spécifié sera exécuté sur chaque Abonné lorsque l'agent s'exécutera de nouveau pour synchroniser l'abonnement.  
  
## <a name="see-also"></a>Voir aussi  
 [Synchronisez les données](../../relational-databases/replication/synchronize-data.md)  
  
  
