---
title: sys.workload_management_workload_classifier_details (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2019
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
ms.openlocfilehash: 9afd00a887244c02849d40eed635500b06533709
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582722"
---
# <a name="sysworkloadmanagementworkloadclassifierdetails-transact-sql-preview"></a>sys.workload_management_workload_classifier_details (Transact-SQL) (Preview)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

> [!Note]
> Classification de la charge de travail est disponible en version préliminaire sur SQL Data Warehouse Gen2. Aperçu de Classification de gestion de la charge de travail et l’Importance est pour les builds avec une date de publication de 9 avril 2019 ou version ultérieure.  Les utilisateurs Évitez d’utiliser les builds antérieures à cette date pour le test de charge de travail administration.  Pour déterminer si votre build est la gestion de la charge de travail capable, exécutez select @@version lorsque connecté à votre instance SQL Data Warehouse.

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
