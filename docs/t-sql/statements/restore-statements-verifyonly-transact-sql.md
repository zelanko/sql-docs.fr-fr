---
title: RESTORE VERIFYONLY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VERIFYONLY
- RESTORE VERIFYONLY
- VERIFYONLY_TSQL
- RESTORE_VERIFYONLY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- RESTORE VERIFYONLY statement
- backups [SQL Server], verifying
- verifying backups
- checking backups
ms.assetid: cba3b6a0-b48e-4c94-812b-5b3cbb408bd6
caps.latest.revision: 64
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6996997ff66c291285fef4081dc7c21477ea8584
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="restore-statements---verifyonly-transact-sql"></a>RESTAURER les instructions - VERIFYONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Vérifie la sauvegarde sans la restaurer, et s'assure que le jeu de sauvegarde est complet et que tous les volumes sont lisibles. En revanche, l'instruction RESTORE VERIFYONLY ne vérifie pas la structure des données contenues dans les volumes de sauvegarde. Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], RESTORE VERIFYONLY a été améliorée pour effectuer un contrôle supplémentaire sur les données pour augmenter la probabilité de détection des erreurs. Le but est d'être le plus proche possible d'une opération de restauration réelle. Pour plus d'informations, consultez la section Notes.  
  
 Si la sauvegarde est valide, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] renvoie un message de réussite.  
  
> [!NOTE]  
>  Pour les descriptions des arguments, consultez [Arguments RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RESTORE VERIFYONLY  
FROM <backup_device> [ ,...n ]  
[ WITH    
 {  
   LOADHISTORY   
  
--Restore Operation Option  
 | MOVE 'logical_file_name_in_backup' TO 'operating_system_file_name'   
          [ ,...n ]   
  
--Backup Set Options  
 | FILE = { backup_set_file_number | @backup_set_file_number }   
 | PASSWORD = { password | @password_variable }   
  
--Media Set Options  
 | MEDIANAME = { media_name | @media_name_variable }   
 | MEDIAPASSWORD = { mediapassword | @mediapassword_variable }  
  
--Error Management Options  
 | { CHECKSUM | NO_CHECKSUM }   
 | { STOP_ON_ERROR | CONTINUE_AFTER_ERROR }  
  
--Monitoring Options  
 | STATS [ = percentage ]   
  
--Tape Options  
 | { REWIND | NOREWIND }   
 | { UNLOAD | NOUNLOAD }    
 } [ ,...n ]  
]  
[;]  
  
<backup_device> ::=  
{   
   { logical_backup_device_name |  
      @logical_backup_device_name_var }  
   | { DISK | TAPE } = { 'physical_backup_device_name' |  
       @physical_backup_device_name_var }   
}  
  
```  
  
## <a name="arguments"></a>Arguments  
 Pour obtenir une description des arguments RESTORE VERIFYONLY, consultez [Arguments RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Le support de sauvegarde ou le jeu de sauvegarde doivent contenir un minimum d'informations correctes pour pouvoir être interprétés sous Microsoft Tape Format. Dans le cas contraire, RESTORE VERIFYONLY s'arrête et indique que le format de la sauvegarde est incorrect.  
  
 RESTORE VERIFYONLY se charge de vérifier :  
  
-   que le jeu de sauvegarde est complet et que tous les volumes sont lisibles ;  
  
-   certains champs d'en-tête des pages de la base de données, tels que l'ID de la page (comme si l'écriture des données allait avoir lieu) ;  
  
-   la somme de contrôle (si elle figure sur le support) ;  
  
-   s'il y a un espace suffisant sur les périphériques de destination.  
  
> [!NOTE]  
>  RESTORE VERIFYONLY ne fonctionne pas sur un instantané de base de données. Pour vérifier un instantané de base de données avant une opération de restauration, vous pouvez exécuter DBCC CHECKDB.  
  
> [!NOTE]  
>  Avec les sauvegardes d’instantanés, RESTORE VERIFYONLY confirme l’existence des instantanés dans les emplacements spécifiés dans le fichier de sauvegarde. Sauvegardes de captures instantanées sont une nouvelle fonctionnalité dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Pour plus d’informations sur les sauvegardes de captures instantanées, consultez [sauvegardes d’instantanés de fichiers pour les fichiers de base de données dans Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
## <a name="security"></a>Sécurité  
 Une opération de sauvegarde peut éventuellement spécifier des mots de passe pour un support de sauvegarde, un jeu de sauvegarde ou les deux. Lorsqu'un mot de passe a été défini sur un support de sauvegarde ou un jeu de sauvegarde, vous devez entrer le ou les mots de passe corrects dans l'instruction RESTORE. Ces mots de passe empêchent les opérations non autorisées de restauration et d'ajouts de jeux de sauvegarde au support à l'aide d'outils [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. En revanche, un mot de passe n'empêche pas d'écraser les supports en cas d'utilisation de l'option FORMAT de l'instruction BACKUP.  
  
> [!IMPORTANT]  
>  La protection assurée par ce mot de passe est plutôt faible. Son but est d'éviter que des utilisateurs autorisés ou non autorisés effectuent une restauration incorrecte à l'aide des outils [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. En aucun cas, elle n'empêche la lecture des données de la sauvegarde par d'autres moyens ou le remplacement du mot de passe. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]La meilleure pratique pour la protection des sauvegardes consiste à stocker les bandes de sauvegarde dans un emplacement sécurisé ou à sauvegarder les fichiers de disque qui sont protégés par des listes de contrôle d’accès adéquates (ACL). La liste de contrôle d'accès doit être définie à la racine du répertoire dans lequel les sauvegardes sont effectuées.  
  
### <a name="permissions"></a>Permissions  
 Dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], vous devez avoir l'autorisation CREATE DATABASE pour pouvoir obtenir des informations sur un jeu de sauvegardes ou sur une unité de sauvegarde. Pour plus d’informations, consultez [GRANT – octroi d’autorisations de base de données &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE REWINDONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Historique de sauvegarde et informations d’en-tête &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  

