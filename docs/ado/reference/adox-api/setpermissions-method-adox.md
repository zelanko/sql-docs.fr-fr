---
description: SetPermissions, méthode (ADOX)
title: SetPermissions, méthode (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- User25::SetPermissions
- User25::raw_SetPermissions
- _Group25::SetPermissions
- _Group25::raw_SetPermissions
helpviewer_keywords:
- SetPermissions method [ADOX]
ms.assetid: b7f925d7-b05c-4376-bb49-f8d2c17b8b24
author: rothja
ms.author: jroth
ms.openlocfilehash: 3a13e1dc23556888c2d4ee5c013472614b764d57
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769398"
---
# <a name="setpermissions-method-adox"></a>SetPermissions, méthode (ADOX)
Spécifie les autorisations pour un [groupe](./group-object-adox.md) ou un [utilisateur](./user-object-adox.md) sur un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
GroupOrUser.SetPermissions Name, ObjectType, Action, Rights [, Inherit] [, ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Nom*  
 Valeur de **chaîne** qui spécifie le nom de l’objet pour lequel les autorisations doivent être définies.  
  
 *ObjectType*  
 Valeur de type **long** qui peut être l’une des constantes [ObjectTypeEnum](./objecttypeenum.md) , qui spécifie le type de l’objet pour lequel obtenir des autorisations.  
  
 *Action*  
 Valeur de type **long** qui peut être l’une des constantes [ActionEnum](./actionenum.md) qui spécifient le type d’action à effectuer lors de la définition des autorisations.  
  
 *Droits*  
 Valeur de **type long** qui peut être un masque de caractères d’une ou plusieurs des constantes [RightsEnum](./rightsenum.md) , qui indique les droits à définir.  
  
 *Être*  
 facultatif. Valeur de **type long** qui peut être l’une des constantes [InheritTypeEnum](./inherittypeenum.md) , qui spécifie comment les objets hériteront de ces autorisations. La valeur par défaut est **adInheritNone**.  
  
 *ObjectTypeId*  
 facultatif. Valeur de **type Variant** qui spécifie le GUID pour un type d’objet fournisseur qui n’est pas défini par la spécification OLE DB. Ce paramètre est obligatoire si *ObjectType* a la valeur **adPermObjProviderSpecific**; dans le cas contraire, il n’est pas utilisé.  
  
## <a name="remarks"></a>Notes  
 Une erreur se produit si le fournisseur ne prend pas en charge la définition des droits d’accès pour les groupes ou les utilisateurs.  
  
> [!NOTE]
>  Lors de l’appel de **SetPermissions**, la définition des actions sur **adAccessRevoke** remplace tous les paramètres du paramètre *Rights* . Ne définissez pas d' *actions* sur **adAccessRevoke** si vous souhaitez que les droits spécifiés dans le paramètre *Rights* prennent effet.  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [Group, objet (ADOX)](./group-object-adox.md)  
    :::column-end:::
    :::column:::
        [User, objet (ADOX)](./user-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi  
 [GetPermissions et SetPermissions, exemples de méthodes (VB)](./getpermissions-and-setpermissions-methods-example-vb.md)   
 [GetPermissions, méthode (ADOX)](./getpermissions-method-adox.md)   
 [Name, propriété (ADOX)](./name-property-adox.md)