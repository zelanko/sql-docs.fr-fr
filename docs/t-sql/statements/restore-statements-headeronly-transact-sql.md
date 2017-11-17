---
title: RESTORE HEADERONLY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/07/2016
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
- HEADERONLY
- RESTORE HEADERONLY
- RESTORE_HEADERONLY_TSQL
- HEADERONLY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup sets [SQL Server], header information
- headers [SQL Server]
- RESTORE HEADERONLY statement
- backup header information [SQL Server]
ms.assetid: 4b88e98c-49c4-4388-ab0e-476cc956977c
caps.latest.revision: 95
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 694c77c3d59b5565e6c5b25eaf946e9ebaa0e22f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="restore-statements---headeronly-transact-sql"></a>RESTAURER les instructions - HEADERONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie un jeu de résultats contenant toutes les dernières informations d'en-tête des sauvegardes pour tous les jeux de sauvegardes d'un périphérique de sauvegarde particulier dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Pour les descriptions des arguments, consultez [Arguments RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RESTORE HEADERONLY   
FROM <backup_device>   
[ WITH   
 {  
--Backup Set Options  
   FILE = { backup_set_file_number | @backup_set_file_number }   
 | PASSWORD = { password | @password_variable }   
  
--Media Set Options  
 | MEDIANAME = { media_name | @media_name_variable }   
 | MEDIAPASSWORD = { mediapassword | @mediapassword_variable }  
  
--Error Management Options  
 | { CHECKSUM | NO_CHECKSUM }   
 | { STOP_ON_ERROR | CONTINUE_AFTER_ERROR }  
  
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
 Pour obtenir une description des arguments RESTORE HEADERONLY, consultez [Arguments RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
## <a name="result-sets"></a>Jeux de résultats  
 Pour chaque sauvegarde réalisée sur une unité donnée, le serveur envoie une ligne d'informations d'en-tête composée des colonnes suivantes :  
  
> [!NOTE]  
>  RESTORE HEADERONLY recherche tous les jeux de sauvegarde sur le support. Par conséquent, la production de ce jeu de résultats en utilisant des lecteurs de bande à capacité élevée risque de prendre du temps. Pour obtenir un aperçu du support sans récupérer les informations sur chaque jeu de sauvegarde, utilisez RESTORE LABELONLY ou spécifiez le fichier  **=**  *numéro_fichier_jeu_sauvegarde*.  
  
> [!NOTE]  
>  En raison de la nature de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tape Format, il est possible de jeux de sauvegarde à partir d’autres logiciels pour occuper l’espace sur le même support [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] jeux de sauvegarde. Le jeu de résultats renvoyé par RESTORE HEADERONLY inclue une ligne pour chacun de ces autres jeux de sauvegardes.  
  
|Nom de colonne|Type de données|Description des jeux de sauvegardes SQL Server|  
|-----------------|---------------|--------------------------------------------|  
|**Nom_sauvegarde**|**nvarchar (128)**|Nom du jeu de sauvegardes.|  
|**BackupDescription**|**nvarchar(255)**|Description du jeu de sauvegardes.|  
|**Type_sauvegarde**|**smallint**|Type de sauvegarde :<br /><br /> **1** = base de données<br /><br /> **2** = journal des transactions<br /><br /> **4** = fichier<br /><br /> **5** = base de données différentielle<br /><br /> **6** = fichier différentiel<br /><br /> **7** = partiel<br /><br /> **8** = partielle différentielle|  
|**ExpirationDate**|**datetime**|Date d'expiration du jeu de sauvegardes.|  
|**Compressé**|**BYTE(1)**|Indique si le jeu de sauvegarde a fait l'objet d'une compression logicielle :<br /><br /> **0** = non<br /><br /> **1** = Oui|  
|**Position**|**smallint**|Position du jeu de sauvegardes dans le volume (utilisée avec l'option FILE =).|  
|**Type d’appareil**|**tinyint**|Numéro correspondant à l'unité utilisée pour la sauvegarde.<br /><br /> Disque :<br /><br /> **2** = logique<br /><br /> **102** = physique<br /><br /> Bande :<br /><br /> **5** = logique<br /><br /> **105** = physique<br /><br /> Unité virtuelle :<br /><br /> **7** = logique<br /><br /> **107** = physique<br /><br /> Noms d’unités logiques et les numéros d’unité se trouvent dans **sys.backup_devices**; pour plus d’informations, consultez [sys.backup_devices &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md).|  
|**UserName**|**nvarchar (128)**|Nom de l'utilisateur qui a effectué l'opération de sauvegarde.|  
|**ServerName**|**nvarchar (128)**|Nom du serveur qui a permis l'écriture du jeu de sauvegardes.|  
|**DatabaseName**|**nvarchar (128)**|Nom de la base de données qui a été sauvegardée.|  
|**Base de donnéesversion**|**int**|Version de la base de données à partir de laquelle la sauvegarde a été créée.|  
|**DatabaseCreationDate**|**datetime**|Date et heure de création de la base de données.|  
|**BackupSize**|**NUMERIC (20,0)**|Taille de la sauvegarde en octets.|  
|**FirstLSN**|**NUMERIC(25,0)**|Numéro séquentiel dans le journal correspondant au premier enregistrement du journal dans le jeu de sauvegarde.|  
|**LastLSN**|**NUMERIC(25,0)**|Numéro séquentiel dans le journal correspondant à l'enregistrement du journal suivant après le jeu de sauvegarde.|  
|**CheckpointLSN**|**NUMERIC(25,0)**|Numéro séquentiel dans le journal correspondant au point de contrôle le plus récent au moment où la sauvegarde a été créée.|  
|**DatabaseBackupLSN**|**NUMERIC(25,0)**|Numéro séquentiel dans le journal correspondant à la sauvegarde complète la plus récente de la base de données.<br /><br /> **DatabaseBackupLSN** est le « début du point de contrôle » déclenché lors du démarrage de la sauvegarde. Ce LSN coïncide avec **FirstLSN** si la sauvegarde est effectuée lorsque la base de données est inactive et aucune réplication n’est configurée.|  
|**BackupStartDate**|**datetime**|Date et heure de début de l'opération de sauvegarde.|  
|**BackupFinishDate**|**datetime**|Date et heure de fin de l'opération de sauvegarde.|  
|**Ordre de tri**|**smallint**|Ordre de tri du serveur. Cette colonne n'est valide que pour les sauvegardes de base de données. Fourni pour la compatibilité ascendante.|  
|**CodePage**|**smallint**|Page de codes du serveur ou jeu de caractères utilisé par le serveur.|  
|**UnicodeLocaleId**|**int**|Option de configuration de ID locale Unicode du serveur utilisée pour le tri des données caractères Unicode. Fourni pour la compatibilité ascendante.|  
|**UnicodeComparisonStyle**|**int**|Option de configuration du style de comparaison Unicode du serveur qui offre un contrôle supplémentaire du tri des données Unicode. Fourni pour la compatibilité ascendante.|  
|**CompatibilityLevel**|**tinyint**|Paramètre de niveau de compatibilité de la base à partir de laquelle la sauvegarde a été créée.|  
|**SoftwareVendorId**|**int**|Numéro d'identification du fournisseur de logiciel. Pour SQL Server, ce nombre est **4608** (ou hexadécimal **0 x 1200**).|  
|**SoftwareVersionMajor**|**int**|Numéro de version principal du serveur qui a créé le jeu de sauvegardes.|  
|**SoftwareVersionMinor**|**int**|Numéro de version secondaire du serveur qui a créé le jeu de sauvegardes.|  
|**SoftwareVersionBuild**|**int**|Numéro de build du serveur qui a créé le jeu de sauvegardes.|  
|**MachineName**|**nvarchar (128)**|Nom de l'ordinateur qui a effectué l'opération de sauvegarde.|  
|**Indicateurs**|**int**|Les significations de bit d’indicateur individuel si la valeur **1**:<br /><br /> **1** = journal de sauvegarde contient des opérations journalisées en bloc.<br /><br /> **2** = sauvegarde instantanée.<br /><br /> **4** = base de données était en lecture seule lors de la sauvegarde.<br /><br /> **8** = base de données était en mode mono-utilisateur lors de la sauvegarde.<br /><br /> **16** = sauvegarde contient des sommes de contrôle de sauvegarde.<br /><br /> **32** = base de données a été endommagée lors de la sauvegarde, mais l’opération de sauvegarde a été maintenue en dépit des erreurs.<br /><br /> **64** = sauvegarde de la fin du journal.<br /><br /> **128** = sauvegarde de fin du journal avec des métadonnées incomplètes.<br /><br /> **256** = sauvegarde de fin du journal avec NORECOVERY.<br /><br /> **Important :** nous vous recommandons plutôt de **indicateurs** vous utilisez les colonnes booléennes individuelles (répertoriées ci-dessous, commençant par **HasBulkLoggedData** et se terminant par **IsCopyOnly**).|  
|**BindingID**|**uniqueidentifier**|ID de liaison de la base de données. Cela correspond à **sys.database_recovery_status***database_guid**. Lors de la restauration d'une base de données, une nouvelle valeur est attribuée. Consultez également **FamilyGUID** (ci-dessous).|  
|**RecoveryForkID**|**uniqueidentifier**|ID de la fourchette de récupération de fin. Cette colonne correspond à **last_recovery_fork_guid** dans les [backupset](../../relational-databases/system-tables/backupset-transact-sql.md) table.<br /><br /> Pour les sauvegardes de données, **RecoveryForkID** est égal à **FirstRecoveryForkID**.|  
|**Classement**|**nvarchar (128)**|Classement utilisé par la base de données.|  
|**FamilyGUID**|**uniqueidentifier**|ID de la base de données d'origine lors de sa création. Cette valeur reste identique lors de la restauration de la base de données.|  
|**HasBulkLoggedData**|**bit**|**1** = sauvegarde de journal contenant des opérations journalisées en bloc.|  
|**IsSnapshot**|**bit**|**1** = sauvegarde instantanée.|  
|**IsReadOnly**|**bit**|**1** = base de données était en lecture seule lors de la sauvegarde.|  
|**IsSingleUser**|**bit**|**1** = base de données a été mono-utilisateur lors de la sauvegarde.|  
|**HasBackupChecksums**|**bit**|**1** = sauvegarde contient des sommes de contrôle de sauvegarde.|  
|**IsDamaged**|**bit**|**1** = base de données a été endommagée lors de la sauvegarde, mais l’opération de sauvegarde a été maintenue en dépit des erreurs.|  
|**BeginsLogChain**|**bit**|**1** = Ceci est le premier d’une chaîne continue de sauvegardes de journaux. Une séquence de journaux démarre par la première sauvegarde journalisée effectuée après la création de la base de données, ou lorsqu'elle passe du mode de récupération simple à complète ou utilisant les journaux de transactions.|  
|**HasIncompleteMetaData**|**bit**|**1** = une sauvegarde de la fin du journal avec des métadonnées incomplètes.<br /><br /> Pour plus d’informations sur les sauvegardes de la fin du journal avec des métadonnées incomplètes, consultez [sauvegardes de la fin du journal &#40; SQL Server &#41; ](../../relational-databases/backup-restore/tail-log-backups-sql-server.md).|  
|**IsForceOffline**|**bit**|**1** = sauvegarde effectuée avec NORECOVERY ; la base de données a été effectuée en mode hors connexion par la sauvegarde.|  
|**IsCopyOnly**|**bit**|**1** = sauvegarde de copie uniquement.<br /><br /> Une sauvegarde de copie unique n'influe pas sur les procédures globales de sauvegarde et de restauration de la base de données. Pour plus d’informations, consultez [Sauvegardes de copie uniquement &#40;SQL Server&#41;](../../relational-databases/backup-restore/copy-only-backups-sql-server.md).|  
|**FirstRecoveryForkID**|**uniqueidentifier**|ID de la fourchette de récupération de début. Cette colonne correspond à **first_recovery_fork_guid** dans les [backupset](../../relational-databases/system-tables/backupset-transact-sql.md) table.<br /><br /> Pour les sauvegardes de données, **FirstRecoveryForkID** est égal à **RecoveryForkID**.|  
|**ForkPointLSN**|**NUMERIC(25,0)** NULL|Si **FirstRecoveryForkID** n’est pas égal à **RecoveryForkID**, il s’agit du numéro de séquence de journal du point du branchement. Dans les autres cas, cette valeur est NULL.|  
|**RecoveryModel**|**nvarchar (60)**|Modèle de restauration de la base de données, parmi<br /><br /> FULL<br /><br /> BULK-LOGGED<br /><br /> SIMPLE|  
|**DifferentialBaseLSN**|**NUMERIC(25,0)** NULL|Pour une sauvegarde différentielle unique, la valeur est égale à la **FirstLSN** de la base différentielle ; les modifications avec des LSN supérieurs ou égales à **DifferentialBaseLSN** sont inclus dans la sauvegarde différentielle.<br /><br /> Pour une sauvegarde différentielle multiple, la valeur est NULL, tandis que le LSN de base doit être déterminé au niveau du fichier. Pour plus d’informations, consultez [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md).<br /><br /> Pour les types de sauvegarde non différentiels, la valeur est toujours NULL.<br /><br /> Pour plus d’informations, consultez [Sauvegardes différentielles &#40;SQL Server&#41;](../../relational-databases/backup-restore/differential-backups-sql-server.md).|  
|**DifferentialBaseGUID**|**uniqueidentifier**|Pour une sauvegarde différentielle unique, cette valeur constitue l'identificateur unique de la base différentielle.<br /><br /> Pour les sauvegardes différentielles multiples, cette valeur est NULL, tandis que la base différentielle doit être déterminée par fichier.<br /><br /> Pour les types de sauvegarde non différentiels, la valeur est NULL.|  
|**BackupTypeDescription**|**nvarchar (60)**|Type de sauvegarde en tant que chaîne, parmi :<br /><br /> DATABASE<br /><br /> JOURNAL DES TRANSACTIONS<br /><br /> FICHIER OU GROUPE DE FICHIERS<br /><br /> BASE DE DONNÉES DIFFÉRENTIELLE<br /><br /> FICHIER DIFFÉRENTIEL PARTIEL<br /><br /> DIFFÉRENTIEL PARTIEL|  
|**BackupSetGUID**|**uniqueidentifier** NULL|Numéro d'identification unique du jeu de sauvegardes, par lequel s'effectue l'identification sur le support.|  
|**CompressedBackupSize**|**bigint**|Nombre d'octets du jeu de sauvegarde. Pour les sauvegardes non compressées, cette valeur est identique à **BackupSize**.<br /><br /> Pour calculer le taux de compression, utilisez **CompressedBackupSize** et **BackupSize**.<br /><br /> Pendant une **msdb** mise à niveau, cette valeur est définie pour correspondre à la valeur de la **BackupSize** colonne.|  
|**relation contenant-contenu**|**tinyint** non NULL|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Indique l'état de la relation contenant-contenu de la base de données.<br /><br /> 0 = La relation contenant-contenu de base de données est désactivée<br /><br /> 1 = La base de données est dans une relation contenant-contenu partielle|  
|**KeyAlgorithm**|**nvarchar(32)**|**S’applique aux**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (CU1) jusqu'à la version actuelle.<br /><br /> Algorithme de chiffrement utilisé pour chiffrer la sauvegarde. La valeur NO_Encryption indique que la sauvegarde n'est pas chiffrée. Lorsque la valeur correcte ne peut pas être déterminée, la valeur doit être NULL.|  
|**EncryptorThumbprint**|**varbinary(20)**|**S’applique aux**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (CU1) jusqu'à la version actuelle.<br /><br /> Empreinte numérique du chiffreur pouvant être utilisé pour rechercher un certificat ou la clé asymétrique dans la base de données. Si la sauvegarde n'est pas chiffrée, cette valeur est NULL.|  
|**EncryptorType**|**nvarchar(32)**|**S’applique aux**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (CU1) jusqu'à la version actuelle.<br /><br /> Type de chiffreur utilisé : certificat ou clé asymétrique Si la sauvegarde n'est pas chiffrée, cette valeur est NULL.|  
  
> [!NOTE]  
>  Si des mots de passe sont définis pour les jeux de sauvegarde, RESTORE HEADERONLY n'affiche que les informations complètes relatives au jeu de sauvegarde dont le mot de passe correspond à la définition de l'option PASSWORD de la commande. RESTORE HEADERONLY affiche également les informations complètes relatives aux jeux de sauvegarde non protégés. Le **Nom_sauvegarde** colonne pour les autres protégé par mot de passe jeux de sauvegarde sur le support est défini sur « *** protégé par mot de passe\*\*\*», et toutes les autres colonnes sont NULL.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Un client peut utiliser RESTORE HEADERONLY pour récupérer toutes les informations des en-têtes de sauvegarde pour toutes les sauvegardes figurant sur une unité particulière. Pour chaque sauvegarde réalisée sur une unité de sauvegarde, le serveur envoie les informations d'en-tête sous forme de ligne.  
  
## <a name="security"></a>Sécurité  
 Une opération de sauvegarde peut éventuellement spécifier des mots de passe pour un support de sauvegarde, un jeu de sauvegarde ou les deux. Lorsqu'un mot de passe a été défini sur un support de sauvegarde ou un jeu de sauvegarde, vous devez entrer le ou les mots de passe corrects dans l'instruction RESTORE. Ces mots de passe empêchent les opérations de restauration non autorisée et non autorisé ajoute des jeux de sauvegarde à l’aide de media [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] outils. En revanche, un mot de passe n'empêche pas d'écraser les supports en cas d'utilisation de l'option FORMAT de l'instruction BACKUP.  
  
> [!IMPORTANT]  
>  La protection assurée par ce mot de passe est plutôt faible. Son but est d'éviter que des utilisateurs autorisés ou non autorisés effectuent une restauration incorrecte à l'aide des outils [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. En aucun cas, elle n'empêche la lecture des données de la sauvegarde par d'autres moyens ou le remplacement du mot de passe. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]La meilleure pratique pour la protection des sauvegardes consiste à stocker les bandes de sauvegarde dans un emplacement sécurisé ou à sauvegarder les fichiers de disque qui sont protégés par des listes de contrôle d’accès adéquates (ACL). La liste de contrôle d'accès doit être définie à la racine du répertoire dans lequel les sauvegardes sont effectuées.  
  
### <a name="permissions"></a>Permissions  
 Vous devez avoir l'autorisation CREATE DATABASE pour pouvoir obtenir des informations sur un jeu de sauvegardes ou sur une unité de sauvegarde. Pour plus d’informations, consultez [GRANT – octroi d’autorisations de base de données &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant renvoie les informations contenues dans l'en-tête pour le fichier de disque `C:\AdventureWorks-FullBackup.bak`.  
  
```  
RESTORE HEADERONLY   
FROM DISK = N'C:\AdventureWorks-FullBackup.bak'   
WITH NOUNLOAD;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [RESTORE REWINDONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Historique de sauvegarde et informations d’en-tête &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)   
 [Activer ou désactiver des sommes de contrôle de sauvegarde pendant la sauvegarde ou de restauration &#40; SQL Server &#41;](../../relational-databases/backup-restore/enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)   
 [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [Modes de récupération &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)  
  
  

