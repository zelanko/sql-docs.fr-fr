---
title: sys. dm_os_child_instances (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_child_instances
- sys.dm_os_child_instances_TSQL
- dm_os_child_instances
- dm_os_child_instances_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server state information [SQL Server]
- sys.dm_os_child_instances dynamic management view
- monitoring server health
ms.assetid: 1bef3074-0ccc-48fa-8f3d-14f3d99df86b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 59a58348f5428f568f40d28b4e83bc6bc040647c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67900234"
---
# <a name="sysdm_os_child_instances-transact-sql"></a>sys.dm_os_child_instances (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque instance utilisateur qui a été créée à partir de l'instance de serveur parente.  
  
> **IMPORTANT !** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Les informations retournées par **sys. dm_os_child_instances** peuvent être utilisées pour déterminer l’état de chaque instance utilisateur (heart_beat) et pour obtenir le nom du canal (instance_pipe_name) qui peut être utilisé pour créer une connexion à l' [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] instance utilisateur à l’aide de ou de sqlcmd. Vous pouvez vous connecter à une instance utilisateur uniquement lorsque cette dernière a été démarrée par un processus externe, tel qu'une application cliente. Les outils de gestion de SQL Server ne peuvent pas démarrer une instance utilisateur.  
  
> **Remarque :** Les instances utilisateur sont une fonctionnalité [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] de uniquement.  
> 
> **Remarque** Pour appeler cette valeur [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] à [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]partir de ou, utilisez le nom **sys. dm_pdw_nodes_os_child_instances**.  
  
|Colonne|Type de données|Description|  
|------------|---------------|-----------------|  
|**owning_principal_name**|**nvarchar(256)**|Nom de l'utilisateur pour lequel cette instance utilisateur a été créée.|  
|owning_principal_sid|nvarchar(256)|SID (Security-Identifier) du principal propriétaire de cette instance utilisateur. Elle correspond au SID Windows.|  
|owning_principal_sid_binary|varbinary(85)|Version binaire du SID de l'utilisateur propriétaire de l'instance utilisateur.|  
|**instance_name**|**nvarchar(128)**|Nom de cette instance utilisateur.|  
|**instance_pipe_name**|**nvarchar(260)**|Lors de la création d'une instance utilisateur, un canal nommé est créé auquel les applications peuvent se connecter. Ce nom peut s'utiliser dans une chaîne de connexion pour se connecter à cette instance utilisateur.|  
|**os_process_id**|**Int**|Numéro du processus Windows pour cette instance utilisateur.|  
|**os_process_creation_date**|**Date/heure**|Date et heure du dernier démarrage du processus de cette instance utilisateur.|  
|**heart_beat**|**nvarchar(5**|État actuel de cette instance utilisateur ; ALIVE ou DEAD.|  
|**pdw_node_id**|**int**|**S’applique à**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificateur du nœud sur lequel cette distribution se trouve.|  
  
## <a name="permissions"></a>Autorisations  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la vue de gestion dynamique, consultez [fonctions et vues de gestion dynamique &#40;&#41;Transact-SQL](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Instances d'utilisateur pour les non administrateurs](https://msdn.microsoft.com/85385aae-10fb-4f8b-9eeb-cce2ee7da019)  
  
  



