---
title: Catalog.execution_property_override_values | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
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
ms.assetid: 83cbdd6f-ddde-47bf-abde-36bd24272621
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ed9ae4ea7a7165efe53a551832d8e4a0eb7a2114
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogexecutionpropertyoverridevalues"></a>catalog.execution_property_override_values
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche les valeurs de remplacement de la propriété définies pendant l'exécution du package.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|property_id|**bigint**|Identificateur unique de valeur de remplacement de la propriété.|  
|execution_id|**bigint**|ID unique de l'instance d'exécution.|  
|property_path|**nvarchar(4000)**|Chemin d'accès à la propriété dans le package.|  
|property_value|**nvarchar(max)**|Valeur de remplacement de la propriété.|  
| sensible|**bit**|Lorsque la valeur est 1, la propriété est sensible et est chiffrée lorsqu'elle est stockée. Lorsque la valeur est 0, la propriété n'est pas sensible et la valeur est stockée dans en texte en clair.|  
  
## <a name="remarks"></a>Notes  
 Cette vue affiche une ligne pour chaque exécution de la propriété valeurs ont été remplacées à l’aide de la **substitutions de propriété** section dans le **avancé** onglet de la **exécuter le Package** boîte de dialogue. Le chemin d’accès à la propriété est dérivée de la **chemin d’accès du Package** propriété de la tâche du package.  
  
## <a name="permissions"></a>Permissions  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur l'instance d'exécution  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
> [!NOTE]  
>  Lorsque vous avez l'autorisation pour effectuer une opération sur le serveur, vous avez également l'autorisation pour consulter les informations de l'opération. La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
  

