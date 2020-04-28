---
title: GetObjectOwner, méthode (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::raw_GetObjectOwner
- _Catalog::GetObjectOwner
helpviewer_keywords:
- GetObjectOwner method [ADOX]
ms.assetid: 8965adf0-9075-4125-8142-73eb700029c3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ff85491cf7ca30e3f95526aa7043f321a65cccc5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67966278"
---
# <a name="getobjectowner-method-adox"></a>GetObjectOwner, méthode (ADOX)
Retourne le propriétaire d’un objet dans un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Owner = Catalog.GetObjectOwner(ObjectName, ObjectType [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur de **chaîne** qui spécifie le [nom](../../../ado/reference/adox-api/name-property-adox.md) de l' [utilisateur](../../../ado/reference/adox-api/user-object-adox.md) ou du [groupe](../../../ado/reference/adox-api/group-object-adox.md) propriétaire de l’objet.  
  
#### <a name="parameters"></a>Paramètres  
 *ObjectName*  
 Valeur de **chaîne** qui spécifie le nom de l’objet pour lequel le propriétaire doit être retourné.  
  
 *ObjectType*  
 Valeur de type **long** qui peut être l’une des constantes [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) , qui spécifie le type de l’objet pour lequel obtenir le propriétaire.  
  
 *ObjectTypeId*  
 Facultatif. Valeur de **type Variant** qui spécifie le GUID pour un type d’objet fournisseur non défini par la spécification OLE DB. Ce paramètre est obligatoire si *ObjectType* a la valeur **adPermObjProviderSpecific**; dans le cas contraire, il n’est pas utilisé.  
  
## <a name="remarks"></a>Notes  
 Une erreur se produit si le fournisseur ne prend pas en charge le retour de propriétaires d’objets.  
  
## <a name="applies-to"></a>S'applique à  
 [Catalog, objet (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [GetObjectOwner et SetObjectOwner, exemple de méthodes (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [SetObjectOwner, méthode](../../../ado/reference/adox-api/setobjectowner-method.md)
