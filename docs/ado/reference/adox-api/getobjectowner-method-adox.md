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
manager: jroth
ms.openlocfilehash: a3b5ab8c21ee02f646bf4b8e4f4941fafd6edfde
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66712131"
---
# <a name="getobjectowner-method-adox"></a>GetObjectOwner, méthode (ADOX)
Retourne le propriétaire d’un objet dans un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Owner = Catalog.GetObjectOwner(ObjectName, ObjectType [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un **chaîne** valeur qui spécifie le [nom](../../../ado/reference/adox-api/name-property-adox.md) de la [utilisateur](../../../ado/reference/adox-api/user-object-adox.md) ou [groupe](../../../ado/reference/adox-api/group-object-adox.md) qui possède l’objet.  
  
#### <a name="parameters"></a>Paramètres  
 *ObjectName*  
 Un **chaîne** valeur qui spécifie le nom de l’objet pour lequel retourner le propriétaire.  
  
 *ObjectType*  
 Un **Long** valeur qui peut être une de le [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) constantes, qui spécifie le type de l’objet pour lequel obtenir le propriétaire.  
  
 *ObjectTypeId*  
 Facultatif. Un **Variant** valeur qui spécifie le GUID d’un type d’objet de fournisseur non défini par la spécification OLE DB. Ce paramètre est obligatoire si *ObjectType* a la valeur **adPermObjProviderSpecific**; sinon, il n’est pas utilisé.  
  
## <a name="remarks"></a>Notes  
 Une erreur se produit si le fournisseur ne prend pas en charge le retour propriétaires d’objets.  
  
## <a name="applies-to"></a>S'applique à  
 [Catalog, objet (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [GetObjectOwner et SetObjectOwner, exemples de méthodes (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [SetObjectOwner, méthode (ADOX)](../../../ado/reference/adox-api/setobjectowner-method.md)
