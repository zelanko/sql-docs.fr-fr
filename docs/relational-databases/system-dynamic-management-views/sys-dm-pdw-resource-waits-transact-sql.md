---
title: Sys.dm_pdw_resource_waits (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a43ce9a2-5261-41e3-97f0-555ba05ebed9
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 9be76f5f308213f905224de5ade9b604ec119c30
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52514650"
---
# <a name="sysdmpdwresourcewaits-transact-sql"></a>Sys.dm_pdw_resource_waits (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Affiche les informations pour tous les types de ressources dans attente [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|Position de la demande dans la liste d’attente.|ordinal à partir de 0. Cela n’est pas unique sur toutes les entrées de l’attente.|  
|session_id|**nvarchar(32)**|ID de la session dans laquelle l’état d’attente s’est produite.|Consultez session_id dans [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|Type|**nvarchar(255)**|Type d’attente que représente cette entrée.|Valeurs possibles :<br /><br /> Connexion<br /><br /> Concurrence des requêtes locales<br /><br /> Concurrence des requêtes distribuées<br /><br /> Accès concurrentiel DMS<br /><br /> Accès concurrentiel de sauvegarde|  
|object_type|**nvarchar(255)**|Type d’objet qui est affectée par l’attente.|Valeurs possibles :<br /><br /> **OBJECT**<br /><br /> **DATABASE**<br /><br /> **SYSTEM**<br /><br /> **SCHEMA**<br /><br /> **APPLICATION**|  
|object_name|**nvarchar(386)**|Nom ou GUID de l’objet spécifié qui a été affectée par l’attente.|Tables et les vues sont affichées avec des noms en trois parties.<br /><br /> Index et les statistiques sont affichées avec des noms en quatre parties.<br /><br /> Les noms, les principaux et les bases de données sont des noms de chaîne.|  
|request_id|**nvarchar(32)**|ID de la demande sur lequel l’état d’attente s’est produite.|Identificateur QID de la demande.<br /><br /> Identificateur GUID pour les demandes de charge.|  
|request_time|**datetime**|Heure à laquelle le verrou ou la ressource a été demandée.||  
|acquire_time|**datetime**|Heure à laquelle a été acquis le verrou ou une ressource.||  
|state|**nvarchar(50)**|État de l’état d’attente.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**Int**|Priorité de l’élément en attente.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|concurrency_slots_used|**Int**|Nombre d’emplacements de concurrence (32 max) réservé pour cette demande.|1 - pour SmallRC<br /><br /> 3 - pour MediumRC<br /><br /> 7 pour LargeRC<br /><br /> 22 - pour XLargeRC|  
|resource_class|**nvarchar(20)**|La classe de ressources pour cette demande.|SmallRC<br /><br /> MediumRC<br /><br /> LargeRC<br /><br /> XLargeRC|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
