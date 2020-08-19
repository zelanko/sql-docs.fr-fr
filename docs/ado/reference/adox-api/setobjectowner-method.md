---
description: SetObjectOwner, méthode
title: Méthode SetObjectOwner | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::SetObjectOwner
- _Catalog::raw_SetObjectOwner
helpviewer_keywords:
- SetObjectOwner method [ADOX]
ms.assetid: e5170a37-9d6e-43db-bfb6-9b6631fa3048
author: rothja
ms.author: jroth
ms.openlocfilehash: 216a01a6a182e7d2fad97a8ed88e6ca09719a33e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439531"
---
# <a name="setobjectowner-method"></a>SetObjectOwner, méthode
Spécifie le propriétaire d’un objet dans un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Catalog.SetObjectOwner ObjectName, ObjectType, OwnerName [,ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ObjectName*  
 Valeur de **chaîne** qui spécifie le nom de l’objet dont le propriétaire doit être spécifié.  
  
 *ObjectType*  
 Valeur de type **long** qui peut être l’une des constantes [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) qui spécifient le type de propriétaire.  
  
 *OwnerName*  
 Valeur de **chaîne** qui spécifie le [nom](../../../ado/reference/adox-api/name-property-adox.md) de l' [utilisateur](../../../ado/reference/adox-api/user-object-adox.md) ou du [groupe](../../../ado/reference/adox-api/group-object-adox.md) propriétaire de l’objet.  
  
 *ObjectTypeId*  
 facultatif. Valeur de **type Variant** qui spécifie le GUID pour un type d’objet fournisseur qui n’est pas défini par la spécification OLE DB. Ce paramètre est obligatoire si *ObjectType* a la valeur **adPermObjProviderSpecific**; dans le cas contraire, il n’est pas utilisé.  
  
## <a name="remarks"></a>Notes  
 Une erreur se produit si le fournisseur ne prend pas en charge la spécification des propriétaires d’objets.  
  
## <a name="applies-to"></a>S'applique à  
 [Catalog, objet (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [GetObjectOwner et SetObjectOwner, exemple de méthodes (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [GetObjectOwner, méthode (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)
