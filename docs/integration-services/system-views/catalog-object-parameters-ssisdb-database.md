---
title: "Catalog.object_parameters (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: d7b04903-2d61-4159-9456-475942d1f732
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9d538e5b55ef4e8880afb2d008b11c17d9a03189
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogobjectparameters-ssisdb-database"></a>catalog.object_parameters (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche les paramètres de tous les packages et projets dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|parameter_id|**bigint**|Identificateur (ID) unique du paramètre.|  
|project_id|**bigint**|ID unique du projet.|  
|object_type|**smallint**|Le type de paramètre. La valeur est `20` pour un paramètre du projet et `30` pour un paramètre du package.|  
|object_name|**sysname**|Nom du projet ou package correspondant.|  
|parameter_name|**sysname(nvarchar(128))**|Nom du paramètre.|  
|data_type|**nvarchar (128)**|Type de données du paramètre.|  
|required|**bit**|Lorsque la valeur est `1`, la valeur de paramètre est obligatoire pour démarrer l'exécution. Lorsque la valeur est `0`, la valeur de paramètre n'est pas obligatoire pour démarrer l'exécution.|  
| sensible|**bit**|Lorsque la valeur est `1`, la valeur de paramètre est sensible. Lorsque la valeur est `0`, la valeur de paramètre n'est pas sensible.|  
|description|**nvarchar (1024)**|Description facultative du package.|  
|design_default_value|**sql_variant**|Valeur par défaut du paramètre qui a été affecté pendant la conception du projet ou du package.|  
|default_value|**sql_variant**|Valeur par défaut utilisée actuellement sur le serveur.|  
|Value_type|**char (1)**|Indique la valeur de type de paramètre. Ce champ affiche `V` lorsque parameter_value est une valeur littérale et `R` lorsque la valeur est assignée en faisant référence à une variable d’environnement.|  
|value_set|**bit**|Lorsque la valeur est `1`, la valeur de paramètre a été affectée. Lorsque la valeur est `0`, la valeur de paramètre n'a pas été affectée.|  
|referenced_variable_name|**nvarchar (128)**|Nom de la variable d'environnement affectée à la valeur du paramètre. La valeur par défaut est **NULL**.|  
|validation_status|**char (1)**|Identifié à titre d'information uniquement. Inutilisé dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|last_validation_time|**DateTimeOffset(7)**|Identifié à titre d'information uniquement. Inutilisé dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
  
## <a name="permissions"></a>Permissions  
 Pour consulter des lignes dans cette vue, vous devez avoir l'une des autorisations suivantes :  
  
-   Autorisation READ sur le projet  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur.  
  
 La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
  
