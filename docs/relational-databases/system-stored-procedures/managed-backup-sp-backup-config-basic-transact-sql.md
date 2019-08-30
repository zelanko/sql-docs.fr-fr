---
title: managed_backup. sp_backup_config_basic (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_backup_config_basic_TSQL
- sp_backup_config_basic
- managed_backup.sp_backup_config_basic
- managed_backup.sp_backup_config_basic_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- managed_backup.sp_backup_config_basic
- sp_backup_config_basic
ms.assetid: 3ad73051-ae9a-4e41-a889-166146e5508f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 92cbea99941b6e9378c4400ae0b563d462c34f27
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70152032"
---
# <a name="managed_backupsp_backup_config_basic-transact-sql"></a>managed_backup. sp_backup_config_basic (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Configure les [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] paramètres de base pour une base de données spécifique ou pour une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]instance de.  
  
> [!NOTE]  
>  Cette procédure peut être appelée seule pour créer une configuration de sauvegarde managée de base. Toutefois, si vous envisagez d’ajouter des fonctionnalités avancées ou un calendrier personnalisé, commencez par configurer ces paramètres à l’aide de [managed_backup. sp_backup_config_advanced &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md) et de [managed_backup. sp_backup_config_schedule &#40; Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md) avant d’activer la sauvegarde managée avec cette procédure.  
   
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```Transact-SQL   
EXEC managed_backup.sp_backup_config_basic  
    [@enable_backup = ] { 0 | 1}    ,[@database_name = ] 'database_name'    ,[@container_url = ] 'Azure_Storage_blob_container  
    ,[@retention_days = ] 'retention_period_in_days'    ,[@credential_name = ] 'sql_credential_name'  
```  
  
##  <a name="Arguments"></a> Arguments  
 @enable_backup  
 Activez ou désactivez la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour la base de données spécifiée. Est @enable_backup un **bit**. Paramètre requis lors de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] configuration de pour la première [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]instance de. Si vous modifiez une configuration existante [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] , ce paramètre est facultatif. Dans ce cas, toutes les valeurs de configuration non spécifiées conservent leurs valeurs existantes.  
  
 @database_name  
 Nom de la base de données pour activer la sauvegarde managée sur une base de données spécifique.  
  
 @container_url  
 URL indiquant l’emplacement de la sauvegarde. Lorsque @credential_name a la valeur null, cette URL est une URL de signature d’accès partagé (SAS) vers un conteneur d’objets BLOB dans le stockage Azure, et les sauvegardes utilisent la nouvelle sauvegarde pour bloquer les fonctionnalités d’objet BLOB. Pour plus d’informations, consultez la présentation de la [technologie](https://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-1/)SAP. Lorsque @credential_name est spécifié, il s’agit d’une URL de compte de stockage, et les sauvegardes utilisent la fonctionnalité de sauvegarde déconseillée de l’objet blob de pages.  
  
> [!NOTE]  
>  Pour l’instant, seule une URL SAS est prise en charge pour ce paramètre.  
  
 @retention_days  
 Période de rétention en jours des fichiers de sauvegarde. Est @storage_url de type int. Il s’agit d’un paramètre obligatoire quand [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] vous configurez pour la première fois [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sur l’instance de. Lors de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] modification de la configuration, ce paramètre est facultatif. S'il n'est pas spécifié, les valeurs de configuration existantes sont retenues.  
  
 @credential_name  
 Nom des informations d’identification SQL utilisées pour l’authentification auprès du compte de stockage Azure. @credentail_nameest de **type sysname**. Lorsque cette valeur est spécifiée, la sauvegarde est stockée dans un objet blob de pages. Si ce paramètre a la valeur NULL, la sauvegarde est stockée en tant qu’objet blob de blocs. La sauvegarde vers l’objet blob de pages est dépréciée. il est donc préférable d’utiliser la nouvelle fonctionnalité de sauvegarde des objets BLOB de blocs. Lorsqu'il est utilisé pour modifier la configuration de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], ce paramètre est facultatif. S’il n’est pas spécifié, les valeurs de configuration existantes sont conservées.  
  
> [!WARNING]
>  Le **@credential_name** paramètre n’est pas pris en charge pour l’instant. Seule la sauvegarde sur un objet blob de blocs est prise en charge, ce qui requiert la valeur NULL pour ce paramètre.  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 Requiert l’appartenance au rôle de base de données **db_backupoperator** , avec les autorisations **ALTER ANY CREDENTIAL** et Execute sur la procédure stockée **sp_delete_backuphistory** .  
  
## <a name="examples"></a>Exemples  
 Vous pouvez créer le conteneur de compte de stockage et l’URL SAS à l’aide des commandes Azure PowerShell les plus récentes. L’exemple suivant crée un nouveau conteneur, mycontainer, dans le compte de stockage mystorageaccount, puis obtient une URL SAS pour celui-ci avec des autorisations complètes.  
  
```powershell  
$context = New-AzureStorageContext -StorageAccountName mystorageaccount -StorageAccountKey (Get-AzureStorageKey -StorageAccountName mystorageaccount).Primary  
New-AzureStorageContainer -Name mycontainer -Context $context  
New-AzureStorageContainerSASToken -Name mycontainer -Permission rwdl -FullUri -Context $context  
```  
  
 L’exemple suivant active [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] l’instance de SQL Server sur laquelle il est exécuté, définit la stratégie de rétention sur 30 jours, définit la destination sur un conteneur nommé «mycontainer» dans un compte de stockage nommé «mystorageaccount».  
  
```Transact-SQL 
Use msdb;  
Go  
   EXEC managed_backup.sp_backup_config_basic  
                @enable_backup=1  
                ,@container_url = 'https://mystorageaccount.blob.core.windows.net/mycontainer'  
                ,@retention_days=30;   
GO  
  
```
  
 L'exemple suivant désactive la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour l'instance de SQL Server sur laquelle elle est exécutée.  
  
```Transact-SQL  
Use msdb;  
Go  
EXEC managed_backup.sp_backup_config_basic  
                @enable_backup=0;  
GO  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [managed_backup.sp_backup_config_advanced &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)   
 [managed_backup.sp_backup_config_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)  
  
  
