---
title: Sys.dm_os_child_instances (Transact-SQL) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 71fc55f996a58fc8ed353405fa9e5fdc9ad845f0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47751087"
---
# <a name="sysdmoschildinstances-transact-sql"></a>sys.dm_os_child_instances (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque instance utilisateur qui a été créée à partir de l'instance de serveur parente.  
  
> **IMPORTANT !** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Les informations retournées par **sys.dm_os_child_instances** peut être utilisé pour déterminer l’état de chaque Instance de l’utilisateur (heart_beat) et pour obtenir le nom du canal (instance_pipe_name) qui peut être utilisé pour créer une connexion à l’utilisateur À l’aide de l’instance [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou SQLCmd. Vous pouvez vous connecter à une instance utilisateur uniquement lorsque cette dernière a été démarrée par un processus externe, tel qu'une application cliente. Les outils de gestion de SQL Server ne peuvent pas démarrer une instance utilisateur.  
  
> **Remarque :** les Instances utilisateur sont une fonctionnalité de [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] uniquement.  
  
> **Remarque** à appeler à partir [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_os_child_instances**.  
  
|colonne|Data type|Description|  
|------------|---------------|-----------------|  
|**owning_principal_name**|**nvarchar (256)**|Nom de l'utilisateur pour lequel cette instance utilisateur a été créée.|  
|owning_principal_sid|nvarchar (256)|SID (Security-Identifier) du principal propriétaire de cette instance utilisateur. Elle correspond au SID Windows.|  
|owning_principal_sid_binary|varbinary(85)|Version binaire du SID de l'utilisateur propriétaire de l'instance utilisateur.|  
|**instance_name**|**nvarchar(128)**|Nom de cette instance utilisateur.|  
|**instance_pipe_name**|**nvarchar(260)**|Lors de la création d'une instance utilisateur, un canal nommé est créé auquel les applications peuvent se connecter. Ce nom peut s'utiliser dans une chaîne de connexion pour se connecter à cette instance utilisateur.|  
|**os_process_id**|**Int**|Numéro du processus Windows pour cette instance utilisateur.|  
|**os_process_creation_date**|**DateTime**|Date et heure du dernier démarrage du processus de cette instance utilisateur.|  
|**heart_beat**|**nvarchar(5)**|État actuel de cette instance utilisateur ; ALIVE ou DEAD.|  
|**pdw_node_id**|**Int**|**S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L’identificateur pour le nœud se trouvant sur cette distribution.|  
  
## <a name="permissions"></a>Permissions  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la vue de gestion dynamique, consultez [fonctions et vues de gestion dynamique &#40;Transact-SQL&#41; ](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Instances d’utilisateur pour les non-administrateurs](http://msdn.microsoft.com/en-us/85385aae-10fb-4f8b-9eeb-cce2ee7da019)  
  
  



