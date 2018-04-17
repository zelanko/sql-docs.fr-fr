---
title: Sys.dm_os_stacks (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_stacks
- dm_os_stacks_TSQL
- sys.dm_os_stacks
- sys.dm_os_stacks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_stacks dynamic management view
ms.assetid: a69b06c4-28f0-4535-8fa1-9f132db4d916
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 261ff9ac3799009ee796fa4712599d15b33f5d59
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmosstacks-transact-sql"></a>sys.dm_os_stacks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise cette vue de gestion dynamique en interne pour effectuer les opérations suivantes :  
  
-   suivre les données de débogage telles que des allocations exceptionnelles ;  
  
-   Supposer ou valider une logique utilisée par les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] là où le composant suppose qu'un certain appel a eu lieu ;  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**stack_address**|**varbinary(8)**|Adresse unique d'allocation de cette pile. N'accepte pas la valeur NULL.|  
|**frame_index**|**int**|Chaque ligne représente une fonction qui, appelez lorsque triées par ordre croissant par index de l’image en tant **(stack_address) donnée**, retourne la pile des appels. N'accepte pas la valeur NULL.|  
|**frame_address**|**varbinary(8)**|Adresse de l'appel de la fonction. N'accepte pas la valeur NULL.|  
  
## <a name="remarks"></a>Notes  
 **Sys.dm_os_stacks** requiert que les symboles du serveur et d’autres composants sur le serveur pour afficher correctement les informations.  
  
## <a name="permissions"></a>Autorisations

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.   


## <a name="see-also"></a>Voir aussi  
  [Vues de gestion dynamique liées à système d’exploitation SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
