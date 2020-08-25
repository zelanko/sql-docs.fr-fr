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
ms.openlocfilehash: acefd94f29b030a6bee724686e11023a354d8921
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769408"
---
# <a name="setobjectowner-method"></a>SetObjectOwner, méthode
Spécifie le propriétaire d’un objet dans un [catalogue](./catalog-object-adox.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Catalog.SetObjectOwner ObjectName, ObjectType, OwnerName [,ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ObjectName*  
 Valeur de **chaîne** qui spécifie le nom de l’objet dont le propriétaire doit être spécifié.  
  
 *ObjectType*  
 Valeur de type **long** qui peut être l’une des constantes [ObjectTypeEnum](./objecttypeenum.md) qui spécifient le type de propriétaire.  
  
 *OwnerName*  
 Valeur de **chaîne** qui spécifie le [nom](./name-property-adox.md) de l' [utilisateur](./user-object-adox.md) ou du [groupe](./group-object-adox.md) propriétaire de l’objet.  
  
 *ObjectTypeId*  
 facultatif. Valeur de **type Variant** qui spécifie le GUID pour un type d’objet fournisseur qui n’est pas défini par la spécification OLE DB. Ce paramètre est obligatoire si *ObjectType* a la valeur **adPermObjProviderSpecific**; dans le cas contraire, il n’est pas utilisé.  
  
## <a name="remarks"></a>Notes  
 Une erreur se produit si le fournisseur ne prend pas en charge la spécification des propriétaires d’objets.  
  
## <a name="applies-to"></a>S'applique à  
 [Catalog, objet (ADOX)](./catalog-object-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [GetObjectOwner et SetObjectOwner, exemple de méthodes (VB)](./getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [GetObjectOwner, méthode (ADOX)](./getobjectowner-method-adox.md)