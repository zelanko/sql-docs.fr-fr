---
title: "supprimer un instantan&#233; de base de donn&#233;es (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "retrait d'instantanés de base de données"
  - "suppression d'instantanés de base de données"
  - "Instantanés de base de données [SQL Server], suppression"
ms.assetid: ad70ec97-d5fb-41aa-b72a-915e74b61b76
caps.latest.revision: 36
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 35
---
# supprimer un instantan&#233; de base de donn&#233;es (Transact-SQL)
  La suppression d'un instantané de base de données entraîne la suppression de l'instantané de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ainsi que celle des fichiers partiellement alloués utilisés par l'instantané. Lorsque vous supprimez un instantané de base de données, toutes ses connexions utilisateur sont terminées.  
  
## Sécurité  
  
###  <a name="Permissions"></a> Autorisations  
 Tout utilisateur doté des autorisations DROP DATABASE peut supprimer un instantané de base de données.  
  
##  <a name="TsqlProcedure"></a> Procédure de suppresssion d'un instantané de base de données (à l'aide de Transact-SQL)  
 **Pour supprimer un instantané de base de données**  
  
1.  Identifiez l'instantané à supprimer. Vous pouvez afficher les instantanés d'une base de données dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour plus d’informations, consultez [Afficher un instantané de base de données &#40;SQL Server&#41;](../../relational-databases/databases/view-a-database-snapshot-sql-server.md).  
  
2.  Exécutez l’instruction [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md) en définissant le nom de l’instantané de base de données à supprimer. La syntaxe de base est la suivante :  
  
     DROP DATABASE *nom_instantané_base_de_données* [ **,**...*n* ]  
  
     où *nom_instantané_base_de_données* est le nom de l’instantané de base de données à supprimer.  
  
####  <a name="TsqlExample"></a> Exemple (Transact-SQL)  
 L'exemple suivant supprime un instantané de base de données nommé SalesSnapshot0600 sans affecter la base de données source.  
  
```  
DROP DATABASE SalesSnapshot0600 ;  
```  
  
 Les connexions utilisateur à SalesSnapshot0600 sont terminées, et tous les fichiers physiques partiellement alloués du système de fichiers NTFS utilisés par l'instantané sont supprimés.  
  
> [!NOTE]  
>  Pour plus d’informations sur l’utilisation des fichiers partiellement alloués par les instantanés de base de données, consultez [Instantanés de base de données &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Créer un instantané de base de données &#40;Transact-SQL&#41;](../../relational-databases/databases/create-a-database-snapshot-transact-sql.md)  
  
-   [Afficher un instantané de base de données &#40;SQL Server&#41;](../../relational-databases/databases/view-a-database-snapshot-sql-server.md)  
  
-   [Rétablir une base de données dans l'état d'un instantané de base de données](../../relational-databases/databases/revert-a-database-to-a-database-snapshot.md)  
  
 ![Icône de flèche utilisée avec le lien Retour en haut](../../analysis-services/instances/media/uparrow16x16.png "Icône de flèche utilisée avec le lien Retour en haut") [&#91;Haut&#93;](#Top)  
  
## Voir aussi  
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
 [Instantanés de base de données &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  