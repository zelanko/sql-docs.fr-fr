---
title: sys.dm_os_loaded_modules (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_loaded_modules
- dm_os_loaded_modules
- sys.dm_os_loaded_modules_TSQL
- dm_os_loaded_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_loaded_modules dynamic management view
ms.assetid: 56c7743a-b568-4943-bd3b-73c57d9d641c
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9e33e71c94cffe6b455be1b5a5fc0e22732e60f0
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmosloadedmodules-transact-sql"></a>sys.dm_os_loaded_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque module chargé dans l'espace d'adressage du serveur.  
  
> [!NOTE]  
>  Pour appeler cette de [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_os_loaded_modules**.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**base_address**|**varbinary(8)**|Adresse du module dans le processus.|  
|**file_version**|**varchar(23)**|Version du fichier. Apparaît sous le format suivant :<br /><br /> x.x:x.x|  
|**product_version**|**varchar(23)**|Version du produit. Apparaît sous le format suivant :<br /><br /> x.x:x.x|  
|**debug**|**bit**|1 = le module est une version de débogage du module chargé.|  
|**patched**|**bit**|1 = le module a été corrigé.|  
|**prerelease**|**bit**|1 = le module est une version préliminaire du module chargé.|  
|**private_build**|**bit**|1 = le module est une version privée du module chargé.|  
|**special_build**|**bit**|1 = le module est une version spéciale du module chargé.|  
|**language**|**int**|Langue des informations de version du module.|  
|**company**|**nvarchar (256)**|Nom de la société qui a créé le module.|  
|**description**|**nvarchar (256)**|Description du module.|  
|**nom**|**nvarchar(255)**|Nom du module. Inclut le chemin d'accès complet du module.|  
|**pdw_node_id**|**int**|**S’applique à**: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L’identificateur du nœud qui se trouve sur cette distribution.|  
  
## <a name="permissions"></a>Autorisations  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Système d’exploitation de serveur SQL relatives des vues de gestion dynamique &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
