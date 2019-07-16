---
title: sys.dm_os_loaded_modules (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: f43e03e482bb7125100ed7bed56337fb75a2e711
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900087"
---
# <a name="sysdmosloadedmodules-transact-sql"></a>sys.dm_os_loaded_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque module chargé dans l'espace d'adressage du serveur.  
  
> [!NOTE]  
>  À appeler à partir [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_os_loaded_modules**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**base_address**|**varbinary(8)**|Adresse du module dans le processus.|  
|**file_version**|**varchar(23)**|Version du fichier. Apparaît sous le format suivant :<br /><br /> x.x:x.x|  
|**product_version**|**varchar(23)**|Version du produit. Apparaît sous le format suivant :<br /><br /> x.x:x.x|  
|**debug**|**bit**|1 = le module est une version de débogage du module chargé.|  
|**patched**|**bit**|1 = le module a été corrigé.|  
|**version préliminaire**|**bit**|1 = le module est une version préliminaire du module chargé.|  
|**private_build**|**bit**|1 = le module est une version privée du module chargé.|  
|**special_build**|**bit**|1 = le module est une version spéciale du module chargé.|  
|**language**|**Int**|Langue des informations de version du module.|  
|**Entreprise**|**nvarchar (256)**|Nom de la société qui a créé le module.|  
|**description**|**nvarchar (256)**|Description du module.|  
|**name**|**nvarchar(255)**|Nom du module. Inclut le chemin d'accès complet du module.|  
|**pdw_node_id**|**Int**|**S’applique à** : [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L’identificateur pour le nœud se trouvant sur cette distribution.|  
  
## <a name="permissions"></a>Autorisations  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vues de gestion dynamique liées à système d’exploitation SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
