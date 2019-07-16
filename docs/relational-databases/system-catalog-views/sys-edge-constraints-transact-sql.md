---
title: Sys.edge_constraints (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.edge_constraints
- edge_constraints
- SQL Graph
- edge_constraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.edge_constraints catalog view
ms.assetid: 0f782d2f-7126-46ab-85b7-bcba44862231
author: shkale-msft
ms.author: shkale
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5dc2e47c49dc9d639489426fceab0b848c9def3e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68079326"
---
# <a name="sysedgeconstraints-transact-sql"></a>Sys.edge_constraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Contient une ligne pour chaque objet qui est une contrainte d’arête. 
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**\<Colonnes héritent de sys.objects >**||Pour obtenir la liste des colonnes qui hérite de cette vue, consultez [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**is_disabled**|**bit**|1 = edge contrainte est désactivée.<br /><br /> 0 = edge contrainte est activée.|  
|**is_not_trusted**|**bit**|1 = edge contrainte n’a pas été vérifiée par le système.<br /><br /> 0 = edge contrainte a été vérifiée par le système.|  
|**delete_referential_action**|**tinyint**|Action référentielle qui a été définie sur cette contrainte d’arête.<br /><br />0 = Aucune Action.|  
|**delete_referential_action_desc**|**nvarchar(60)**|Description de l’action référentielle qui a été définie sur cette contrainte d’arête.<br /><br />NO_ACTION|  
|**is_system_named**|**bit**|1 = edge nom de la contrainte a été généré par le système.<br /><br />0 = edge nom de la contrainte a été fourni par l’utilisateur.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Questions fréquentes (FAQ) sur l’interrogation des catalogues système SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
