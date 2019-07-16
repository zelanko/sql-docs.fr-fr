---
title: sys.syscurconfigs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.syscurconfigs
- sys.syscurconfigs_TSQL
- syscurconfigs
- syscurconfigs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.syscurconfigs compatibility view
- syscurconfigs system table
ms.assetid: 454ab849-07a5-4b50-ba0a-6b1b14721f77
author: rothja
ms.author: jroth
ms.openlocfilehash: 1b0fad344831d8073badb2618eb2c34a1cdc2161
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68089181"
---
# <a name="syssyscurconfigs-transact-sql"></a>sys.syscurconfigs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une entrée pour chaque option de configuration courante. De plus, cette vue contient quatre entrées décrivant la structure de la configuration. **syscurconfigs** se construit dynamiquement lorsqu’un utilisateur. Pour plus d’informations, consultez [sys.sysconfigures &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysconfigures-transact-sql.md).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**value**|**int**|Valeur modifiable par l'utilisateur pour la variable. Utilisée par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uniquement en cas d'exécution de RECONFIGURE.|  
|**config**|**smallint**|Numéro de variable de configuration.|  
|**comment**|**nvarchar(255)**|Explication de l'option de configuration.|  
|**status**|**smallint**|Bitmap indiquant l'état de l'option. Il peut prendre les valeurs suivantes :<br /><br /> 0 = Statique. Le paramètre prend effet au redémarrage du serveur.<br /><br /> 1 = Dynamique. La variable prend effet lorsque l'instruction RECONFIGURE est exécutée.<br /><br /> 2 = Avancé. Variable s’affiche uniquement lorsque le **afficher les options avancées** est définie.<br /><br /> 3 = Dynamique et avancé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système avec les vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
