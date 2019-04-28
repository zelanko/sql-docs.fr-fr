---
title: ObjectTypeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ObjectTypeEnum
helpviewer_keywords:
- ObjectTypeEnum enumeration [ADOX]
ms.assetid: 3fdecfca-aa91-4596-ad98-610f1b7f840b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ed7273b2fd24690956fa5c5ffe317ad9c00c40ee
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62710268"
---
# <a name="objecttypeenum"></a>ObjectTypeEnum
Spécifie le type d’objet de base de données pour lequel définir des autorisations ou la propriété.  
  
|Constante|Value|Description|  
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
