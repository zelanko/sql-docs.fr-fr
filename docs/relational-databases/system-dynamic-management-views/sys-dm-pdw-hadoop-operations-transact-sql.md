---
description: sys. dm_pdw_hadoop_operations (Transact-SQL)
title: sys. dm_pdw_hadoop_operations (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5d2337d4-e2c7-48de-9c26-cdc7e6eb5d55
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 6665a23aa3b3a30aee3c80cfbd8ed139d6784d3e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481859"
---
# <a name="sysdm_pdw_hadoop_operations-transact-sql"></a>sys. dm_pdw_hadoop_operations (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Contient une ligne pour chaque travail Map-Reduce qui est envoyé vers Hadoop dans le cadre de l’exécution d’une [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] requête sur une table Hadoop externe. Chaque travail Map-Reduce représente l’un des prédicats de la requête. Cette option est utilisée uniquement lorsque la poussée de prédicat est activée pour les requêtes sur les tables externes Hadoop.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|ID de cette opération Hadoop externe.|Identique à ID dans [sys. dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Index de l’étape de la requête qui fait référence à cette opération Hadoop.|Identique à step_index dans [sys. dm_pdw_request_steps &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|operation_type|**nvarchar(255)**|Décrit le type d’opération externe.|'Opération Hadoop externe'|  
|operation_name|**nvarchar(4000)**|ID de tâche d’un travail Map-Reduce. Elle est retournée par Hadoop après [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] l’envoi du travail.||  
|map_progress|**float**|Pourcentage de données d’entrée consommées jusqu’à présent par le travail de mappage.|Nombre à virgule flottante entre et incluant, 0 et 100.|  
|reduce_progress|**int**|Pourcentage du travail de réduction terminé.|Nombre à virgule flottante entre et incluant, 0 et 100.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues système &#40;&#41;Transact-SQL ](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
