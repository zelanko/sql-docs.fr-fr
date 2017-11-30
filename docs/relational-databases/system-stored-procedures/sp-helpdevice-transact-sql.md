---
title: sp_helpdevice (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helpdevice
- sp_helpdevice_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_helpdevice
ms.assetid: 1a5eafa7-384e-4691-ba05-978eb73bbefb
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a39dcc6cd75837017826fdcf9b37ff7d6a3598c9
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="sphelpdevice-transact-sql"></a>sp_helpdevice (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Transmet des informations sur les unités de sauvegarde Microsoft® SQL Server™.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Nous vous recommandons d’utiliser le [sys.backup_devices](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md) affichage du catalogue à la place  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpdevice [ [ @devname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@devname =** ] **'***nom***'**  
 Nom de l'unité de sauvegarde à propos de laquelle des informations sont transmises. La valeur de *nom* est toujours **sysname**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**nom_unité**|**sysname**|Nom de périphérique logique.|  
|**physical_name**|**nvarchar (260)**|Nom de fichier physique.|  
|**Description**|**nvarchar(255)**|Description du périphérique.|  
|**status**|**int**|Un nombre qui correspond à la description de l’état dans le **description** colonne.|  
|**CntrlType**|**smallint**|Type de contrôleur du périphérique :<br /><br /> 2 = unité de disque<br /><br /> 5 = périphérique à bandes|  
|**taille**|**int**|Taille du périphérique (en pages de 2 Ko).|  
  
## <a name="remarks"></a>Notes  
 Si *nom* est spécifié, **sp_helpdevice** affiche des informations sur l’unité de vidage spécifiée. Si *nom* n’est pas spécifié, **sp_helpdevice** affiche des informations sur toutes les unités de vidage dans le **sys.backup_devices** affichage catalogue.  
  
 Unités de vidage sont ajoutées au système à l’aide de **sp_addumpdevice**.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 Cet exemple vous renseigne sur toutes les unités de vidage d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
EXEC sp_helpdevice;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_dropdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md)   
 [Moteur de base de données stockée procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
