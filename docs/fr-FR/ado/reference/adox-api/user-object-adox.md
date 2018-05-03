---
title: L’objet utilisateur (ADOX) | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- User
helpviewer_keywords:
- User object [ADOX]
ms.assetid: f68e32ce-ef7c-407d-bdb5-d280947ae0e2
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f261b6b2b4d4fb62f7ac3deee3f555acbce3f992
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="user-object-adox"></a>Objet utilisateur (ADOX)
Représente un compte d’utilisateur qui dispose des autorisations d’accès au sein d’une base de données sécurisée.  
  
## <a name="remarks"></a>Notes  
 Le [utilisateurs](../../../ado/reference/adox-api/users-collection-adox.md) collection d’un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md) représente tous les utilisateurs du catalogue. Le **utilisateurs** collection pour un [groupe](../../../ado/reference/adox-api/group-object-adox.md) représente uniquement les utilisateurs du groupe spécifique.  
  
 Avec les propriétés, les collections et les méthodes d’un **utilisateur** de l’objet, vous pouvez :  
  
-   Identifier l’utilisateur avec le [nom](../../../ado/reference/adox-api/name-property-adox.md) propriété.  
  
-   Modifier le mot de passe pour un utilisateur avec le [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) (méthode).  
  
-   Déterminer si un utilisateur a lire, écrire ou supprimer des autorisations avec la [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md) et [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) méthodes.  
  
-   Accéder aux groupes auxquels appartient un utilisateur avec le [groupes](../../../ado/reference/adox-api/groups-collection-adox.md) collection.  
  
-   Accéder aux propriétés spécifiques au fournisseur avec le [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection.  
  
-   Déterminer le [ParentCatalog](../../../ado/reference/adox-api/parentcatalog-property-adox.md) pour un utilisateur.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements de l’objet User](../../../ado/reference/adox-api/user-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [GetPermissions et SetPermissions, méthodes-exemple (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Collection de groupes (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Users, collection (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
