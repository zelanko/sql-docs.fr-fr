---
title: "Ex&#233;cuter des scripts pendant la synchronisation (programmation Transact-SQL de la r&#233;plication) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "synchronisation [réplication SQL Server], scripts"
  - "scripts [réplication SQL Server], synchronisation et"
  - "sp_addscriptexec"
ms.assetid: b58a0877-4e43-4fab-a281-24e6022d3fb1
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# Ex&#233;cuter des scripts pendant la synchronisation (programmation Transact-SQL de la r&#233;plication)
  La réplication prend en charge l'exécution de script à la demande pour les Abonnés à des publications transactionnelles et de fusion. Cette fonctionnalité copie le script dans le répertoire de travail de réplication, puis utilise **sqlcmd** pour appliquer le script sur l’abonné. Par défaut, en cas d'échec lors de l'application du script pour un abonnement à une publication transactionnelle, l'Agent de distribution s'arrêtera. Vous pouvez spécifier un script [!INCLUDE[tsql](../../includes/tsql-md.md)] à exécuter par programme à l'aide des procédures stockées de réplication.  
  
### Pour spécifier un script à exécuter pour tous les Abonnés à une publication d'instantané, transactionnelle ou de fusion  
  
1.  Composez et testez le script [!INCLUDE[tsql](../../includes/tsql-md.md)] qui sera exécuté à la demande.  
  
2.  Enregistrez le fichier de script dans un emplacement accessible à l'Agent d'instantané pour la publication.  
  
3.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addscriptexec & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql.md). Spécifiez **@publication**, le nom du fichier de script avec le chemin d’accès UNC complet créé à l’étape 2 pour **@scriptfile**, et une de ces valeurs pour **@skiperror**:  
  
    -   **0** -l’agent s’arrête l’exécution du script si une erreur s’est produite.  
  
    -   **1** -l’agent de consigner les erreurs et continuer l’exécution du script lorsque des erreurs sont rencontrées.  
  
4.  Le script spécifié sera exécuté sur chaque Abonné lorsque l'agent s'exécutera de nouveau pour synchroniser l'abonnement.  
  
## Voir aussi  
 [Synchronisez les données](../../relational-databases/replication/synchronize-data.md)  
  
  