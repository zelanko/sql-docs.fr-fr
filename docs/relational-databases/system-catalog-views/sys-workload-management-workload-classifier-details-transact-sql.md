---
description: sys. workload_management_workload_classifier_details (Transact-SQL)
title: sys. workload_management_workload_classifier_details (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/05/2019
ms.prod: sql
ms.technology: system-objects
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: daf46109b627f9ccfec8522cd61bd5df9bac5c3e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419923"
---
# <a name="sysworkload_management_workload_classifier_details-transact-sql"></a>sys. workload_management_workload_classifier_details (Transact-SQL)

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

  Retourne les détails de chaque classifieur.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|ID du classifieur.  N'accepte pas la valeur NULL.|
|classifier_type|**sysname**|Joignable à [sys. workload_management_workload_classifiers](sys-workload-management-workload-classifiers-transact-sql.md).|`membername`</br>`wlm_label`</br>`wlm_context`</br>`start_time`</br>`end_time`|
|classifier_value|**sysname**|Valeur du classifieur. N'accepte pas la valeur NULL.||

## <a name="permissions"></a>Autorisations

Requiert l'autorisation VIEW SERVER STATE.

## <a name="next-steps"></a>Étapes suivantes
  
Pour obtenir la liste de tous les affichages catalogue pour SQL Data Warehouse et les Data Warehouse parallèles, consultez [SQL Data Warehouse et les affichages catalogue de Data Warehouse parallèles](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md). Pour créer un classifieur de charge de travail, consultez [créer un classifieur de charge de travail](../../t-sql/statements/create-workload-classifier-transact-sql.md). Pour plus d’informations sur la classification des charges de travail, consultez SQL Data Warehouse [classification des charges](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification) de travail et importance de la [charge de travail](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
