---
title: "Catalog.extended_operation_info (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: db299b45-557d-4c62-8e14-355cdb051f63
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4d89a9adbf89dcc89715832664dcca176cd7f2ff
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogextendedoperationinfo-ssisdb-database"></a>catalog.extended_operation_info (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche les informations étendues pour toutes les opérations dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|info_id|**bigint**|Identificateur unique (ID) des informations étendues.|  
|operation_id|**bigint**|ID unique de l'opération qui correspond aux informations étendues.|  
|object_name|**nvarchar (260)**|Nom de l'objet.|  
|object_type|**smallint**|Type d'objet affecté par l'opération. L'objet peut être un dossier (`10`), un projet (`20`), un package (`30`), un environnement (`40`) ou une instance d'exécution (`50`).|  
|reference_id|**bigint**|ID unique de la référence utilisée dans l'opération.|  
|status|**int**|État de l'opération. Les valeurs possibles sont Créé (`1`), En cours d'exécution (`2`), Annulé (`3`), Échec (`4`), En attente (`5`), Arrêté prématurément (`6`), Opération réussie (`7`), Arrêt en cours (`8`) et Fin (`9`).|  
|start_time|**DateTimeOffset(7)**|Date et heure du début de l'opération.|  
|end_time|**DateTimeOffset(7)**|Date et heure auxquelles l'opération s'est terminée.|  
  
## <a name="remarks"></a>Notes  
 Une seule opération peut avoir plusieurs lignes d'informations étendues.  
  
## <a name="permissions"></a>Permissions  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur l'opération  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
> [!NOTE]  
>  Lorsque vous avez l'autorisation pour effectuer une opération sur le serveur, vous avez également l'autorisation pour consulter les informations de l'opération. La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
  

