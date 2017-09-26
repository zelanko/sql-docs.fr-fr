---
title: "Catalog.environment_variables (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 45f5aacd-505a-443b-8fc2-c7929e78cff8
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 40e31b9697c453f6a9d60dfcc8d9302dfefe0ac4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogenvironmentvariables-ssisdb-database"></a>catalog.environment_variables (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche les détails de la variable d'environnement pour tous les environnements dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|variable_id|**bigint**|Identificateur (ID) unique de la variable d'environnement.|  
|environment_id|**bigint**|ID unique de l'environnement auquel la variable est associée.|  
|name|**sysname**|Nom de la variable d'environnement.|  
|description|**nvarchar (1024)**|Description de la variable d'environnement.|  
|Type|**nvarchar (128)**|Type de données de la variable d'environnement.|  
|sensible|**bit**|Lorsque la valeur est `1`, la variable est sensible et est chiffrée lorsqu'elle est stockée. Lorsque la valeur est `0`, la variable n'est pas sensible et la valeur est stockée dans en texte en clair.|  
|valeur|**sql_variant**|Valeur de la variable d'environnement. Lorsque sensibles est `0`, la valeur de texte en clair est affichée. Lorsque sensibles est `1`, le **NULL** valeur s’affiche.|  
  
## <a name="remarks"></a>Notes  
 Cette vue affiche une ligne pour chaque variable d'environnement dans le catalogue.  
  
## <a name="permissions"></a>Permissions  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur l'environnement correspondant  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
> [!NOTE]  
>  Lorsque vous avez l'autorisation pour effectuer une opération sur le serveur, vous avez également l'autorisation pour consulter les informations de l'opération. La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
  
