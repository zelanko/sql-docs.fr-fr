---
title: sys. pdw_loader_run_stages (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 255681e9-323c-42c0-a63c-1f05536efdd5
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5d10a3bcbf02e88e054c12060299e9462af3004d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68127454"
---
# <a name="syspdw_loader_run_stages-transact-sql"></a>sys. pdw_loader_run_stages (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contient des informations sur les opérations de chargement en [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]cours et terminées dans. Ces informations sont conservées après le redémarrage du système.  
  
|||||  
|-|-|-|-|  
|Nom de la colonne|Type de données|Description|Plage|  
|run_id|**int**|Identificateur unique d’une exécution de chargeur.||  
|étape|**nvarchar(30**|Étape actuelle pour l’exécution.|'CREATE_STAGING', 'DMS_LOAD', 'LOAD_INSERT', 'LOAD_CLEANUP'|  
|request_id|**nvarchar (32)**|ID de la demande exécutant cette étape.||  
|status|**nvarchar (16)**|État de cette phase.||  
|start_time|**DATETIME**|Heure à laquelle l’étape a été démarrée.||  
|end_time|**DATETIME**|Heure de fin de l’étape, le cas échéant.|NULL s’il n’est pas démarré ou en cours.|  
|total_elapsed_time|**int**|Durée totale d’exécution de cette étape (ou passée jusqu’à présent).|Si total_elapsed_time dépasse la valeur maximale d’un entier (24,8 jours en millisecondes), cela entraînera un échec de matérialisation en raison d’un dépassement de capacité.<br /><br /> La valeur maximale en millisecondes est équivalente à 24,8 jours.|  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue de la SQL Data Warehouse et des Data Warehouse parallèles](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
