---
title: Sys.dm_os_stacks (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c31bf39c4f133aa6f693614845cb54a5cf2bfc6f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67899759"
---
# <a name="sysdmosstacks-transact-sql"></a>sys.dm_os_stacks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise cette vue de gestion dynamique en interne pour effectuer les opérations suivantes :  
  
-   suivre les données de débogage telles que des allocations exceptionnelles ;  
  
-   Supposer ou valider une logique utilisée par les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] là où le composant suppose qu'un certain appel a eu lieu ;  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**stack_address**|**varbinary(8)**|Adresse unique d'allocation de cette pile. N'accepte pas la valeur NULL.|  
|**frame_index**|**int**|Chaque ligne représente une fonction qui, appelez lorsque triés par ordre croissant par index de trame pour un particulier **(stack_address) donnée**, retourne la pile des appels. N'accepte pas la valeur NULL.|  
|**frame_address**|**varbinary(8)**|Adresse de l'appel de la fonction. N'accepte pas la valeur NULL.|  
  
## <a name="remarks"></a>Notes  
 **Sys.dm_os_stacks** requiert la présence sur le serveur pour afficher correctement les informations que les symboles du serveur et d’autres composants.  
  
## <a name="permissions"></a>Autorisations

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], requiert l’autorisation `VIEW DATABASE STATE` dans la base de données.   


## <a name="see-also"></a>Voir aussi  
  [Vues de gestion dynamique liées à système d’exploitation SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
