---
title: Configurer la gestion de sauvegarde (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.managedbackup.configure.f1
ms.assetid: 79397cf6-0611-450a-b0d8-e784a76e3091
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2f8c9664baa2803bbab4282b6897d49f0ddb1831
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62812706"
---
# <a name="configure-managed-backup-sql-server-management-studio"></a>Configuration de la sauvegarde managée (SQL Server Management Studio)
  Le **sauvegarde managée** boîte de dialogue permet de configurer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] valeurs par défaut pour l’instance. Cette rubrique explique comment utiliser cette boîte de dialogue pour configurer les paramètres [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] par défaut de l'instance et les options à prendre en compte. Lorsque [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est configuré pour l'instance, les paramètres sont appliqués aux nouvelles bases de données créées par la suite.  
  
 Si vous souhaitez configurer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une base de données spécifique, consultez [activer et configurer sauvegarde managée SQL Server sur Windows Azure pour une base de données](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).  
 
> [!NOTE] 
> La Gestion de sauvegarde SQL Server n’est pas prise en charge avec les serveurs proxy. 
  
## <a name="task-list"></a>Liste des tâches  
  
## <a name="includesssmartbackupincludesss-smartbackup-mdmd-functions-using-managed-backup-interface-in-sql-server-management-studio"></a>[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Fonctions utilisant l’interface de sauvegarde managée dans SQL Server Management Studio  
 Dans cette version, vous pouvez uniquement configurer des paramètres par défaut au niveau de l’instance à l’aide de la **Management sauvegarde** interface. Vous ne pouvez pas configurer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une base de données, suspendre ou reprendre des opérations [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ou configurer des notifications par courrier électronique. Pour plus d’informations sur la façon d’effectuer des opérations non pris en charge par le biais du **sauvegarde managée** l’interface, consultez [SQL Server Managed Backup pour Windows Azure - paramètres de rétention et stockage](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).  
  
## <a name="permissions"></a>Autorisations  
 **Nœud de sauvegarde vue managé est SQL Server Management Studio :** Pour afficher les **sauvegarde managée** nœud **Explorateur d’objets**, vous devez être un administrateur système ou accordé les autorisations suivantes spécifiquement à votre compte d’utilisateur :  
  
-   `db_backupoperator`  
  
-   `VIEW SERVER STATE`  
  
-   `ALTER ANY CREDENTIAL`  
  
-   `VIEW ANY DEFINITION`  
  
-   `EXECUTE` sur `smart_admin.fn_is_master_switch_on`.  
  
-   `SELECT` sur `smart_admin.fn_backup_instance_config`.  
  
 **Pour configurer des sauvegardes managées :** pour configurer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] dans SQL Server Management Studio, vous devez être un administrateur système ou disposer des autorisations suivantes :  
  
 L'appartenance au rôle de base de données `db_backupoperator`, avec autorisations `ALTER ANY CREDENTIAL` et autorisations `EXECUTE` sur la procédure stockée `sp_delete_backuphistory`.  
  
 `SELECT` autorisations sur le `smart_admin.fn_get_current_xevent_settings` (fonction).  
  
 `EXECUTE` autorisations sur le `smart_admin.sp_get_backup_diagnostics` procédure stockée. En outre, nécessite les autorisations `VIEW SERVER STATE`, car elle appelle en interne d'autres objets système qui nécessitent cette autorisation.  
  
 Autorisations `EXECUTE` sur `smart_admin.sp_set_instance_backup` et `smart_admin.sp_backup_master_switch`.  
  
## <a name="configure-includesssmartbackupincludesss-smartbackup-mdmd-using-sql-server-management-studio"></a>Configuration de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] à l'aide de SQL Server Management Studio  
 À partir de la **Explorateur d’objets**, développez le **gestion** nœud et clic droit sur **sauvegarde managée**. Sélectionnez **Configurer**. La boîte de dialogue **Sauvegarde managée** s'ouvre.  
  
 Vérifiez **activer la sauvegarde managée** option et spécifiez les valeurs de configuration :  
  
 Le **fichier rétention** période est spécifiée en jours et doit être comprise entre 1 et 30.  
  
 Le **informations d’identification SQL** vous sélectionnez doit correspondre au compte de stockage. Si vous n’avez pas d’informations d’identification SQL qui stocke les informations d’authentification, vous pouvez en créer un en cliquant sur **créer**. Vous pouvez également créer des informations d'identification à l'aide de l'instruction Transact-SQL CREATE CREDENTIAL et fournir le nom du compte de stockage d'identité et la clé d'accès pour les paramètres SECRET. Pour plus d’informations, consultez [créer une information d’identification](../relational-databases/backup-restore/sql-server-backup-to-url.md#credential).  
  
 Spécifiez le **URL de stockage** pour le compte de stockage Windows Azure, les informations d’identification SQL qui stocke les informations d’authentification pour le compte de stockage et la période de rétention pour les fichiers de sauvegarde.  
  
 Le format d’URL de stockage est : https://\<StorageAccount >.blob.core.windows.net/  
  
 Pour définir les paramètres de chiffrement au niveau de l’instance, vérifiez **chiffrer la sauvegarde** option et spécifiez l’algorithme et d’un certificat ou clé asymétrique à utiliser pour le chiffrement.  Cette valeur définie au niveau de l'instance est utilisée pour toutes les nouvelles bases de données créées une fois cette configuration appliquée.  
  
> [!WARNING]  
>  Cette boîte de dialogue ne peut pas être utilisée pour spécifier les options de chiffrement sans configuration de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Ces options de chiffrement s'appliquent uniquement aux opérations [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Pour utiliser le chiffrement pour les autres procédures de sauvegarde, consultez [chiffrement de sauvegarde](../relational-databases/backup-restore/backup-encryption.md).  
  
### <a name="considerations"></a>Observations  
 Si vous configurez [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] au niveau de l'instance, les paramètres sont appliqués aux nouvelles bases de données créées par la suite.  Toutefois, une base de données existante n’hérite pas automatiquement de ces paramètres. Pour configurer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] sur des bases de données existantes, vous devez configurer spécifiquement chaque base de données. Pour plus d’informations, consultez [activer et configurer sauvegarde managée SQL Server sur Windows Azure pour une base de données](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).  
  
 Si [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] a été suspendu à l’aide de la `smart_admin.sp_backup_master_switch`, vous verrez un avertissement de message « sauvegarde managée est désactivée et les configurations actuelles ne prendront effet... » lorsque vous essayez d’effectuer la configuration. Utilisez le `smart_admin.sp_backup_master_switch` stocké et définissez la @new_state= 1. Cela relance les services [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] et les paramètres de configuration prennent effet. Pour plus d’informations sur la procédure stockée, consultez [smart_admin.sp_ backup_master_switch &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde managée SQL Server sur Windows Azure : Interopérabilité et Coexistence](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
  
