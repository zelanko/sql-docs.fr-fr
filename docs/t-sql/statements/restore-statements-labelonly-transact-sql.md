---
title: RESTORE LABELONLY (Transact-SQL) | Documents Microsoft
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
- LABELONLY
- RESTORE_LABELONLY_TSQL
- LABELONLY_TSQL
- RESTORE LABELONLY
dev_langs:
- TSQL
helpviewer_keywords:
- RESTORE LABELONLY statement
- backup media [SQL Server], content information
ms.assetid: 7cf0641e-0d55-4ffb-9500-ecd6ede85ae5
caps.latest.revision: 46
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f69efb096931108fdaea084b337fcb319f7cfb6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="restore-statements---labelonly-transact-sql"></a>RESTAURER les instructions - LABELONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie un jeu de résultats contenant des informations sur le support de sauvegarde identifié par l'unité de sauvegarde spécifiée.  
  
> [!NOTE]  
>  Pour les descriptions des arguments, consultez [Arguments RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RESTORE LABELONLY   
FROM <backup_device>   
[ WITH   
 {  
--Media Set Options  
   MEDIANAME = { media_name | @media_name_variable }   
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
 Pour obtenir une description des arguments RESTORE LABELONLY, consultez [Arguments RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
## <a name="result-sets"></a>Jeux de résultats  
 Le jeu de résultats renvoyé par RESTORE LABELONLY comporte une seule ligne avec les informations suivantes :  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**MediaName**|**nvarchar (128)**|Nom du support de sauvegarde.|  
|**MediaSetId**|**uniqueidentifier**|Numéro d'identification unique du jeu de supports.|  
|**FamilyCount**|**int**|Nombre de familles de supports dans le support de sauvegarde.|  
|**FamilySequenceNumber**|**int**|Numéro de séquence de la famille.|  
|**MediaFamilyId**|**uniqueidentifier**|Numéro d'identification unique de la famille de supports de sauvegardes.|  
|**MediaSequenceNumber**|**int**|Numéro de séquence de ce support dans la famille de supports.|  
|**MediaLabelPresent**|**tinyint**|Indique si la description du support contient :<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] format de bande<br /><br /> **0** = description du support|  
|**MediaDescription**|**nvarchar(255)**|Description du support, au format libre, ou étiqueté au format de bande.|  
|**SoftwareName**|**nvarchar (128)**|Nom du logiciel de sauvegarde qui a permis l'écriture de l'étiquette du support de sauvegarde.|  
|**SoftwareVendorId**|**int**|Numéro d'identification du fournisseur du logiciel qui a permis l'écriture de la sauvegarde.|  
|**MediaDate**|**datetime**|Date et heure de que l’étiquette.|  
|**Mirror_Count**|**int**|Nombre de miroirs dans le jeu (1-4).<br /><br /> Remarque : Les étiquettes créées pour différents miroirs d’un jeu sont identiques.|  
|**IsCompressed**|**bit**|Indique si la sauvegarde est compressée :<br /><br /> 0 = non compressée<br /><br /> 1 =compressée|  
  
> [!NOTE]  
>  Si des mots de passe sont définis pour le support de sauvegarde, RESTORE LABELONLY ne retourne des informations que si le mot de passe de support adéquat est spécifié dans l'option MEDIAPASSWORD de la commande.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 L'exécution de RESTORE LABELONLY permet de déterminer rapidement le contenu du support de sauvegarde. Comme elle lit uniquement l'en-tête de support, l'instruction RESTORE LABELONLY s'exécute vite, même pour des unités de bande de grande capacité.  
  
## <a name="security"></a>Sécurité  
 Une opération de sauvegarde peut éventuellement spécifier les mots de passe d'un support de sauvegarde. Si un mot de passe est défini dans un support de sauvegarde, vous devez spécifier le mot de passe approprié dans l'instruction RESTORE. Le mot de passe empêche les opérations de restauration non autorisée et non autorisé ajoute des jeux de sauvegarde à l’aide de media [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] outils. En revanche, un mot de passe n'empêche pas d'écraser les supports en cas d'utilisation de l'option FORMAT de l'instruction BACKUP.  
  
> [!IMPORTANT]  
>  La protection assurée par ce mot de passe est plutôt faible. Son but est d'éviter que des utilisateurs autorisés ou non autorisés effectuent une restauration incorrecte à l'aide des outils [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. En aucun cas, elle n'empêche la lecture des données de la sauvegarde par d'autres moyens ou le remplacement du mot de passe. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]La meilleure pratique pour la protection des sauvegardes consiste à stocker les bandes de sauvegarde dans un emplacement sécurisé ou à sauvegarder les fichiers de disque qui sont protégés par des listes de contrôle d’accès adéquates (ACL). La liste de contrôle d'accès doit être définie à la racine du répertoire dans lequel les sauvegardes sont effectuées.  
  
### <a name="permissions"></a>Permissions  
 Dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et les versions ultérieures, l'obtention d'informations relatives à un jeu de sauvegarde ou une unité de sauvegarde requiert l'autorisation CREATE DATABASE. Pour plus d’informations, consultez [GRANT – octroi d’autorisations de base de données &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE REWINDONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Historique de sauvegarde et informations d’en-tête &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  

