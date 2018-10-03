---
title: sp_helpdevice (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpdevice
- sp_helpdevice_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdevice
ms.assetid: 1a5eafa7-384e-4691-ba05-978eb73bbefb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3ec03794e60027ea578988dbe38855d8ad14cb09
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47596797"
---
# <a name="sphelpdevice-transact-sql"></a>sp_helpdevice (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Transmet des informations sur les unités de sauvegarde Microsoft® SQL Server™.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Nous vous recommandons d’utiliser le [sys.backup_devices](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md) à la place de vue de catalogue  
  
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
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**device_name**|**sysname**|Nom de périphérique logique.|  
|**physical_name**|**nvarchar(260)**|Nom de fichier physique.|  
|**description**|**nvarchar(255)**|Description du périphérique.|  
|**status**|**Int**|Un nombre qui correspond à la description d’état dans le **description** colonne.|  
|**cntrltype**|**smallint**|Type de contrôleur du périphérique :<br /><br /> 2 = unité de disque<br /><br /> 5 = périphérique à bandes|  
|**size**|**Int**|Taille du périphérique (en pages de 2 Ko).|  
  
## <a name="remarks"></a>Notes  
 Si *nom* est spécifié, **sp_helpdevice** affiche des informations sur l’unité de vidage spécifiée. Si *nom* n’est pas spécifié, **sp_helpdevice** affiche des informations sur toutes les unités de vidage dans le **sys.backup_devices** vue de catalogue.  
  
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
 [Procédures stockées du moteur de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
