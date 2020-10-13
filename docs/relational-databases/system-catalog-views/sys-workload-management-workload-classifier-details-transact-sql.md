---
description: sys.workload_management_workload_classifier_details (Transact-SQL)
title: sys.workload_management_workload_classifier_details (Transact-SQL) | Microsoft Docs
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
ms.openlocfilehash: 2135b567509ef9df5f3c8df7a317a9ea45b92ec7
ms.sourcegitcommit: a5398f107599102af7c8cda815d8e5e9a367ce7e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92006416"
---
# <a name="sysworkload_management_workload_classifier_details-transact-sql"></a>sys.workload_management_workload_classifier_details (Transact-SQL)

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

  Retourne les détails de chaque classifieur.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|ID du classifieur.  N'accepte pas la valeur NULL.|
|classifier_type|**sysname**|Joignable à [sys.workload_management_workload_classifiers](sys-workload-management-workload-classifiers-transact-sql.md).|`membername`</br>`wlm_label`</br>`wlm_context`</br>`start_time`</br>`end_time`|
|classifier_value|**sysname**|Valeur du classifieur. N'accepte pas la valeur NULL.||

## <a name="permissions"></a>Autorisations

Requiert l'autorisation VIEW SERVER STATE.

## <a name="next-steps"></a>Étapes suivantes
  
Pour obtenir la liste de tous les affichages catalogue pour Azure Synapse Analytics et les Data Warehouse parallèles, consultez [SQL Data Warehouse et les affichages catalogue Data Warehouse parallèles](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md). Pour créer un classifieur de charge de travail, consultez [créer un classifieur de charge de travail](../../t-sql/statements/create-workload-classifier-transact-sql.md). Pour plus d’informations sur la classification de la charge de travail, consultez [classification](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification) des charges de travail Azure Synapse Analytics et [importance des charges de travail](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
