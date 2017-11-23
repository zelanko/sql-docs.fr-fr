---
title: Sys.parameter_type_usages (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.parameter_type_usages
- sys.parameter_type_usages_TSQL
- parameter_type_usages_TSQL
- parameter_type_usages
dev_langs: TSQL
helpviewer_keywords: sys.parameter_type_usages catalog view
ms.assetid: af0e167b-bffb-4525-84ec-3607f9268d3d
caps.latest.revision: "24"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e477f00a9f80159daa74bb3199c8629f52322b9b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sysparametertypeusages-transact-sql"></a>sys.parameter_type_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne par paramètre de type défini par l'utilisateur (personnalisé).  
  
> [!NOTE]  
>  Cette vue ne retourne pas les paramètres des procédures numérotées.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID de l’objet auquel appartient ce paramètre.|  
|**parameter_id**|**int**|ID du paramètre. Unique dans l'objet.|  
|**user_type_id**|**int**|Identificateur de type de données défini par l'utilisateur.<br /><br /> Pour retourner le nom du type, joindre à la [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) affichage sur cette colonne catalogue.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** . Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40; de Types scalaires Transact-SQL &#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
