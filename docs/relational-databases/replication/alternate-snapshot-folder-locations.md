---
title: "Autres emplacements du dossier d&#39;instantan&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instantanés [réplication SQL Server], emplacements des autres dossiers"
  - "réplication d’instantané [SQL Server], emplacements des autres dossiers"
  - "autres dossiers d'instantané [réplication SQL Server]"
ms.assetid: 437553b0-19df-4522-8f27-06b5bc747c69
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Autres emplacements du dossier d&#39;instantan&#233;
  Les autres emplacements d'instantané vous permettent de stocker les fichiers d'instantanés dans un lieu autre que l'emplacement par défaut (généralement, sur le serveur de distribution), ou s'ajoutent à cet emplacement par défaut. Il peut s'agir d'un autre serveur, d'un lecteur réseau ou d'un support amovible tel qu'un CD-ROM ou un disque.  
  
 L'autre emplacement d'instantané est mémorisé sous la forme d'une propriété de la publication. Dans la mesure où cet emplacement est une propriété de la publication, l'Agent de distribution et l'Agent de fusion sont capables de déterminer l'instantané approprié dans le cadre du processus de synchronisation.  
  
 Si vous souhaitez spécifier un autre emplacement pour le dossier d'instantanés ou compresser des fichiers d'instantanés, créez la publication sans créer immédiatement l'instantané initial, définissez les propriétés de publication de l'emplacement de l'instantané, puis exécutez l'Agent d'instantané pour cette publication. Si vous changez l'autre emplacement après avoir créé l'instantané initial, les instantanés déjà générés pour la publication ne seront pas transférés vers le nouvel emplacement. Dans ce cas, et en fonction des paramètres de publication, l'Agent de fusion ou de distribution ne trouvera peut-être pas les fichiers d'instantanés dans le nouvel emplacement.  
  
> [!NOTE]  
>  Ne spécifiez pas un autre emplacement (à l’aide de le **Propriétés de la Publication** boîte de dialogue ou [sp_changepublication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)) qui est identique à l’emplacement par défaut du dossier de capture instantanée.  
  
> [!CAUTION]  
>  N'utilisez pas WebSync et d'autres emplacements de dossier d'instantanés à la fois.  
  
 **Pour spécifier un autre emplacement d'instantané**  
  
-   [! INCLURE [ssManStudioFull] (.. / Token/ssManStudioFull_md.md)]: [Specify an Alternate Snapshot Folder Location &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/publish/specify-an-alternate-snapshot-folder-location-sql-server-management-studio.md)  
  
-   Réplication [!INCLUDE[tsql](../../includes/tsql-md.md)] programming : [configurer les propriétés d’instantané & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## Voir aussi  
 [Initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Options d'instantané](../../relational-databases/replication/snapshot-options.md)  
  
  