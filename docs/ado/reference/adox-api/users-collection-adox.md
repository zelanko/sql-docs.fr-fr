---
title: "Collection d’utilisateurs (ADOX) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Group::Users
- Users
- Catalog::Users
helpviewer_keywords:
- Users collection [ADOX]
ms.assetid: 0a30fa74-6f10-4410-bd70-882e7c43cd46
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b9c19df96e66927c6dc5092cd0584f071a3d3b40
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="users-collection-adox"></a>Collection d’utilisateurs (ADOX)
Contient tous les stockées [utilisateur](../../../ado/reference/adox-api/user-object-adox.md) les objets d’un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md) ou [groupe](../../../ado/reference/adox-api/group-object-adox.md).  
  
## <a name="remarks"></a>Notes  
 Le **utilisateurs** collection d’un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md) représente tous les utilisateurs du catalogue. Le **utilisateurs** collection pour un [groupe](../../../ado/reference/adox-api/group-object-adox.md) représente uniquement les utilisateurs qui appartiennent à ce groupe.  
  
 Le [Append](../../../ado/reference/adox-api/append-method-adox-users.md) méthode pour un **utilisateurs** collection est unique pour ADOX. Vous pouvez :  
  
-   Ajouter un nouvel utilisateur à la collection à l’aide de la **Append** (méthode).  
  
 Les autres propriétés et méthodes sont des collections ADO standard. Vous pouvez :  
  
-   Accéder à un utilisateur dans la collection avec le [élément](../../../ado/reference/ado-api/item-property-ado.md) propriété.  
  
-   Retourner le nombre d’utilisateurs contenus dans la collection avec le [nombre](../../../ado/reference/ado-api/count-property-ado.md) propriété.  
  
-   Supprimer un utilisateur de la collection avec le [supprimer](../../../ado/reference/adox-api/delete-method-adox-collections.md) (méthode).  
  
-   Mettre à jour les objets dans la collection pour refléter le schéma de la base de données en cours avec le [Actualiser](../../../ado/reference/ado-api/refresh-method-ado.md) (méthode).  
  
> [!NOTE]
>  Avant d’ajouter un **utilisateur** de l’objet à la **utilisateurs** collection d’un **groupe** objet, un **utilisateur** objet avec le même [nom](../../../ado/reference/adox-api/name-property-adox.md) que celui à ajouter doit déjà exister dans le **utilisateurs** collection de la **catalogue**.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés de Collection d’utilisateurs, des méthodes et des événements](../../../ado/reference/adox-api/users-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [GetPermissions et SetPermissions, méthodes-exemple (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Objet catalogue (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Objet utilisateur (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)

