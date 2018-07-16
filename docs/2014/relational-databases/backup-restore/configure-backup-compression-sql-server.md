---
title: Configurer la compression de sauvegarde (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 430905eb-d218-458c-bd48-aeee6fbb7446
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7136e9f5bda8cd873ae9d30c14ef66b6acf324ab
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287505"
---
# <a name="configure-backup-compression-sql-server"></a>Configurer la compression de sauvegarde (SQL Server)
  À l'installation, la compression de la sauvegarde est désactivée par défaut. Le comportement par défaut de la compression de la sauvegarde est défini par l’option de configuration au niveau du serveur **backup compression default** (valeur par défaut de compression de la sauvegarde). Toutefois, vous pouvez remplacer la valeur par défaut au niveau du serveur lors de la création d'une sauvegarde unique ou de la planification d'une série de sauvegardes de routine. Pour modifier la valeur par défaut au niveau du serveur, consultez [Afficher ou configurer l’option de configuration du serveur valeur par défaut de compression de la sauvegarde](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).  
  
## <a name="override-the-backup-compression-default"></a>Remplacer la valeur par défaut de compression de la sauvegarde  
 Vous pouvez modifier le comportement de compression de la sauvegarde pour une sauvegarde individuelle, un travail de sauvegarde ou une configuration de la copie des journaux de transactions.  
  
-   **[!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
     Pour remplacer la valeur par défaut de compression de la sauvegarde de serveur lors de la création d’une sauvegarde, utilisez WITH NO_COMPRESSION ou WITH COMPRESSION dans votre instruction [BACKUP](/sql/t-sql/statements/backup-transact-sql).  
  
     Pour une configuration de la copie des journaux de transactions, vous pouvez contrôler le comportement de compression des sauvegardes de fichiers journaux en utilisant [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql)[sp_change_log_shipping_primary_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-primary-database-transact-sql).  
  
-   **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
     Pour plus d’informations sur la façon d’afficher ou de configurer l’option par défaut de compression de la sauvegarde pour une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Afficher ou configurer l’option de configuration du serveur valeur par défaut de compression de la sauvegarde](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).  
  
     Vous pouvez remplacer la valeur par défaut de compression de la sauvegarde au niveau du serveur lors de la création d’une sauvegarde en spécifiant **Compresser la sauvegarde** ou **Ne pas compresser la sauvegarde** dans l’une des boîtes de dialogue suivantes :  
  
    -   [Sauvegarder la base de données (page Options)](back-up-database-backup-options-page.md)  
  
         Lors de la sauvegarde d'une base de données, vous pouvez contrôler la compression de la sauvegarde pour une sauvegarde de base de données, de fichier ou de journal individuelle.  
  
    -   [Utiliser l'Assistant Plan de maintenance](../maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
         L'Assistant Plan de la maintenance vous permet de contrôler la compression de la sauvegarde pour chaque jeu de sauvegardes complètes ou différentielles de base de données ou de sauvegardes de fichier journal que vous planifiez.  
  
    -   Integration Services (SSIS) [Tâche Sauvegarder la base de données](../../integration-services/control-flow/back-up-database-task.md)  
  
         Vous pouvez contrôler le comportement de compression de la sauvegarde lors de la création d'un package pour sauvegarder une base de données unique ou plusieurs bases de données.  
  
    -   [Paramètres de sauvegarde des journaux de transactions](../databases/log-shipping-transaction-log-backup-settings.md)  
  
         Vous pouvez contrôler le comportement de compression de la sauvegarde pour les sauvegardes de journaux.  
  
  
## <a name="see-also"></a>Voir aussi  
 [Compression de sauvegarde &#40;SQL Server&#41;](backup-compression-sql-server.md)  
  
  
