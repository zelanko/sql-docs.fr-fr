---
title: "SetObjectOwner, méthode | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Catalog::SetObjectOwner
- _Catalog::raw_SetObjectOwner
helpviewer_keywords:
- SetObjectOwner method [ADOX]
ms.assetid: e5170a37-9d6e-43db-bfb6-9b6631fa3048
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 35b592bf1503c457532d8988f0fd6e09f06115dd
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="setobjectowner-method"></a>SetObjectOwner, méthode
Spécifie le propriétaire d’un objet dans un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Catalog.SetObjectOwner ObjectName, ObjectType, OwnerName [,ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ObjectName*  
 A **chaîne** valeur qui spécifie le nom de l’objet pour lequel vous permet de spécifier le propriétaire.  
  
 *ObjectType*  
 A **Long** valeur qui peut être une de le [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) constantes qui spécifie le type de propriétaire.  
  
 *OwnerName*  
 A **chaîne** valeur qui spécifie le [nom](../../../ado/reference/adox-api/name-property-adox.md) de la [utilisateur](../../../ado/reference/adox-api/user-object-adox.md) ou [groupe](../../../ado/reference/adox-api/group-object-adox.md) au propriétaire de l’objet.  
  
 *ObjectTypeId*  
 Ce paramètre est facultatif. A **Variant** valeur qui spécifie le GUID d’un type d’objet de fournisseur qui n’est pas défini par la spécification OLE DB. Ce paramètre est obligatoire si *ObjectType* a la valeur **adPermObjProviderSpecific**; sinon, il n’est pas utilisé.  
  
## <a name="remarks"></a>Notes  
 Une erreur se produit si le fournisseur ne prend pas en charge en spécifiant les propriétaires d’objets.  
  
## <a name="applies-to"></a>S'applique à  
 [Catalog, objet (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [GetObjectOwner et SetObjectOwner, méthodes-exemple (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [GetObjectOwner, méthode (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)
