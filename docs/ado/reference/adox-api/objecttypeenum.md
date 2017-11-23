---
title: ObjectTypeEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: ObjectTypeEnum
helpviewer_keywords: ObjectTypeEnum enumeration [ADOX]
ms.assetid: 3fdecfca-aa91-4596-ad98-610f1b7f840b
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5a320f3471c3ba7db9bd51225d9237ae0d29e085
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="objecttypeenum"></a>ObjectTypeEnum
Spécifie le type d’objet de base de données pour lequel définir des autorisations ou la propriété.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adPermObjColumn**|2|L’objet est une colonne.|  
|**adPermObjDatabase**|3|L’objet est une base de données.|  
|**adPermObjProcedure**|4|L’objet est une procédure.|  
|**adPermObjProviderSpecific**|-1|L’objet est un type défini par le fournisseur. Une erreur se produit si le *ObjectType* paramètre est **adPermObjProviderSpecific** et un *ObjectTypeId* n’est pas fourni.|  
|**adPermObjTable**|1|L’objet est une table.|  
|**adPermObjView**|5|L’objet est une vue.|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[GetObjectOwner, méthode (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)|[GetPermissions, méthode (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|  
|[SetObjectOwner, méthode (ADOX)](../../../ado/reference/adox-api/setobjectowner-method.md)|[SetPermissions, méthode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
