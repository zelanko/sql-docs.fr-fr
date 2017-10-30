---
title: "Catalog.explicit_object_permissions (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 49b09e0f-06e8-451f-b979-a0d91000bfe3
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ce92a61241cb70f5e1c6d1bab8db8264d6228bd2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogexplicitobjectpermissions-ssisdb-database"></a>catalog.explicit_object_permissions (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche uniquement les autorisations affectées explicitement à l'utilisateur.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|object_type|**smallint**|Type d'objet sécurisable. Les types d'objets sécurisables incluent le dossier (`1`), le projet (`2`), l'environnement (`3`) et l'opération (`4`).|  
|object_id|**bigint**|Identificateur unique (ID) ou clé primaire de l'objet sécurisé.|  
|principal_id|**int**|ID du principal de base de données.|  
|permission_type|**smallint**|Type de l'autorisation.|  
|is_deny|**bit**|Indique si l'autorisation a été refusée ou accordée. Lorsque la valeur est `1`, l'autorisation a été refusée. Lorsque la valeur est `0`, l'autorisation n'a pas été refusée.|  
|grantor_id|**int**|ID du principal qui a accordé l'autorisation.|  
  
## <a name="remarks"></a>Notes  
 Cette vue affiche les types d'autorisation répertoriés dans le tableau suivant :  
  
|Valeur permission_type|Nom de l'autorisation|Description de l'autorisation|Types d'objet applicables|  
|----------------------------|---------------------|----------------------------|-----------------------------|  
|`1`|READ|Permet au principal de lire des informations considérées comme faisant partie de l'objet, telles que les propriétés. Il n'autorise pas le principal à énumérer ou à lire le contenu d'autres objets contenus dans l'objet.|Dossier, projet, environnement, opération|  
|`2`|MODIFY|Permet au principal de modifier des informations considérées comme faisant partie de l'objet, telles que les propriétés. Il ne permet pas au principal de modifier d'autres objets contenus dans l'objet.|Dossier, projet, environnement, opération|  
|`3`|Exécutez|Permet au principal d'exécuter tous les packages dans le projet.|Projet|  
|`4`|MANAGE_PERMISSIONS|Permet au principal d'affecter des autorisations aux objets.|Dossier, projet, environnement, opération|  
|`100`|CREATE_OBJECTS|Permet au principal de créer des objets dans le dossier.|Dossier|  
|`101`|READ_OBJECTS|Permet au principal de lire tous les objets dans le dossier.|Dossier|  
|`102`|MODIFY_OBJECTS|Permet au principal de modifier tous les objets dans le dossier.|Dossier|  
|`103`|EXECUTE_OBJECTS|Permet au principal d'exécuter tous les packages de tous les projets dans le dossier.|Dossier|  
|`104`|MANAGE_OBJECT_PERMISSIONS|Permet au principal de gérer des autorisations sur tous les objets dans le dossier.|Dossier|  
  
## <a name="permissions"></a>Permissions  
 Cette vue ne donne pas une vue complète des autorisations pour le principal actuel. L'utilisateur doit également vérifier si le principal est un membre de rôles et de groupes auxquels des autorisations sont affectées.  
  
  

