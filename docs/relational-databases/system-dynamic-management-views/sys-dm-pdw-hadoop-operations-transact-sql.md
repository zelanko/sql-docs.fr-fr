---
title: Sys.dm_pdw_hadoop_operations (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.component: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5d2337d4-e2c7-48de-9c26-cdc7e6eb5d55
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: f158ac7c5904e54daf384ddbf8196dbf8fd5f66f
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36925970"
---
# <a name="sysdmpdwhadoopoperations-transact-sql"></a>Sys.dm_pdw_hadoop_operations (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient une ligne pour chaque tâche Map/reduce qui a été repoussée à Hadoop dans le cadre de l’exécution un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] requête sur une table Hadoop externe. Chaque tâche Map/reduce représente un des prédicats de la requête. Cela est utilisé uniquement lors de l’activation du prédicat est activée pour les requêtes sur les tables externes Hadoop.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|ID pour cette opération Hadoop externe.|Même en tant qu’ID dans [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**Int**|Index de l’étape de requête qui fait référence à cette opération Hadoop.|Identique à step_index dans [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|operation_type|**nvarchar(255)**|Décrit le type d’opération externe.|'Opération Hadoop externe'|  
|nom_opération|**nvarchar(4000)**|L’ID de travail pour un travail MapReduce. Celui-ci est renvoyé par Hadoop après [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] soumet le travail.||  
|map_progress|**float**|Le pourcentage de données d’entrée qui a été utilisées jusqu’ici par le travail de la carte.|Nombre à virgule flottante compris entre et y compris 0 et 100.|  
|reduce_progress|**Int**|Le pourcentage de la tâche de réduction est terminée...|Nombre à virgule flottante compris entre et y compris 0 et 100.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues système &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
