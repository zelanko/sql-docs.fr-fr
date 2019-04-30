---
title: L’objet utilisateur (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- User
helpviewer_keywords:
- User object [ADOX]
ms.assetid: f68e32ce-ef7c-407d-bdb5-d280947ae0e2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3acdea5ae284b2e9a0ac9c28fe8430a11de8fbd4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281577"
---
# <a name="user-object-adox"></a>User, objet (ADOX)
Représente un compte d’utilisateur qui dispose des autorisations d’accès au sein d’une base de données sécurisée.  
  
## <a name="remarks"></a>Notes  
 Le [utilisateurs](../../../ado/reference/adox-api/users-collection-adox.md) collection d’un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md) représente tous les utilisateurs du catalogue. Le **utilisateurs** collection pour un [groupe](../../../ado/reference/adox-api/group-object-adox.md) représente uniquement les utilisateurs du groupe spécifique.  
  
 Avec les propriétés, les collections et les méthodes d’un **utilisateur** de l’objet, vous pouvez :  
  
-   Identifier l’utilisateur avec le [nom](../../../ado/reference/adox-api/name-property-adox.md) propriété.  
  
-   Modifier le mot de passe pour un utilisateur avec le [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) (méthode).  
  
-   Déterminer si un utilisateur a lire, écrire ou supprimer des autorisations avec le [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md) et [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) méthodes.  
  
-   Accéder aux groupes auxquels appartient un utilisateur avec le [groupes](../../../ado/reference/adox-api/groups-collection-adox.md) collection.  
  
-   Accéder aux propriétés spécifiques au fournisseur avec le [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection.  
  
-   Déterminer le [ParentCatalog](../../../ado/reference/adox-api/parentcatalog-property-adox.md) pour un utilisateur.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements de l’objet User](../../../ado/reference/adox-api/user-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [GetPermissions et SetPermissions, exemples de méthodes (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Collection de groupes (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Users, collection (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
