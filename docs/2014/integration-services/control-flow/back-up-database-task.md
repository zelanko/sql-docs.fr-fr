---
title: Sauvegarder la base de données, tâche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.backupdatabasetask.f1
helpviewer_keywords:
- database backups [Integration Services]
- Back Up Database task [Integration Services]
- backing up databases [Integration Services]
- transaction log backups [Integration Services]
- backing up transaction logs [Integration Services]
ms.assetid: b8839d71-13b7-41f2-a434-cb95020e79d7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d4b6aabb1f44c2a25704b7079074a5600c4d52d4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62833127"
---
# <a name="back-up-database-task"></a>Tâche Sauvegarder la base de données
  La tâche Sauvegarder la base de données effectue différents types de sauvegardes de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
 La tâche Sauvegarder la base de données permet à un package de sauvegarder une ou plusieurs bases de données. Si la tâche ne sauvegarde qu'une seule base de données, vous pouvez choisir le composant de sauvegarde : la base de données ou ses fichiers et groupes de fichiers.  
  
## <a name="supported-recover-models-and-backup-types"></a>Modes de récupération et types de sauvegarde pris en charge  
 Le tableau suivant décrit les modes de récupération et les types de sauvegarde pris en charge par la tâche Sauvegarder la base de données.  
  
|mode de récupération|Base de données|Base de données différentielle|Journal des transactions|Fichier ou différentielle de fichiers|  
|--------------------|--------------|---------------------------|---------------------|-------------------------------|  
|Simple|Requis|Ce paramètre est facultatif|Non pris en charge|Non pris en charge|  
|Complète|Requis|Ce paramètre est facultatif|Requis|Ce paramètre est facultatif|  
|Bulk-logged|Requis|Ce paramètre est facultatif|Requis|Ce paramètre est facultatif|  
  
 La tâche Sauvegarder la base de données encapsule une instruction Transact-SQL BACKUP. Pour plus d’informations, consultez [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).  
  
## <a name="configuration-of-the-back-up-database-task"></a>Configuration de la tâche Sauvegarder la base de données  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Cette tâche se trouve dans la section **Tâches du plan de maintenance** de la **boîte à outils** du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Tâche Sauvegarder la base de données &#40;Plan de maintenance&#41;](../../relational-databases/maintenance-plans/options-in-the-back-up-database-task-for-maintenance-plan.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
  
