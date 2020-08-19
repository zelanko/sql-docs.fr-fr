---
description: User, objet (ADOX)
title: User, objet (ADOX) | Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 3c81caba440367712e5743bc1e224bd3968a2990
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439391"
---
# <a name="user-object-adox"></a>User, objet (ADOX)
Représente un compte d’utilisateur qui dispose d’autorisations d’accès au sein d’une base de données sécurisée.  
  
## <a name="remarks"></a>Notes  
 La collection d' [utilisateurs](../../../ado/reference/adox-api/users-collection-adox.md) d’un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md) représente tous les utilisateurs du catalogue. La collection d' **utilisateurs** d’un [groupe](../../../ado/reference/adox-api/group-object-adox.md) représente uniquement les utilisateurs du groupe spécifique.  
  
 Avec les propriétés, collections et méthodes d’un objet **utilisateur** , vous pouvez :  
  
-   Identifiez l’utilisateur à l’aide de la propriété [Name](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Modifiez le mot de passe d’un utilisateur à l’aide de la méthode [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) .  
  
-   Déterminez si un utilisateur dispose d’autorisations de lecture, d’écriture ou de suppression avec les méthodes [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md) et [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) .  
  
-   Accédez aux groupes auxquels appartient un utilisateur avec la collection de [groupes](../../../ado/reference/adox-api/groups-collection-adox.md) .  
  
-   Accédez aux propriétés spécifiques au fournisseur avec la collection [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) .  
  
-   Déterminez le [ParentCatalog](../../../ado/reference/adox-api/parentcatalog-property-adox.md) d’un utilisateur.  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet User](../../../ado/reference/adox-api/user-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [GetPermissions et SetPermissions, exemples de méthodes (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Groups, collection (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Users, collection (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
