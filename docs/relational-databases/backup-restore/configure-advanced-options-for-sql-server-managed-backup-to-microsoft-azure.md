---
title: Configurer les options avancées pour la sauvegarde managée SQL Server sur Microsoft Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/05/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: ffd28159-8de8-4d40-87da-1586bfef3315
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b9f63c9fed9be5a88c68c88938b77483a077df1e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68081360"
---
# <a name="configure-advanced-options-for-sql-server-managed-backup-to-microsoft-azure"></a>Configurer les options avancées pour la sauvegarde managée SQL Server sur Microsoft Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Ce didacticiel explique comment définir les options avancées pour [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Ces procédures sont nécessaires uniquement si vous avez besoin des fonctionnalités qu’elles proposent. Sinon, vous pouvez activer [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] et utiliser le comportement par défaut.  
  
 Dans chaque scénario, la sauvegarde est spécifiée à l'aide du paramètre `database_name` . Quand le paramètre `database_name` est NULL ou *, les modifications affectent les paramètres par défaut au niveau de l’instance. Les paramètres au niveau de l'instance affectent également les bases de données créées après la modification.  
  
 Une fois que vous avez défini ces paramètres, vous pouvez activer la sauvegarde managée pour la base de données ou l’instance à l’aide de la procédure stockée système [managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md). Pour plus d'informations, consultez [Enable SQL Server Managed Backup to Microsoft Azure](../../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md).  
  
> [!WARNING]  
>  Vous devez toujours configurer les options avancées et les options de planification personnalisées avant d’activer [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] avec [managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md). Sinon, des opérations de sauvegarde indésirables risquent se produire pendant le laps de temps qui sépare l'activation de [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] et la configuration de ces paramètres.  
  
## <a name="configure-encryption"></a>Configurer le chiffrement  
 Les étapes suivantes expliquent comment spécifier les paramètres de chiffrement à l’aide de la procédure stockée [managed_backup.sp_backup_config_advanced &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md).  

[!INCLUDE[Freshness](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

1.  **Définir l'algorithme de chiffrement :** Commencez par définir le nom de l'algorithme de chiffrement à utiliser. Sélectionnez l'une des algorithmes suivants.  
  
    -   AES_128  
  
    -   AES_192  
  
    -   AES_256  
  
    -   TRIPLE_DES_3KEY  
  
    -   NO_ENCRYPTION  
  
2.  **Créer une clé principale de base de données :** Choisissez un mot de passe pour chiffrer la copie de la clé principale qui sera stockée dans la base de données.  
  
    ```  
    -- Creates a database master key.  
    -- The key is encrypted using the password "<master key password>"  
    USE Master;  
    GO  
       CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
    ```  
  
3.  **Créer un certificat de sauvegarde ou une clé asymétrique :** vous pouvez utiliser un certificat ou une clé asymétrique pour le chiffrement. L'exemple suivant crée un certificat de sauvegarde à utiliser pour le chiffrement.  
  
    ```sql  
    USE Master;  
    GO  
       CREATE CERTIFICATE MyTestDBBackupEncryptCert  
          WITH SUBJECT = 'MyTestDBBackupEncryptCert';  
    GO  
    ```  
  
4.  **Définir le chiffrement de sauvegarde managé :** appeler la procédure stockée **managed_backup.sp_backup_config_advanced** avec les valeurs correspondantes. L'exemple suivant configure la base de données `MyDB` pour le chiffrement à l'aide d'un certificat nommé `MyTestDBBackupEncryptCert` et de l’algorithme de chiffrement `AES_128` .  
  
    ```  
    USE msdb;  
    GO  
       EXEC managed_backup.sp_backup_config_advanced  
          @database_name = 'MyDB'                
          ,@encryption_algorithm ='AES_128'  
          ,@encryptor_type = 'CERTIFICATE'  
          ,@encryptor_name = 'MyTestDBBackupEncryptCert';  
    GO  
    ```  
  
    > [!WARNING]  
    >  Si le paramètre `@database_name` a la valeur NULL dans l’exemple précédent, les paramètres s’appliquent à l’instance SQL Server.  
  
## <a name="configure-a-custom-backup-schedule"></a>Configurer une planification de sauvegarde personnalisée  
 Les étapes suivantes expliquent comment définir une planification personnalisée avec la procédure stockée [managed_backup.sp_backup_config_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md).  
  
1.  **Définir la fréquence des sauvegardes complètes :** déterminer la fréquence à laquelle effectuer des sauvegardes complètes de la base de données. Vous pouvez choisir entre des sauvegardes complètes « quotidiennes » ou « hebdomadaires ».  
  
2.  **Définir la fréquence des sauvegardes de fichier journal :** définir la fréquence à laquelle effectuer une sauvegarde de fichier journal. Cette valeur est exprimée en minutes ou en heures.  
  
3.  **Définir le jour de la semaine où seront effectuées les sauvegardes locales :** si la sauvegarde est hebdomadaire, choisissez un jour de la semaine pour la sauvegarde complète.  
  
4.  **Définir l’heure de début de la sauvegarde :** en utilisant la notation sur 24 heures, choisissez une heure de début de la sauvegarde.  
  
5.  **Définir la longueur de la durée autorisée pour la sauvegarde :** ceci indique la durée pendant laquelle une sauvegarde doit être effectuée.  
  
6.  **Définir une planification de sauvegarde personnalisée :** la procédure stockée suivante définit une planification personnalisée pour la base de données `MyDB`. Les sauvegardes complètes sont effectuées toutes les semaines le `Monday` à `17:30`. Les sauvegardes du journal sont effectuées toutes les `5` minutes. Les sauvegardes doivent être effectuées en moins de deux heures.  
  
    ```  
    USE msdb;  
    GO  
    EXEC managed_backup.sp_backup_config_schedule   
         @database_name =  'MyDB'  
        ,@scheduling_option = 'Custom'  
        ,@full_backup_freq_type = 'Weekly'  
        ,@days_of_week = 'Monday'  
        ,@backup_begin_time =  '17:30'  
        ,@backup_duration = '02:00'  
        ,@log_backup_freq = '00:05'  
    GO  
  
    ```  
  
## <a name="next-steps"></a>Next Steps  
 Après avoir configuré les options avancées et les planifications personnalisées, vous devez activer [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] sur la base de données cible ou l’instance SQL Server. Pour plus d'informations, consultez [Enable SQL Server Managed Backup to Microsoft Azure](../../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde managée SQL Server sur Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
