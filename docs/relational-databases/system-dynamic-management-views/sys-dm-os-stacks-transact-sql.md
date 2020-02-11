---
title: sys. dm_os_stacks (Transact-SQL) | Microsoft Docs
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
ms.openlocfilehash: 8f287c548a7ebb71b1ebf3e1bce30e43b412c755
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68265716"
---
# <a name="sysdm_os_stacks-transact-sql"></a>sys.dm_os_stacks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise cette vue de gestion dynamique en interne pour effectuer les opérations suivantes :  
  
-   suivre les données de débogage telles que des allocations exceptionnelles ;  
  
-   Supposer ou valider une logique utilisée par les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] là où le composant suppose qu'un certain appel a eu lieu ;  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**stack_address**|**varbinary (8)**|Adresse unique d'allocation de cette pile. N'accepte pas la valeur NULL.|  
|**frame_index**|**int**|Chaque ligne représente un appel de fonction qui, lorsqu’il est trié par ordre croissant d’index de frames pour une **stack_address**particulière, retourne la pile des appels complète. N'accepte pas la valeur NULL.|  
|**frame_address**|**varbinary (8)**|Adresse de l'appel de la fonction. N'accepte pas la valeur NULL.|  
  
## <a name="remarks"></a>Notes  
 **sys. dm_os_stacks** nécessite que les symboles du serveur et des autres composants soient présents sur le serveur pour afficher correctement les informations.  
  
## <a name="permissions"></a>Autorisations

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiert `VIEW SERVER STATE` l’autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux Premium, requiert l' `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux standard et de base, nécessite l' **administrateur du serveur** ou un compte d' **administrateur Azure Active Directory** .   


## <a name="see-also"></a>Voir aussi  
  [SQL Server vues de gestion dynamique liées au système d’exploitation &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
