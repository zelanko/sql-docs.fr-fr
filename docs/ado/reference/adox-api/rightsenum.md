---
title: RightsEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- RightsEnum
helpviewer_keywords:
- RightsEnum enumeration [ADOX]
ms.assetid: 55ee67c7-a583-42aa-849a-78264b4cb614
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ac335398b4895e01ece3324488d30bfd670fd140
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="rightsenum"></a>RightsEnum
Spécifie les droits ou autorisations pour un groupe ou utilisateur sur un objet.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adRightCreate**|16384 (& H4000)|L’utilisateur ou le groupe a l’autorisation de créer des objets de ce type.|  
|**adRightDelete**|65536 (& H10000)|L’utilisateur ou le groupe a l’autorisation de supprimer des données à partir d’un objet. Pour les objets tels que **Tables**, l’utilisateur est autorisé à supprimer des valeurs de données à partir d’enregistrements.|  
|**adRightDrop**|256 (& H100)|L’utilisateur ou le groupe a l’autorisation de supprimer des objets à partir du catalogue. Par exemple, **Tables** peut être supprimée par une commande DROP TABLE SQL.|  
|**adRightExclusive**|512 (& H200)|L’utilisateur ou le groupe a l’autorisation d’accéder à l’objet exclusivement.|  
|**adRightExecute**|536870912 (& H20000000)|L’utilisateur ou le groupe a l’autorisation d’exécuter l’objet.|  
|**adRightFull**|268435456 (& H10000000)|L’utilisateur ou le groupe a toutes les autorisations sur l’objet.|  
|**adRightInsert**|32768 (& H8000)|L’utilisateur ou le groupe a l’autorisation d’insérer l’objet. Pour les objets tels que **Tables**, l’utilisateur a l’autorisation d’insérer des données dans la table.|  
|**adRightMaximumAllowed**|33554432 (& H2000000)|L’utilisateur ou le groupe a le nombre maximal d’autorisations permises par le fournisseur. Des autorisations spécifiques dépendent du fournisseur.|  
|**adRightNone**|0|L’utilisateur ou le groupe n’est pas autorisé pour l’objet.|  
|**adRightRead**|-2147483648 (& H80000000)|L’utilisateur ou le groupe a l’autorisation pour lire l’objet. Pour les objets tels que [Tables](../../../ado/reference/adox-api/table-object-adox.md), l’utilisateur est autorisé à lire les données de la table.|  
|**adRightReadDesign**|1024 (& H400)|L’utilisateur ou le groupe a l’autorisation de lire la conception de l’objet.|  
|**adRightReadPermissions**|131072 (& H20000)|L’utilisateur ou le groupe peut afficher, mais pas modifier, les autorisations spécifiques à un objet dans le catalogue.|  
|**adRightReference**|8192 (& H2000)|L’utilisateur ou le groupe a l’autorisation pour référencer l’objet.|  
|**adRightUpdate**|1073741824 (& H40000000)|L’utilisateur ou le groupe a l’autorisation de mettre à jour l’objet. Pour les objets tels que **Tables**, l’utilisateur est autorisé à mettre à jour les données dans la table.|  
|**adRightWithGrant**|4096 (& H1000)|L’utilisateur ou le groupe a l’autorisation d’accorder des autorisations sur l’objet.|  
|**adRightWriteDesign**|2048 (& H800)|L’utilisateur ou le groupe a l’autorisation de modifier la conception de l’objet.|  
|**adRightWriteOwner**|524288 (& H80000)|L’utilisateur ou le groupe a l’autorisation de modifier le propriétaire de l’objet.|  
|**adRightWritePermissions**|262144 (& H40000)|L’utilisateur ou le groupe peut modifier les autorisations spécifiques à un objet dans le catalogue.|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[GetPermissions, méthode (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|[SetPermissions, méthode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
