---
title: Append, méthode (utilisateurs ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Users::raw_Append
- Users::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: b80bc5d5-78ca-4f75-956b-2ac658029cc7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 99a21cd5dd32af9e84877865cfe7c0fc92f6c087
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67967228"
---
# <a name="append-method-adox-users"></a>Append, méthode (utilisateurs ADOX)
Ajoute un nouvel objet [utilisateur](../../../ado/reference/adox-api/user-object-adox.md) à la collection [Users](../../../ado/reference/adox-api/users-collection-adox.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Users.Append User[,Password]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Utilisateur*  
 Valeur de **type Variant** qui contient l’objet **utilisateur** à ajouter ou le nom de l’utilisateur à créer et à ajouter.  
  
 *Mot de passe*  
 Facultatif. Valeur de **chaîne** qui contient le mot de passe de l’utilisateur. Le paramètre de *mot de passe* correspond à la valeur spécifiée par la méthode [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) d’un objet **utilisateur** .  
  
## <a name="remarks"></a>Notes  
 La collection d' **utilisateurs** d’un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md) représente tous les utilisateurs du catalogue. Le regroupement **utilisateurs** pour un [groupe](../../../ado/reference/adox-api/group-object-adox.md) représente uniquement les utilisateurs qui ont une appartenance au groupe spécifique.  
  
 Une erreur se produit si le fournisseur ne prend pas en charge la création d’utilisateurs.  
  
> [!NOTE]
>  Avant d’ajouter un objet **utilisateur** à la collection **Users** d’un objet **Group** , un objet **utilisateur** portant le même [nom](../../../ado/reference/adox-api/name-property-adox.md) que celui à ajouter doit déjà exister dans la collection **Users** du **catalogue**.  
  
## <a name="applies-to"></a>S'applique à  
 [Users, collection (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Groups and Users Append, ChangePassword, exemple de méthodes (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)   
 [Append, méthode (colonnes ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append, méthode (groupes ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append, méthode (Index ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append, méthode (clés ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append, méthode (procédures ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append, méthode (Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append, méthode (vues ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
