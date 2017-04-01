---
title: "Configurer des param&#232;tres de collecte de donn&#233;es (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "collecte de données [SQL Server]"
ms.assetid: 850905b6-35d2-4ed1-ab51-de64daa832b2
caps.latest.revision: 16
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 16
---
# Configurer des param&#232;tres de collecte de donn&#233;es (Transact-SQL)
  Avant de créer un jeu d'éléments de collecte personnalisé, vous devez d'abord configurer des paramètres de collecte de données. Pour cela, vous devez vous servir des procédures stockées fournies avec le collecteur de données. L’utilisation de l'éditeur de requêtes dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] est nécessaire pour effectuer la procédure suivante.  
  
> [!NOTE]  
>  Vous ne configurez des paramètres de collecte de données qu'une seule fois. Lorsque la configuration est terminée, ces paramètres servent pour tous les jeux d'éléments de collecte supplémentaires que vous créez.  
  
### Configurer des paramètres de collecte de données  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à la base de données dans laquelle vous souhaitez créer un jeu d'éléments de collecte personnalisé.  
  
2.  Dans l'éditeur de requêtes, émettez les instructions suivantes.  
  
    ```tsql  
    USE msdb;  
    EXEC sp_syscollector_set_warehouse_instance_name N'INSTANCE_NAME';-- where instance name is the name of the SQL Server instance  
    EXEC sp_syscollector_set_warehouse_database_name N'MDW';  
    EXEC sp_syscollector_set_cache_directory N'D:\tempdata';  
    ```  
  
## Voir aussi  
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)   
 [Procédures stockées du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  