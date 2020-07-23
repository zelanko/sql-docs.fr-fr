---
title: Sauvegarder la base de données, tâche | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.backupdatabasetask.f1
helpviewer_keywords:
- database backups [Integration Services]
- Back Up Database task [Integration Services]
- backing up databases [Integration Services]
- transaction log backups [Integration Services]
- backing up transaction logs [Integration Services]
ms.assetid: b8839d71-13b7-41f2-a434-cb95020e79d7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d10f1ceab3ddb56ae8edbd06b2226fad2646c586
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86918873"
---
# <a name="back-up-database-task"></a>Tâche Sauvegarder la base de données

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  La tâche Sauvegarder la base de données effectue différents types de sauvegardes de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Sauvegarder et restaurer des bases de données SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
 La tâche Sauvegarder la base de données permet à un package de sauvegarder une ou plusieurs bases de données. Si la tâche ne sauvegarde qu'une seule base de données, vous pouvez choisir le composant de sauvegarde : la base de données ou ses fichiers et groupes de fichiers.  
  
## <a name="supported-recover-models-and-backup-types"></a>Modes de récupération et types de sauvegarde pris en charge  
 Le tableau suivant décrit les modes de récupération et les types de sauvegarde pris en charge par la tâche Sauvegarder la base de données.  
  
|mode de récupération|Base de données|Base de données différentielle|Journal des transactions|Fichier ou différentielle de fichiers|  
|--------------------|--------------|---------------------------|---------------------|-------------------------------|  
|Simple|Obligatoire|Facultatif|Non pris en charge|Non pris en charge|  
|Complète|Obligatoire|Facultatif|Obligatoire|Facultatif|  
|Bulk-logged|Obligatoire|Facultatif|Obligatoire|Facultatif|  
  
 La tâche Sauvegarder la base de données encapsule une instruction Transact-SQL BACKUP. Pour plus d’informations, consultez [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md).  
  
## <a name="configuration-of-the-back-up-database-task"></a>Configuration de la tâche Sauvegarder la base de données  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Cette tâche se trouve dans la section **Tâches du plan de maintenance** de la **boîte à outils** du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Tâche Sauvegarder la base de données &#40;Plan de maintenance&#41;](../../relational-databases/maintenance-plans/options-in-the-back-up-database-task-for-maintenance-plan.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
  
