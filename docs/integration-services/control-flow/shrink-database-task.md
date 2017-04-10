---
title: "T&#226;che R&#233;duire la base de donn&#233;es | Microsoft Docs"
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
  - "sql13.dts.designer.shrinkdatabasetask.f1"
helpviewer_keywords: 
  - "tâche Réduire la base de données"
  - "bases de données, réduction [Integration Services]"
  - "réduction des bases de données"
ms.assetid: e66286f8-97b1-4e5a-86b4-e56f1932b7d5
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 42
---
# T&#226;che R&#233;duire la base de donn&#233;es
  La tâche Réduire la base de données réduit la taille des fichiers journaux et de données de bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La tâche Réduire la base de données permet à un package de réduire les fichiers d'une ou plusieurs bases de données.  
  
 La réduction des fichiers de données permet de récupérer de l'espace en déplaçant des pages de données de la fin du fichier vers un espace inoccupé plus proche de l'avant du fichier. Lorsqu'une quantité d'espace libre suffisante est créée à la fin du fichier, des pages de données à la fin du fichier peuvent être désallouées et retournées au système de fichiers.  
  
> [!WARNING]  
>  Les données qui sont déplacées pour réduire un fichier peuvent être dispersées à n'importe quel emplacement disponible dans le fichier. Cela provoque la fragmentation de l'index et peut ralentir les performances des requêtes qui recherchent une plage de l'index. Pour éliminer la fragmentation, reconstruisez les index dans le fichier après réduction.  
  
## Commandes  
 La tâche Réduire la base de données encapsule une commande DBCC SHRINKDATABASE, avec les options et les arguments suivants :  
  
-   *database_name*  
  
-   *target_percent*  
  
-   NOTRUNCATE ou TRUNCATEONLY.  
  
 Si la tâche de réduction de base de données réduit plusieurs bases de données, la tâche exécute plusieurs commandes SHRINKDATABASE, une pour chaque base de données. Toutes les instances de la commande SHRINKDATABASE utilisent les mêmes valeurs d’argument, sauf pour l’argument *database_name*. Pour plus d’informations, consultez [DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
## Configuration de la tâche Réduire la base de données  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Cette tâche se trouve dans la section **Tâches du plan de maintenance** de la **boîte à outils** du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], cliquez sur la rubrique suivante :  
  
-   [Tâche Réduire la base de données &#40;Plan de maintenance&#41;](../../relational-databases/maintenance-plans/shrink-database-task-maintenance-plan.md)  
  
 Pour plus d’informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
  