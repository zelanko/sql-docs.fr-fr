---
title: sys.workload_management_workload_classifier_details (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/01/2019
ms.prod: sql
ms.technology: system-objects
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: d5494cb7e8fc49e9aa6e8335d0c65e6415375a1a
ms.sourcegitcommit: 0a4879dad09c6c42ad1ff717e4512cfea46820e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67413096"
---
# <a name="sysworkloadmanagementworkloadclassifierdetails-transact-sql"></a>sys.workload_management_workload_classifier_details (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  Retourne les détails pour chaque classifieur.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**Int**|ID du classifieur. Joignable à [sys.workload_management_workload_classifiers](sys-workload-management-workload-classifiers-transact-sql.md). N'accepte pas la valeur NULL.|
|classifier_type|**sysname**|L’entité sur laquelle la classification est effectuée. N'accepte pas la valeur NULL.|NOM DE MEMBRE|
|classifier_value|**sysname**|La valeur du classifieur. N'accepte pas la valeur NULL.||

## <a name="permissions"></a>Autorisations

Requiert l'autorisation VIEW SERVER STATE.

## <a name="next-steps"></a>Étapes suivantes
  
 Pour obtenir la liste de toutes les vues de catalogue pour SQL Data Warehouse et Parallel Data Warehouse, consultez [SQL Data Warehouse et les vues du catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md). Pour créer un classifieur de charge de travail, consultez [créer un classifieur de charge de travail](../../t-sql/statements/create-workload-classifier-transact-sql.md). Pour plus d’informations sur la classification de la charge de travail, consultez SQL Data Warehouse [Classification de la charge de travail](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification) et [Importance de la charge de travail](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
