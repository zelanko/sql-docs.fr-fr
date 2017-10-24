---
title: Group, objet (ADOX) | Documents Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Group
helpviewer_keywords:
- group object [ADOX]
ms.assetid: 55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 16aad2cd94a457d3d6efe97326fdbe7e6c06e53d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="group-object-adox"></a>Objet de groupe (ADOX)
Représente un compte de groupe qui dispose des autorisations d’accès au sein d’une base de données sécurisée.  
  
## <a name="remarks"></a>Notes  
 Le [groupes](../../../ado/reference/adox-api/groups-collection-adox.md) collection d’un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md) représente tous les comptes du catalogue groupe. Le **groupes** collection pour un [utilisateur](../../../ado/reference/adox-api/user-object-adox.md) représente uniquement le groupe auquel appartient l’utilisateur.  
  
 Avec les propriétés, les collections et les méthodes d’un **groupe** de l’objet, vous pouvez :  
  
-   Identifier le groupe avec le [nom](../../../ado/reference/adox-api/name-property-adox.md) propriété.  
  
-   Déterminer si un groupe a lire, écrire ou supprimer des autorisations avec la [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md) et [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) méthodes.  
  
-   Accéder aux comptes d’utilisateur ayant des appartenances du groupe avec la [utilisateurs](../../../ado/reference/adox-api/users-collection-adox.md) collection.  
  
-   Accéder aux propriétés spécifiques au fournisseur avec le [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés de l’objet groupe, méthodes et événements](../../../ado/reference/adox-api/group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Collection de groupes (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Collection d’utilisateurs (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)

