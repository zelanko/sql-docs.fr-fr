---
title: Sys.dm_os_stacks (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_os_stacks
- dm_os_stacks_TSQL
- sys.dm_os_stacks
- sys.dm_os_stacks_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_stacks dynamic management view
ms.assetid: a69b06c4-28f0-4535-8fa1-9f132db4d916
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9e3e292fbafbee9586d377f133af7f9d3ee520d5
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosstacks-transact-sql"></a>sys.dm_os_stacks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise cette vue de gestion dynamique en interne pour effectuer les opérations suivantes :  
  
-   suivre les données de débogage telles que des allocations exceptionnelles ;  
  
-   Supposer ou valider une logique utilisée par les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] là où le composant suppose qu'un certain appel a eu lieu ;  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**(stack_address) donnée**|**varbinary (8)**|Adresse unique d'allocation de cette pile. N'accepte pas la valeur NULL.|  
|**frame_index**|**int**|Chaque ligne représente une fonction qui, appelez lorsque triées par ordre croissant par index de l’image en tant **(stack_address) donnée**, retourne la pile des appels. N'accepte pas la valeur NULL.|  
|**frame_address**|**varbinary (8)**|Adresse de l'appel de la fonction. N'accepte pas la valeur NULL.|  
  
## <a name="remarks"></a>Notes  
 **Sys.dm_os_stacks** requiert que les symboles du serveur et d’autres composants sur le serveur pour afficher correctement les informations.  
  
## <a name="permissions"></a>Permissions  
Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] niveaux Premium, nécessite le `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard et les niveaux de base, nécessite le **administrateur du serveur** ou **administrateur Active Directory de Azure** compte.  
  

## <a name="see-also"></a>Voir aussi  
  [Système d’exploitation de serveur SQL relatives des vues de gestion dynamique &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
