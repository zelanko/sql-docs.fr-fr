---
title: Sys.resource_governor_configuration (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_configuration_TSQL
- sys.resource_governor_configuration
- resource_governor_configuration_TSQL
- resource_governor_configuration
dev_langs: TSQL
helpviewer_keywords: sys.resource_governor_configuration catalog view
ms.assetid: 89099668-1dc6-4b07-9d8b-49bc95c7bfc0
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a1a02e4e7b26ec1c86f10f13632ade9c3bd3d264
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysresourcegovernorconfiguration-transact-sql"></a>sys.resource_governor_configuration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne l'état du gouverneur de ressources stocké.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|classifier_function_id|**int**|ID de la fonction classifieur tel qu'il est stocké dans les métadonnées. N'accepte pas la valeur NULL.<br /><br /> **Remarque** cette fonction est utilisée pour classer les nouvelles sessions et utilise des règles pour router la charge de travail au groupe de charges de travail approprié. Pour plus d’informations, consultez [du gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md).|  
|is_enabled|**bit**|Indique l'état actuel du gouverneur de ressources :<br /><br /> 0 = le gouverneur de ressources n’est pas activé.<br /><br /> 1 = le gouverneur de ressources est activé.<br /><br /> N'accepte pas la valeur NULL.|  
|max_outstanding_io_per_volume|**int**|**S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Nombre maximal d'E/S en attente par volume.|  
  
## <a name="remarks"></a>Notes  
 L'affichage catalogue affiche la configuration du gouverneur de ressources telle qu'elle est stockée dans les métadonnées. Pour consulter la configuration en mémoire, utilisez la vue de gestion dynamique correspondante.  
  
## <a name="permissions"></a>Permissions  
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
 [Affichages catalogue du gouverneur de ressources &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Sys.dm_resource_governor_configuration &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql.md)   
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)  
  
  
