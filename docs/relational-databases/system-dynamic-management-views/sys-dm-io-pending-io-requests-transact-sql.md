---
title: Sys.dm_io_pending_io_requests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_io_pending_io_requests
- dm_io_pending_io_requests
- dm_io_pending_io_requests_TSQL
- sys.dm_io_pending_io_requests_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_io_pending_io_requests dynamic management view
ms.assetid: d1fb46dd-5c74-4c04-9ecf-8934b1bedb5b
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 71fb4daabcdb0eef03e615f595df20d555673a24
ms.sourcegitcommit: 467b2c708651a3a2be2c45e36d0006a5bbe87b79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53980205"
---
# <a name="sysdmiopendingiorequests-transact-sql"></a>sys.dm_io_pending_io_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne une ligne pour chaque requête d'entrée/sortie en attente dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  À appeler à partir [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_io_pending_io_requests**.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**io_completion_request_address**|**varbinary(8)**|Adresse mémoire de la requête d'entrée/sortie. N'accepte pas la valeur NULL.|  
|**io_type**|**nvarchar(60)**|Type de requête d'entrée/sortie en attente. N'accepte pas la valeur NULL.|  
|**io_pending_ms_ticks**|**bigint**|À usage interne uniquement N'accepte pas la valeur NULL.| 
|**io_pending**|**Int**|Indique si la requête d'entrée/sortie est en attente ou a été effectuée par Windows. Une requête d'entrée/sortie peut toujours être en attente même si Windows l'a effectuée mais que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'a pas encore effectué un changement de contexte dans lequel il doit traiter la requête d'entrée/sortie et la supprimer de la liste. N'accepte pas la valeur NULL.|  
|**io_completion_routine_address**|**varbinary(8)**|Fonction interne à appeler lorsque la requête d'entrée/sortie est terminée. Autorise la valeur NULL.|  
|**io_user_data_address**|**varbinary(8)**|À usage interne uniquement Autorise la valeur NULL.|  
|**scheduler_address**|**varbinary(8)**|Planificateur sur lequel a été émis la requête d'entrée/sortie. Cette requête s'affiche dans la liste des entrées/sorties en attente du planificateur. Pour plus d’informations, consultez [sys.dm_os_schedulers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md). N'accepte pas la valeur NULL.|  
|**io_handle**|**varbinary(8)**|Descripteur du fichier utilisé dans la requête d'entrée/sortie. Autorise la valeur NULL.|  
|**io_offset**|**bigint**|Déplacement de la requête d'entrée/sortie. N'accepte pas la valeur NULL.|  
|**io_handle_path**|**nvarchar (256)**| Chemin d’accès du fichier qui est utilisé dans la demande d’e/s. Autorise la valeur NULL.|
|**pdw_node_id**|**Int**|**S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L’identificateur pour le nœud se trouvant sur cette distribution.|  
  
## <a name="permissions"></a>Autorisations  

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.   
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [E/S des fonctions et vues de gestion dynamique liées &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


