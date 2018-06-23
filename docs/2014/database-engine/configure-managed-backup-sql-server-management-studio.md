---
title: Configurer la gestion de sauvegarde (SQL Server Management Studio) | Documents Microsoft
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.managedbackup.configure.f1
ms.assetid: 79397cf6-0611-450a-b0d8-e784a76e3091
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2d3dfda6b4fb970f9ee8424cd3eec2e72bf0a22b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141027"
---
# <a name="configure-managed-backup-sql-server-management-studio"></a>Configuration de la sauvegarde managée (SQL Server Management Studio)
  Le **sauvegarde managée** boîte de dialogue vous permet de configurer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] valeurs par défaut pour l’instance. Cette rubrique explique comment utiliser cette boîte de dialogue pour configurer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] paramètres par défaut pour l’instance et les options que vous devez prendre en compte lorsque vous procédez ainsi. Lorsque [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est configuré pour l’instance, les paramètres sont appliqués aux nouvelles bases de données créées par la suite.  
  
 Si vous souhaitez configurer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une base de données spécifique, consultez [activer et configurer sauvegarde managée SQL Server vers Windows Azure pour une base de données](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).  
 
> [!NOTE] 
> La Gestion de sauvegarde SQL Server n’est pas prise en charge avec les serveurs proxy. 
  
## <a name="task-list"></a>Liste des tâches  
  
## <a name="includesssmartbackupincludesss-smartbackup-mdmd-functions-using-managed-backup-interface-in-sql-server-management-studio"></a>[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Fonctions utilisant l’interface de sauvegarde managée dans SQL Server Management Studio  
 Dans cette version, vous pouvez uniquement configurer des paramètres par défaut au niveau de l’instance à l’aide de la **gestion de sauvegarde** interface. Vous ne pouvez pas configurer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une base de données, suspendre ou reprendre [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] opérations ou configuration de notifications par courrier électronique. Pour plus d’informations sur la façon d’effectuer des opérations non prises en charge par le biais du **sauvegarde managée** l’interface, consultez [SQL Server Managed Backup dans Windows Azure - paramètres de rétention et stockage](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).  
  
## <a name="permissions"></a>Autorisations  
 **Sauvegarde nœud géré est SQL Server Management Studio :** pour afficher les **sauvegarde managée** nœud **l’Explorateur d’objets**, vous devez être un administrateur système ou disposer des autorisations suivantes plus précisément, accordée à votre compte d’utilisateur :  
  
-   `db_backupoperator`  
  
-   `VIEW SERVER STATE`  
  
-   `ALTER ANY CREDENTIAL`  
  
-   `VIEW ANY DEFINITION`  
  
-   `EXECUTE` sur `smart_admin.fn_is_master_switch_on`.  
  
-   `SELECT` sur `smart_admin.fn_backup_instance_config`.  
  
 **Pour configurer des sauvegardes managées :** pour configurer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] dans SQL Server Management Studio, vous devez être un administrateur système ou disposer des autorisations suivantes :  
  
 L’appartenance au `db_backupoperator` de la base de données de rôle, avec `ALTER ANY CREDENTIAL` autorisations, et `EXECUTE` autorisations sur `sp_delete_backuphistory` procédure stockée.  
  
 `SELECT` autorisations sur le `smart_admin.fn_get_current_xevent_settings` (fonction).  
  
 `EXECUTE` autorisations sur le `smart_admin.sp_get_backup_diagnostics` procédure stockée. En outre, nécessite les autorisations `VIEW SERVER STATE`, car elle appelle en interne d'autres objets système qui nécessitent cette autorisation.  
  
 `EXECUTE` autorisations sur `smart_admin.sp_set_instance_backup`, et `smart_admin.sp_backup_master_switch`.  
  
## <a name="configure-includesssmartbackupincludesss-smartbackup-mdmd-using-sql-server-management-studio"></a>Configurer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] à l’aide de SQL Server Management Studio  
 À partir de la **l’Explorateur d’objets**, développez le **gestion** nœud et cliquez à droite sur **sauvegarde managée**. Sélectionnez **Configurer**. La boîte de dialogue **Sauvegarde managée** s'ouvre.  
  
 Vérifiez **activer la gestion de sauvegarde** option et spécifiez les valeurs de configuration :  
  
 Le **fichier rétention** période est spécifiée en jours et doit être comprise entre 1 et 30.  
  
 Le **informations d’identification SQL** vous sélectionnez doit correspondre au compte de stockage. Si vous n’avez pas d’informations d’identification SQL qui stocke les informations d’authentification, vous pouvez en créer un en cliquant sur **créer**. Vous pouvez également créer des informations d'identification à l'aide de l'instruction Transact-SQL CREATE CREDENTIAL et fournir le nom du compte de stockage d'identité et la clé d'accès pour les paramètres SECRET. Pour plus d’informations, consultez [créer les informations d’identification](../relational-databases/backup-restore/sql-server-backup-to-url.md#credential).  
  
 Spécifiez le **URL de stockage** pour le compte de stockage Windows Azure, les informations d’identification SQL qui stocke les informations d’authentification pour le compte de stockage et la période de rétention pour les fichiers de sauvegarde.  
  
 Le format d’URL de stockage est : https://\<StorageAccount >.blob.core.windows.net/  
  
 Pour définir les paramètres de chiffrement au niveau de l’instance, vérifiez **chiffrer la sauvegarde** option et spécifiez l’algorithme et d’un certificat ou clé asymétrique à utiliser pour le chiffrement.  Cette valeur définie au niveau de l'instance est utilisée pour toutes les nouvelles bases de données créées une fois cette configuration appliquée.  
  
> [!WARNING]  
>  Cette boîte de dialogue ne peut pas être utilisé pour spécifier les options de chiffrement sans configuration [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Ces options de chiffrement s’appliquent uniquement aux [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] operations. Pour utiliser le chiffrement pour les autres procédures de sauvegarde, consultez [chiffrement de sauvegarde](../relational-databases/backup-restore/backup-encryption.md).  
  
### <a name="considerations"></a>Observations  
 Si vous configurez [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] au niveau de l’instance, les paramètres sont appliqués aux nouvelles bases de données créées par la suite.  Toutefois, une base de données existante n’hérite pas automatiquement de ces paramètres. Pour configurer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] sur bases de données existantes, vous devez configurer spécifiquement chaque base de données. Pour plus d’informations, consultez [activer et configurer sauvegarde managée SQL Server vers Windows Azure pour une base de données](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).  
  
 Si [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] a été suspendu à l'aide de `smart_admin.sp_backup_master_switch`, vous verrez un message d'avertissement « La sauvegarde managée est désactivée et les configurations actuelles ne prendront pas effet... » lorsque vous essayez de terminer la configuration. Utilisez le `smart_admin.sp_backup_master_switch` stocké et définissez la @new_state= 1. Cette tâche relance [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] services et les paramètres de configuration prennent effet. Pour plus d’informations sur la procédure stockée, consultez [smart_admin.sp_ backup_master_switch &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Managed Backup to Windows Azure : interopérabilité et Coexistence](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
  
