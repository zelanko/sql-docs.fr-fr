---
title: Sys.extended_procedures (Transact-SQL) | Documents Microsoft
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
- extended_procedures
- sys.extended_procedures
- sys.extended_procedures_TSQL
- extended_procedures_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.extended_procedures catalog view
ms.assetid: 310e0f87-0044-4fdf-bd12-51a723a74ce6
caps.latest.revision: "33"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8f444616226ead7ecf159d3361af0845d80fd2b4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sysextendedprocedures-transact-sql"></a>sys.extended_procedures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque objet qui est une procédure stockée étendue, avec **sys.objects.type** = X. Étant donné que les procédures stockées étendues sont installés dans le **master** base de données, ils sont visibles uniquement à partir de ce contexte de base de données. Sélection de la **sys.extended_procedures** affichage dans un autre contexte de base de données renvoie un jeu de résultats vide.  

  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**\<Colonnes héritent de sys.objects >**||Pour obtenir la liste des colonnes qui hérite de cette vue, consultez [sys.objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**nom_dll**|**nvarchar (260)**|Nom (chemin d'accès compris) de la DLL pour cette procédure stockée étendue.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue d’objets &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
