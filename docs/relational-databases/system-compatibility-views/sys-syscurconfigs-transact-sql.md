---
title: Sys.syscurconfigs (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.syscurconfigs
- sys.syscurconfigs_TSQL
- syscurconfigs
- syscurconfigs_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.syscurconfigs compatibility view
- syscurconfigs system table
ms.assetid: 454ab849-07a5-4b50-ba0a-6b1b14721f77
caps.latest.revision: "34"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ced0f1fa5237ecef93d61ea2049245f33bcca3cc
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="syssyscurconfigs-transact-sql"></a>sys.syscurconfigs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une entrée pour chaque option de configuration courante. De plus, cette vue contient quatre entrées décrivant la structure de la configuration. **syscurconfigs** se construit dynamiquement lorsqu’un utilisateur. Pour plus d’informations, consultez [sys.sysconfigures &#40; Transact-SQL &#41; ](../../relational-databases/system-compatibility-views/sys-sysconfigures-transact-sql.md).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**valeur**|**int**|Valeur modifiable par l'utilisateur pour la variable. Utilisée par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uniquement en cas d'exécution de RECONFIGURE.|  
|**configuration**|**smallint**|Numéro de variable de configuration.|  
|**commentaire**|**nvarchar(255)**|Explication de l'option de configuration.|  
|**status**|**smallint**|Bitmap indiquant l'état de l'option. Il peut prendre les valeurs suivantes :<br /><br /> 0 = Statique. Le paramètre prend effet au redémarrage du serveur.<br /><br /> 1 = Dynamique. La variable prend effet lorsque l'instruction RECONFIGURE est exécutée.<br /><br /> 2 = Avancé. Variable s’affiche uniquement lorsque le **show advanced options** est définie.<br /><br /> 3 = Dynamique et avancé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système pour les vues système &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
