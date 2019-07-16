---
title: Sys.resource_governor_configuration (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_configuration_TSQL
- sys.resource_governor_configuration
- resource_governor_configuration_TSQL
- resource_governor_configuration
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor_configuration catalog view
ms.assetid: 89099668-1dc6-4b07-9d8b-49bc95c7bfc0
author: stevestein
ms.author: sstein
ms.openlocfilehash: c85332cb1c26f81cdbbaa7bffa5410cf29e711e2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67904551"
---
# <a name="sysresourcegovernorconfiguration-transact-sql"></a>sys.resource_governor_configuration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne l'état du gouverneur de ressources stocké.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|classifier_function_id|**Int**|ID de la fonction classifieur tel qu'il est stocké dans les métadonnées. N'accepte pas la valeur NULL.<br /><br /> **Remarque** cette fonction est utilisée pour classer les nouvelles sessions et utilise des règles pour router la charge de travail vers le groupe de charges de travail approprié. Pour plus d’informations, consultez [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).|  
|is_enabled|**bit**|Indique l'état actuel du gouverneur de ressources :<br /><br /> 0 = le gouverneur de ressources n’est pas activé.<br /><br /> 1 = resource Governor est activé.<br /><br /> N'accepte pas la valeur NULL.|  
|max_outstanding_io_per_volume|**int**|**S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Nombre maximal d'E/S en attente par volume.|  
  
## <a name="remarks"></a>Notes  
 L'affichage catalogue affiche la configuration du gouverneur de ressources telle qu'elle est stockée dans les métadonnées. Pour consulter la configuration en mémoire, utilisez la vue de gestion dynamique correspondante.  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation VIEW ANY DEFINITION pour consulter le contenu, requiert l'autorisation CONTROL SERVER pour modifier le contenu.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant indique comment obtenir et comparer les valeurs de métadonnées stockées et les valeurs en mémoire de la configuration du gouverneur de ressources.  
  
```  
USE master;  
GO  
-- Get the stored metadata.  
SELECT   
object_schema_name(classifier_function_id) AS 'Classifier UDF schema in metadata',   
object_name(classifier_function_id) AS 'Classifier UDF name in metadata'  
FROM   
sys.resource_governor_configuration;  
GO  
-- Get the in-memory configuration.  
SELECT   
object_schema_name(classifier_function_id) AS 'Active classifier UDF schema',   
object_name(classifier_function_id) AS 'Active classifier UDF name'  
FROM   
sys.dm_resource_governor_configuration;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue du gouverneur de ressources &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Sys.dm_resource_governor_configuration &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql.md)   
 [gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md)  
  
  
