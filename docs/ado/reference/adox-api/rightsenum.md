---
title: RightsEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RightsEnum
helpviewer_keywords:
- RightsEnum enumeration [ADOX]
ms.assetid: 55ee67c7-a583-42aa-849a-78264b4cb614
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1904a77ae104576f2a9f82fc09d8728e2ec88c11
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47760507"
---
# <a name="rightsenum"></a>RightsEnum
Spécifie les droits ou les autorisations pour un groupe ou utilisateur sur un objet.  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adRightCreate**|16384 (&AMP; H4000)|L’utilisateur ou le groupe est autorisé à créer de nouveaux objets de ce type.|  
|**adRightDelete**|65536 (&AMP; H10000)|L’utilisateur ou le groupe est autorisé à supprimer des données à partir d’un objet. Pour les objets tels que **Tables**, l’utilisateur est autorisé à supprimer les valeurs de données à partir d’enregistrements.|  
|**adRightDrop**|256 (&AMP; H100)|L’utilisateur ou le groupe est autorisé à supprimer des objets à partir du catalogue. Par exemple, **Tables** peuvent être supprimées par une commande DROP TABLE SQL.|  
|**adRightExclusive**|512 (&AMP; H200)|L’utilisateur ou le groupe est autorisé à accéder à l’objet exclusivement.|  
|**adRightExecute**|536870912 (&AMP; H20000000)|L’utilisateur ou le groupe est autorisé à exécuter l’objet.|  
|**adRightFull**|268435456 (&AMP; H10000000)|L’utilisateur ou le groupe a toutes les autorisations sur l’objet.|  
|**adRightInsert**|32768 (&AMP; H8000)|L’utilisateur ou le groupe a l’autorisation d’insérer l’objet. Pour les objets tels que **Tables**, l’utilisateur est autorisé à insérer des données dans la table.|  
|**adRightMaximumAllowed**|33554432 (&AMP; H2000000)|L’utilisateur ou le groupe possède le nombre maximal d’autorisations autorisé par le fournisseur. Des autorisations spécifiques dépendent du fournisseur.|  
|**adRightNone**|0|L’utilisateur ou le groupe dispose d’aucune autorisation pour l’objet.|  
|**adRightRead**|-2147483648 (&AMP; H80000000)|L’utilisateur ou le groupe est autorisé à lire l’objet. Pour les objets tels que [Tables](../../../ado/reference/adox-api/table-object-adox.md), l’utilisateur est autorisé à lire les données dans la table.|  
|**adRightReadDesign**|1024 (&AMP; H400)|L’utilisateur ou le groupe est autorisé à lire la conception de l’objet.|  
|**adRightReadPermissions**|131072 (&AMP; H20000)|L’utilisateur ou le groupe peut afficher, mais pas modifier, les autorisations spécifiques pour un objet dans le catalogue.|  
|**adRightReference**|8192 (&AMP; H2000)|L’utilisateur ou le groupe est autorisé à faire référence à l’objet.|  
|**adRightUpdate**|1073741824 (&AMP; H40000000)|L’utilisateur ou le groupe est autorisé à mettre à jour de l’objet. Pour les objets tels que **Tables**, l’utilisateur est autorisé à mettre à jour les données dans la table.|  
|**adRightWithGrant**|4096 (&AMP; H1000)|L’utilisateur ou le groupe est autorisé à accorder des autorisations sur l’objet.|  
|**adRightWriteDesign**|2048 (&AMP; H800)|L’utilisateur ou le groupe est autorisé à modifier la conception pour l’objet.|  
|**adRightWriteOwner**|524288 (&AMP; H80000)|L’utilisateur ou le groupe est autorisé à modifier le propriétaire de l’objet.|  
|**adRightWritePermissions**|262144 (&AMP; H40000)|L’utilisateur ou le groupe peut modifier les autorisations spécifiques pour un objet dans le catalogue.|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[GetPermissions, méthode (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|[SetPermissions, méthode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
