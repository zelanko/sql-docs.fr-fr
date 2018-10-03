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
manager: craigg
ms.openlocfilehash: 61936891ecd31b3bf5421a8cac49aad9f0dd37f7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47635317"
---
# <a name="syssysconfigures-transact-sql"></a>sys.sysconfigures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque option de configuration définie par un utilisateur. **sysconfigures** contient les options de configuration définies avant le dernier démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ainsi que des options de configuration dynamiques définies depuis.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**value**|**Int**|Valeur modifiable par l'utilisateur pour la variable. Utilisée par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] uniquement en cas d'exécution de RECONFIGURE.|  
|**config**|**Int**|Numéro de variable de configuration.|  
|**Commentaire**|**nvarchar(255)**|Explication de l'option de configuration.|  
|**status**|**smallint**|Bitmap qui indique l’état de l’option. Il peut prendre les valeurs suivantes :<br /><br /> 0 = Statique. Le paramètre prend effet au redémarrage du serveur.<br /><br /> 1 = Dynamique. La variable prend effet lorsque l'instruction RECONFIGURE est exécutée.<br /><br /> 2 = Avancé. Variable s’affiche uniquement lorsque le **afficher les options avancées** est définie. Le paramètre prend effet au redémarrage du serveur.<br /><br /> 3 = Dynamique et avancé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système avec les vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
