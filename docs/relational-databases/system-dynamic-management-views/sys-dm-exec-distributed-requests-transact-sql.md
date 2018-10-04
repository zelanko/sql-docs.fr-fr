---
title: Sys.dm_exec_distributed_requests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_DISTRIBUTED_REQUESTS
- DM_EXEC_DISTRIBUTED_REQUESTS_TSQL
- SYS.DM_EXEC_DISTRIBUTED_REQUESTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- sys.dm_exec_distributed_sql_requests management view
- PolyBase
- dm_exec_distributed_sql_requests management view
ms.assetid: c041d416-d8c6-435e-a563-6a310abd33e3
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 87fa42aa2603a3a25e5a53ca5abb3a140299dd6c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47743237"
---
# <a name="sysdmexecdistributedrequests-transact-sql"></a>Sys.dm_exec_distributed_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Contient des informations sur toutes les demandes actuellement ou récemment active dans les requêtes PolyBase. Elle répertorie une ligne par/requête de la demande.  
  
 Basé sur session et demande l’ID, un utilisateur peut ensuite récupérer les requêtes distribuées réels générées de façon à être exécutée : via sys.dm_exec_distributed_requests. Par exemple, une requête impliquant SQL normales et les tables SQL externes sera être décomposée en différentes instructions/requêtes exécutées sur les différents nœuds de calcul. Pour suivre les étapes distribuées sur tous les nœuds de calcul, nous présentons un ID d’exécution 'global' qui peut être utilisé pour effectuer le suivi de toutes les opérations sur les nœuds de calcul associés à une requête particulière et l’opérateur, respectivement.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|sql_handle|**varbinary(64)**|Clé pour cette vue. Id numérique unique associé à la demande.|Unique pour toutes les requêtes dans le système.|  
|execution_id|**nvarchar(32**|Id numérique unique associé à la session dans laquelle cette requête a été exécutée.||  
|status|**nvarchar(32**|État actuel de la demande.|« En attente » 'Autoriser', 'AcquireSystemResources', 'Initialisation', 'Plan », « Analyse », « AquireResources », « Running », « Annulation », « Complète », « échec », « Annulé ».|  
|error_id|**nvarchar(36)**|Id unique de l’erreur associée à la demande, le cas échéant.|La valeur NULL si aucune erreur ne s’est produite.|  
|start_time|**datetime**|Heure de début de l’exécution de la demande.|0 pour les demandes en file d’attente ; Sinon, valide date/heure inférieure ou égale à l’heure actuelle.|  
|end_time|**datetime**|Heure à laquelle le moteur a terminé la compilation de la demande.|NULL pour les demandes en file d’attente ou actives ; Sinon, une valeur datetime valide inférieure ou égale à l’heure actuelle.|  
|total_elapsed_time|**Int**|Temps écoulé dans l’exécution dans la mesure où la demande a été démarrée, en millisecondes.|Comprise entre 0 et la différence entre start_time et end_time. Si total_elapsed_time dépasse la valeur maximale d’un entier, total_elapsed_time continueront à être la valeur maximale. Cette condition génère l’avertissement « la valeur maximale a été dépassée. » La valeur maximale en millisecondes est équivalente à 24,8 jours environ.|  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes avec les vues de gestion dynamique de PolyBase](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vues de gestion dynamique liées à la base de données &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
