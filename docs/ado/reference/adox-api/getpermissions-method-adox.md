---
title: GetPermissions, méthode (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User25::GetPermissions
- _Group25::raw_GetPermissions
- _Group25::GetPermissions
- _User25::raw_GetPermissions
helpviewer_keywords:
- GetPermissions method [ADOX]
ms.assetid: df201c1f-c76a-465d-98f0-83b7fc36e6e3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5f5b2a5170b499f5e88d4caac4822d2998691eea
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67966224"
---
# <a name="getpermissions-method-adox"></a>GetPermissions, méthode (ADOX)
Retourne les autorisations pour un [groupe](../../../ado/reference/adox-api/group-object-adox.md) ou un [utilisateur](../../../ado/reference/adox-api/user-object-adox.md) sur un objet ou un conteneur d’objets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ReturnValue=GroupOrUser.GetPermissions(Name, ObjectType    [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur de **type long** qui spécifie un masque de caractères contenant les autorisations dont dispose le groupe ou l’utilisateur sur l’objet. Cette valeur peut être une ou plusieurs des constantes [RightsEnum](../../../ado/reference/adox-api/rightsenum.md) .  
  
#### <a name="parameters"></a>Paramètres  
 *Nom*  
 Valeur de **type Variant** qui spécifie le nom de l’objet pour lequel les autorisations doivent être définies. Affectez une valeur null au *nom* si vous souhaitez obtenir les autorisations pour le conteneur d’objets.  
  
 *ObjectType*  
 Valeur de type **long** qui peut être l’une des constantes [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) , qui spécifie le type de l’objet pour lequel obtenir des autorisations.  
  
 *ObjectTypeId*  
 Facultatif. Valeur de **type Variant** qui spécifie le GUID pour un type d’objet fournisseur non défini par la spécification OLE DB. Ce paramètre est obligatoire si *ObjectType* a la valeur **adPermObjProviderSpecific**; dans le cas contraire, il n’est pas utilisé.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Group, objet (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[User, objet (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [GetPermissions et SetPermissions, exemples de méthodes (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Name, propriété (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)   
 [SetPermissions, méthode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
