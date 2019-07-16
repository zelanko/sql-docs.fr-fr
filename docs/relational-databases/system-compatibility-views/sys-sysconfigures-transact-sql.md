---
title: Sys.sysconfigures (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysconfigures
- sysconfigures
- sys.sysconfigures_TSQL
- sysconfigures_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysconfigures compatibility view
- sysconfigures system table
ms.assetid: 146bf10a-c898-4676-a2a1-673fb1cee7a2
author: rothja
ms.author: jroth
ms.openlocfilehash: c785ee1c4d3c5382aa42adf48ad9880f00297137
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68089201"
---
# <a name="syssysconfigures-transact-sql"></a>sys.sysconfigures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque option de configuration définie par un utilisateur. **sysconfigures** contient les options de configuration définies avant le dernier démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ainsi que des options de configuration dynamiques définies depuis.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**value**|**int**|Valeur modifiable par l'utilisateur pour la variable. Utilisée par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] uniquement en cas d'exécution de RECONFIGURE.|  
|**config**|**int**|Numéro de variable de configuration.|  
|**comment**|**nvarchar(255)**|Explication de l'option de configuration.|  
|**status**|**smallint**|Bitmap qui indique l’état de l’option. Il peut prendre les valeurs suivantes :<br /><br /> 0 = Statique. Le paramètre prend effet au redémarrage du serveur.<br /><br /> 1 = Dynamique. La variable prend effet lorsque l'instruction RECONFIGURE est exécutée.<br /><br /> 2 = Avancé. Variable s’affiche uniquement lorsque le **afficher les options avancées** est définie. Le paramètre prend effet au redémarrage du serveur.<br /><br /> 3 = Dynamique et avancé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système avec les vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
