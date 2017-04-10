---
title: "T&#226;che Sauvegarder la base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.backupdatabasetask.f1"
helpviewer_keywords: 
  - "bases de données, sauvegardes [Integration Services]"
  - "tâche Sauvegarder la base de données [Integration Services]"
  - "sauvegarde des bases de données [Integration Services]"
  - "journaux de transactions, sauvegarde [Integration Services]"
  - "sauvegarde des journaux de transactions [Integration Services]"
ms.assetid: b8839d71-13b7-41f2-a434-cb95020e79d7
caps.latest.revision: 46
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 46
---
# T&#226;che Sauvegarder la base de donn&#233;es
  La tâche Sauvegarder la base de données effectue différents types de sauvegardes de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
 La tâche Sauvegarder la base de données permet à un package de sauvegarder une ou plusieurs bases de données. Si la tâche ne sauvegarde qu'une seule base de données, vous pouvez choisir le composant de sauvegarde : la base de données ou ses fichiers et groupes de fichiers.  
  
## Modes de récupération et types de sauvegarde pris en charge  
 Le tableau suivant décrit les modes de récupération et les types de sauvegarde pris en charge par la tâche Sauvegarder la base de données.  
  
|Mode de récupération|Base de données|Base de données différentielle|Journal des transactions|Fichier ou différentielle de fichiers|  
|--------------------|--------------|---------------------------|---------------------|-------------------------------|  
|Simple|Requis|Ce paramètre est facultatif|Non pris en charge|Non pris en charge|  
|Complet|Requis|Ce paramètre est facultatif|Requis|Ce paramètre est facultatif|  
|Bulk-logged|Requis|Ce paramètre est facultatif|Requis|Ce paramètre est facultatif|  
  
 La tâche Sauvegarder la base de données encapsule une instruction Transact-SQL BACKUP. Pour plus d’informations, consultez [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md).  
  
## Configuration de la tâche Sauvegarder la base de données  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Cette tâche se trouve dans la section **Tâches du plan de maintenance** de la **boîte à outils** du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Tâche Sauvegarder la base de données &#40;Plan de maintenance&#41;](../../relational-databases/maintenance-plans/back-up-database-task-maintenance-plan.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
  