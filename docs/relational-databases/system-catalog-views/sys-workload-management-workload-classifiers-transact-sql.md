---
title: sys.workload_management_workload_classifiers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/08/2019
ms.prod: ''
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: d93876db1bb31edab2ad128a0ab8af4d4a5230cd
ms.sourcegitcommit: aa8bec762be29a29aed651d98ed4d868da85ba67
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57975367"
---
# <a name="sysworkloadmanagementworkloadclassifiers-transact-sql-preview"></a>sys.workload_management_workload_classifiers (Transact-SQL) (Preview)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

 Renvoie les détails de classifieurs de charge de travail.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**Int**|ID unique du classifieur. N'accepte pas la valeur NULL||
group_name|**sysname**|Nom du groupe de charge de travail le classifieur est assigné à. N'accepte pas la valeur NULL. |Classes de ressources statiques</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80 </br>Classes de ressources dynamiques</br>smallrc</br>mediumrc</br>Largerc</br>xlargerc|
NAME|**sysname**|Nom du classifieur. Doit être unique à l’instance. N'accepte pas la valeur NULL.||
|importance|**sysname**|Est l’importance relative d’une demande dans ce groupe de charge de travail et les groupes de charges de travail pour les ressources partagées.  Importance spécifiée dans le classifieur remplace le paramètre d’importance de groupe de charge de travail.|low, below_normal, normal, above_normal, high |
|create_time|**datetime**|Heure de que création de classifieur. N'accepte pas la valeur NULL.||
modify_time|**datetime**|Heure de que dernière modification du classifieur. N'accepte pas la valeur NULL.||
is_enabled|**bit**|Indique si le classifieur est activé ou non. Est activé par défaut. N'accepte pas la valeur NULL.|0 = le classifieur n’est pas activé. </br> 1 = le classifieur est activé|
|&nbsp;||||
  
## <a name="permissions"></a>Autorisations

Requiert l'autorisation VIEW SERVER STATE.

## <a name="next-steps"></a>Étapes suivantes

 Pour obtenir la liste de toutes les vues de catalogue pour SQL Data Warehouse et Parallel Data Warehouse, consultez [SQL Data Warehouse et les vues du catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md). Pour créer un classifieur de charge de travail, consultez [créer un classifieur de charge de travail](../../t-sql/statements/create-workload-classifier-transact-sql.md). Pour plus d’informations sur la classification de la charge de travail, consultez [SQL la Classification des charges de travail entrepôt de données](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
