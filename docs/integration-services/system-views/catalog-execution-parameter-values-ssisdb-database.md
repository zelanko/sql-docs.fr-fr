---
title: "Catalog.execution_parameter_values (base de données SSISDB) | Documents Microsoft"
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
ms.assetid: ec93e67b-04ce-4aae-ab96-3ad20e9793ad
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 60907a82f3d0bb9f273355fd6bfbd7378ce72c9f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogexecutionparametervalues-ssisdb-database"></a>catalog.execution_parameter_values (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche les valeurs de paramètre effectives utilisées par les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pendant une instance d'exécution.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|execution_parameter_id|**bigint**|Identificateur (ID) unique du paramètre d'exécution.|  
|execution_id|**bigint**|ID unique de l'instance d'exécution.|  
|object_type|**smallint**|Lorsque la valeur est `20`, le paramètre est un paramètre de projet. Lorsque la valeur est `30`, le paramètre est un paramètre de package. Lorsque la valeur est `50`, le paramètre est une des valeurs suivantes :<br /><br /> **LOGGING_LEVEL**<br /><br /> **DUMP_ON_ERROR**<br /><br /> **DUMP_ON_EVENT**<br /><br /> **DUMP_EVENT_CODE**<br /><br /> **CALLER_INFO**<br /><br /> **SYNCHRONISÉ**|  
|parameter_data_type|**nvarchar (128)**|Type de données du paramètre.|  
|parameter_name|**sysname**|Nom du paramètre.|  
|parameter_value|**sql_variant**|Valeur du paramètre. Lorsque sensibles est `0`, la valeur de texte en clair est affichée. Lorsque sensibles est `1`, le **NULL** valeur s’affiche.|  
|sensible|**bit**|Lorsque la valeur est `1`, la valeur de paramètre est sensible. Lorsque la valeur est `0`, la valeur de paramètre n'est pas sensible.|  
|required|**bit**|Lorsque la valeur est `1`, la valeur de paramètre est obligatoire pour démarrer l'exécution. Lorsque la valeur est `0`, la valeur de paramètre n'est pas obligatoire pour démarrer l'exécution.|  
|value_set|**bit**|Lorsque la valeur est `1`, la valeur de paramètre a été affectée. Lorsque la valeur est `0`, la valeur de paramètre n'a pas été affectée.|  
|runtime_override|**bit**|Lorsque la valeur est `1`, la valeur d'origine a été modifiée avant le démarrage de l'exécution. Lorsque la valeur est `0`, la valeur de paramètre est la valeur d'origine définie.|  
  
## <a name="remarks"></a>Notes  
 Cette vue affiche une ligne pour chaque paramètre d'exécution dans le catalogue. Une valeur de paramètre d'exécution est la valeur affectée à un paramètre du projet ou à un paramètre du package pendant une instance d'exécution unique.  
  
## <a name="permissions"></a>Permissions  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur l'instance d'exécution  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
> [!NOTE]  
>  Lorsque vous avez l'autorisation pour effectuer une opération sur le serveur, vous avez également l'autorisation pour consulter les informations de l'opération. La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
  

