---
title: Sys.server_assembly_modules (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_assembly_modules_TSQL
- sys.server_assembly_modules
- server_assembly_modules
- sys.server_assembly_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_assembly_modules catalog view
ms.assetid: af799e38-2d16-49b2-bcf5-6f9199af899e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a257f63328fe0abcf121b82b619bc58b70b7c6f7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711699"
---
# <a name="sysserverassemblymodules-transact-sql"></a>sys.server_assembly_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient pour chaque module d'assembly une ligne destinée aux déclencheurs de niveau serveur de type TA. Cette vue mappe des déclencheurs d'assembly à leur implémentation CLR sous-jacente. Vous pouvez joindre cette relation à **sys.server_triggers**. L’assembly doit être chargé dans le **master** base de données. C'est le tuple (object_id) qui correspond à la clé de cette relation.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**Int**|Contre référence de FOREIGN KEY à l'objet sur lequel ce module d'assembly est défini.|  
|**assembly_id**|**Int**|ID de l'assembly à partir duquel ce module a été créé. L'assembly doit être chargé dans la base de données master.|  
|**assembly_class**|**sysname**|Nom de la classe dans l'assembly définissant ce module.|  
|**assembly_method**|**sysname**|Nom de la méthode dans la classe définissant ce module. Correspond à la valeur NULL dans le cas de fonctions d'agrégation (AF, aggregate functions).|  
|**execute_as_principal_id**|**Int**|ID de l'instruction d'exécution en tant que principal de serveur (EXECUTE AS).<br /><br /> Valeur NULL par défaut ou dans le cas de l'instruction EXECUTE AS CALLER.<br /><br /> ID du principal spécifié si EXECUTE AS SELF EXECUTE AS \<principal >.<br /><br /> -2 = EXECUTE AS OWNER.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Affichages catalogue de l’objet &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
