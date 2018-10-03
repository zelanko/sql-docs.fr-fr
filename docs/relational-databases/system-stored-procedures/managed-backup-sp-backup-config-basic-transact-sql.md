---
title: managed_backup.sp_backup_config_basic (Transact-SQL) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 93e6bcfc4ec686f61672fa382d545db5a7000f96
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47838797"
---
# <a name="managedbackupspbackupconfigbasic-transact-sql"></a>managed_backup.sp_backup_config_basic (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Configure le [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] les paramètres de base pour une base de données spécifique ou d’une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Cette procédure peut être appelée sur son propre pour créer une configuration de sauvegarde managée de base. Toutefois, si vous prévoyez d’ajouter des fonctionnalités avancées ou une planification personnalisée, d’abord configurer ces paramètres à l’aide de [managed_backup.sp_backup_config_advanced &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md) et [managed_backup.sp_ backup_config_schedule &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md) avant d’activer la gestion de sauvegarde avec cette procédure.  
   
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```Transact-SQL   
EXEC managed_backup.sp_backup_config_basic  
    [@enable_backup = ] { 0 | 1}    ,[@database_name = ] 'database_name'    ,[@container_url = ] 'Azure_Storage_blob_container  
    ,[@retention_days = ] 'retention_period_in_days'    ,[@credential_name = ] 'sql_credential_name'  
```  
  
##  <a name="Arguments"></a> Arguments  
 @enable_backup  
 Activez ou désactivez la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour la base de données spécifiée. Le @enable_backup est **bits**. Paramètre obligatoire lors de la configuration [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour la première instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous modifiez un existant [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] configuration, ce paramètre est facultatif. Dans ce cas, les valeurs de configuration sauf indication contraire conservent leurs valeurs existantes.  
  
 @database_name  
 Le nom de la base de données, permettant la gestion de sauvegarde sur une base de données spécifique.  
  
 @container_url  
 Une URL qui indique l’emplacement de la sauvegarde. Lorsque @credential_name est NULL, cette URL est une URL de signature (SAP) d’accès partagé à un conteneur d’objets blob dans le stockage Azure et les sauvegardes utilisent la nouvelle sauvegarde à la fonctionnalité d’objet blob de bloc. Pour plus d’informations, consultez [compréhension SAS](http://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-1/). Lorsque @credential_name est spécifié, il s’agit d’une URL de compte de stockage et les sauvegardes utilisent la sauvegarde obsolète à la fonctionnalité d’objet blob de page.  
  
> [!NOTE]  
>  Uniquement une URL SAS est pris en charge pour ce paramètre pour l’instant.  
  
 @retention_days  
 Période de rétention en jours des fichiers de sauvegarde. Le @storage_url est INT. Ce paramètre est obligatoire lors de la configuration [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour la première fois sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Lors de la modification la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] configuration, ce paramètre est facultatif. S'il n'est pas spécifié, les valeurs de configuration existantes sont retenues.  
  
 @credential_name  
 Nom des informations d'identification SQL utilisées pour identifier le compte de stockage Windows Azure. @credentail_name est **SYSNAME**. Si spécifié, la sauvegarde est stockée à un objet blob de pages. Si ce paramètre est NULL, la sauvegarde est stockée comme un objet blob de blocs. Sauvegarde à l’objet blob de pages est déconseillé, c’est pourquoi il est préférable d’utiliser la nouvelle fonctionnalité de sauvegarde de blob bloc. Lorsqu'il est utilisé pour modifier la configuration de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], ce paramètre est facultatif. Si non spécifié, les valeurs de configuration existantes sont conservées.  
  
> [!WARNING]  
>  Le **@credential_name** paramètre n’est pas pris en charge pour l’instant. Sauvegarde uniquement pour l’objet blob de blocs est pris en charge, ce qui nécessite ce paramètre pour avoir la valeur NULL.  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Permissions  
 Nécessite l’appartenance au **db_backupoperator** rôle, de base de données avec **ALTER ANY CREDENTIAL** autorisations, et **EXECUTE** autorisations sur **sp_delete_ backuphistory** procédure stockée.  
  
## <a name="examples"></a>Exemples  
 Vous pouvez créer le conteneur de compte de stockage et l’URL de SAP en utilisant les dernières commandes Azure PowerShell. L’exemple suivant crée un nouveau conteneur, mycontainer, dans le compte de stockage mystorageaccount et obtient ensuite une URL SAS pour celle-ci avec des autorisations complètes.  
  
```powershell  
$context = New-AzureStorageContext -StorageAccountName mystorageaccount -StorageAccountKey (Get-AzureStorageKey -StorageAccountName mystorageaccount).Primary  
New-AzureStorageContainer -Name mycontainer -Context $context  
New-AzureStorageContainerSASToken -Name mycontainer -Permission rwdl -FullUri -Context $context  
```  
  
 L’exemple suivant active [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour l’instance de SQL Server, elle est exécutée, définit la stratégie de rétention de 30 jours, définit la destination dans un conteneur nommé « mycontainer » dans un compte de stockage nommé « mystorageaccount ».  
  
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
  
  
