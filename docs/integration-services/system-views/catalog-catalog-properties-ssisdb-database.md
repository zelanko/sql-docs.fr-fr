---
title: "Catalog.catalog_properties (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: e604a382-95c8-4764-b268-742eb5c6d4cf
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ca3d5da05126d5b71bf6d714f9e8449f9f5c8335
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcatalogproperties-ssisdb-database"></a>catalog.catalog_properties (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche les propriétés du catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar (256)**|Nom de la propriété de catalogue.|  
|property_value|**nvarchar (256)**|Valeur de la propriété de catalogue.|  
  
## <a name="remarks"></a>Notes  
 Cette vue affiche une ligne pour chaque propriété de catalogue. Les propriétés affichées par cette vue incluent les éléments suivants :  
  
|Nom de la propriété| Description|  
|-------------------|-----------------|  
|**ENCRYPTION_ALGORITHM**|Type d'algorithme de chiffrement utilisé pour chiffrer des données sensibles. Les valeurs prises en charge incluent : `DES`, `TRIPLE_DES`, `TRIPLE_DES_3KEY`, `DESX`, `AES_128`, `AES_192` et `AES_256`. Remarque : la base de données de catalogue doit être en mode mono-utilisateur pour modifier cette propriété.|  
|**MAX_PROJECT_VERSIONS**|Nombre de nouvelles versions du projet qui seront conservées pour un projet unique. Lorsque le nettoyage de version est permis, les versions antérieures au delà de ce nombre seront supprimées.|  
|**OPERATION_CLEANUP_ENABLED**|Lorsque la valeur est `TRUE`, détails et les messages d’opération antérieures à **RETENTION_WINDOW** (jours) sont supprimées du catalogue. Lorsque la valeur est `FALSE`, tous les détails et les messages de l'opération sont stockés dans le catalogue. Remarque : un travail [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectue le nettoyage de l'opération.|  
|**RETENTION_WINDOW**|Nombre de jours que les détails et les messages de l'opération sont stockés dans le catalogue. Lorsque la valeur est `-1`, la période de conservation est infinie. Remarque : Si aucun nettoyage n’est pas souhaité, définissez **OPERATION_CLEANUP_ENABLED** à **FALSE**.|  
|**VALIDATION_TIMEOUT**|Les validations seront arrêtées si elles ne s'achèvent pas dans le nombre de secondes spécifié par cette propriété.|  
|**VERSION_CLEANUP_ENABLED**|Lorsque la valeur est `TRUE`, seule la **MAX_PROJECT_VERSIONS** nombre de versions de projet est stockée dans le catalogue et toutes les autres versions de projet sont supprimées. Lorsque la valeur est **FALSE**, toutes les versions de projet sont stockées dans le catalogue. Remarque : un travail [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectue le nettoyage de l'opération.|  
|**SERVER_LOGGING_LEVEL**|Niveau de journalisation par défaut pour le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].|  
  
## <a name="permissions"></a>Permissions  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
  

