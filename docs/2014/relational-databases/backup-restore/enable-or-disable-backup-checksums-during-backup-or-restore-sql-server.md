---
title: Activer ou désactiver des sommes de contrôle de sauvegarde au cours d’opérations de sauvegarde ou de restauration (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup checksums [SQL Server]
- disabling checksums
- checksums [SQL Server]
ms.assetid: 6786bd1e-ad97-430a-8dfb-d4ba952d6c4d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d5783f393cbbe70e89e2d1ee4b7e05481fdc3ab9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62922100"
---
# <a name="enable-or-disable-backup-checksums-during-backup-or-restore-sql-server"></a>Activer ou désactiver des sommes de contrôle de sauvegarde au cours d'opérations de sauvegarde ou de restauration (SQL Server)
  Cette rubrique décrit comment activer ou désactiver les sommes de contrôle de sauvegarde lorsque vous sauvegardez ou restaurez une base de données dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour activer ou désactiver les sommes de contrôle de sauvegarde, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 BACKUP  
 Les autorisations BACKUP DATABASE et BACKUP LOG reviennent par défaut aux membres du rôle serveur fixe **sysadmin** et des rôles de base de données fixes **db_owner** et **db_backupoperator** .  
  
 Des problèmes de propriété et d'autorisations sur le fichier physique de l'unité de sauvegarde sont susceptibles de perturber une opération de sauvegarde. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être en mesure de lire et d'écrire sur l'unité ; le compte sous lequel le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute doit avoir des autorisations d'écriture. Toutefois, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), qui ajoute une entrée pour une unité de sauvegarde dans les tables système, ne vérifie pas les autorisations d’accès au fichier. De tels problèmes pour le fichier physique de l'unité de sauvegarde peuvent n'apparaître que lorsque la ressource physique est sollicitée au moment de la sauvegarde ou de la restauration.  
  
 RESTORE  
 Si la base de données restaurée n'existe pas, l'utilisateur doit posséder les autorisations CREATE DATABASE afin de pouvoir exécuter RESTORE. Si la base de données existe, les autorisations RESTORE reviennent par défaut aux membres des rôles serveur fixe **sysadmin** et **dbcreator** et au propriétaire (**dbo**) de la base de données (pour l’option FROM DATABASE_SNAPSHOT, la base de données existe toujours).  
  
 Les autorisations RESTORE sont attribuées aux rôles dont les informations d'appartenance sont toujours immédiatement accessibles à partir du serveur. Étant donné que l’appartenance au rôle de base de données fixe ne peut être contrôlée que quand la base de données est accessible et non endommagée, ce qui n’est pas toujours le cas lorsque RESTORE est exécuté, les membres du rôle de base de données fixe **db_owner** ne détiennent pas d’autorisations RESTORE.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-enable-or-disable-checksums-during-a-backup-operation"></a>Pour activer ou désactiver les sommes de contrôle pendant une opération de sauvegarde  
  
1.  Suivez les étapes pour [créer une sauvegarde de base de données](create-a-full-database-backup-sql-server.md).  
  
2.  Sur la page **Options** , dans la section **Fiabilité** , cliquez sur **Effectuer une somme de contrôle avant d'écrire sur le support**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-enable-or-disable-backup-checksum-for-a-backup-operation"></a>Pour activer ou désactiver la somme de contrôle de sauvegarde pour une opération de sauvegarde  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Pour activer les sommes de contrôle de sauvegarde dans une instruction [BACKUP](/sql/t-sql/statements/backup-transact-sql) , spécifiez l'option WITH CHECKSUM. Pour désactiver les sommes de contrôle de sauvegarde, spécifiez l'option WITH NO_CHECKSUM. Ceci est le comportement par défaut, sauf pour une sauvegarde compressée. L'exemple suivant spécifie que les sommes de contrôle doivent être effectuées.  
  
```sql  
BACKUP DATABASE AdventureWorks2012   
 TO DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM;  
GO  
```  
  
#### <a name="to-enable-or-disable-backup-checksum-for-a-restore-operation"></a>Pour activer ou désactiver la somme de contrôle de sauvegarde pour une opération de restauration  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Pour activer les sommes de contrôle de sauvegarde dans une instruction [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) , spécifiez l'option WITH CHECKSUM. Ceci est le comportement par défaut pour une sauvegarde compressée. Pour désactiver les sommes de contrôle de sauvegarde, spécifiez l'option WITH NO_CHECKSUM. Ceci est le comportement par défaut, sauf pour une sauvegarde compressée. L'exemple suivant spécifie que les sommes de contrôle de sauvegarde doivent être effectuées.  
  
```sql  
RESTORE DATABASE AdventureWorks2012   
 FROM DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM;  
GO  
```  
  
> [!WARNING]  
>  Si vous spécifiez explicitement CHECKSUM pour une opération de restauration et que la sauvegarde contient des sommes de contrôle de sauvegarde, ces sommes de contrôle de sauvegarde ainsi que les sommes de contrôle de page sont vérifiées, comme dans le cas par défaut. Toutefois, si le jeu de sauvegarde manque de sommes de contrôle de sauvegarde, l'opération de restauration se solde par un échec et l'affichage d'un message indiquant l'absence des sommes de contrôle.  
  
## <a name="see-also"></a>Voir aussi  
 [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)   
 [RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)   
 [RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql)   
 [Arguments RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)   
 [Erreurs de support possibles pendant les opérations de sauvegarde et de restauration &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)   
 [Spécifier si une opération de sauvegarde ou de restauration continue ou s’arrête après la survenue d’une erreur &#40;SQL Server&#41;](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
  
