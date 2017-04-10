---
title: "Didacticiel&#160;: Sauvegarde et restauration SQL Server dans le service de Stockage Blob Windows Azure | Microsoft Docs"
ms.custom: ""
ms.date: "02/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-query-tuning"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016 Preview"
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 9
---
# Didacticiel&#160;: Sauvegarde et restauration SQL Server dans le service de Stockage Blob Windows Azure
Bienvenue dans le didacticiel Mise en route avec la sauvegarde et la restauration SQL Server dans le service de stockage d'objets blob Windows Azure. Ce didacticiel vous aide à comprendre comment écrire des sauvegardes et les restaurer à partir du service de stockage d'objets blob Windows Azure.  
  
## Contenu du didacticiel  
Ce didacticiel montre comment créer un compte de stockage Windows et un conteneur d'objets blob, créer des informations d'identification pour accéder au compte de stockage, écrire une sauvegarde dans le service d'objet blob et effectuer une restauration simple. Ce didacticiel est divisé en quatre leçons :  
  
[Leçon 1 : Créer des objets de Stockage Microsoft Azure](../Topic/Lesson%201:%20Create%20Windows%20Azure%20Storage%20Objects.md)  
Dans cette leçon, vous allez créer un compte de stockage Windows Azure et un conteneur d'objets blob.  
  
[Leçon 2 : Créer des informations d’identification SQL Server](../Topic/Lesson%202:%20Create%20a%20SQL%20Server%20Credential.md)  
Dans cette leçon, vous allez créer des informations d'identification afin de stocker les informations de sécurité utilisées pour accéder au compte de stockage Windows Azure.  
  
[Leçon 3 : Écrire une sauvegarde de base de données complète dans le service de Stockage Blob Windows Azure](../Topic/Lesson%203:%20Write%20a%20Full%20Database%20Backup%20to%20the%20Windows%20Azure%20Blob%20Storage%20Service.md)  
Dans cette leçon, vous allez publier une instruction T-SQL pour écrire une sauvegarde de la base de données AdventureWorks2012 dans le service de stockage d'objets blob Windows Azure.  
  
[Leçon 4 : Effectuer une restauration d'une sauvegarde de base de données complète](../Topic/Lesson%204:%20Perform%20a%20Restore%20From%20a%20Full%20Database%20Backup.md)  
Dans cette leçon, vous allez publier une instruction T-SQL pour effectuer une restauration d'une sauvegarde de la base de données que vous avez créée au cours de la leçon précédente.  
  
### Spécifications  
Pour suivre ce didacticiel, vous devez être familiarisé avec [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sauvegarder et restaurer les concepts et la syntaxe T-SQL. Pour utiliser ce didacticiel, votre système doit répondre aux spécifications suivantes :  
  
-   Une instance de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]et la base de données AdventureWorks2012 doivent être installées.  
  
    L'instance de SQL Server peut être installée sur site ou sur un ordinateur virtuel Windows Azure.  
  
    Vous pouvez utiliser une base de données utilisateur en remplacement d'AdventureWorks2012, puis modifier la syntaxe TSQL en conséquence.  
  
-   Le compte d’utilisateur utilisé pour émettre les commandes BACKUP (sauvegarder) ou RESTORE (restaurer) doit figurer dans le rôle de base de données **db_backup operator** avec les autorisations **Modifier des informations d’identification**.  
  
### Lecture supplémentaire  
Les ressources suivantes sont des lectures recommandées afin de comprendre les concepts et les pratiques recommandées pour l'utilisation du service de stockage d'objets blob Windows Azure pour les sauvegardes [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
1.  [Sauvegarde et restauration SQL Server avec le service de Stockage Blob Microsoft Azure](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [Meilleures pratiques et dépannage de sauvegarde SQL Server vers une URL](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
## Voir aussi  
[Sauvegarde de la base de données et du journal](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md#databaselog)  
[Création d'une sauvegarde complète du groupe de fichiers principal](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md#filegroups)  
[Restauration d'une base de données et déplacement des fichiers](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md#restoredbwithmove)  
  
