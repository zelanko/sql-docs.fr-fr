---
title: Les utilisateurs, Collection (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Group::Users
- Users
- Catalog::Users
helpviewer_keywords:
- Users collection [ADOX]
ms.assetid: 0a30fa74-6f10-4410-bd70-882e7c43cd46
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8dc465261748c1efd340e78ddc2f3e12d601e931
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281620"
---
# <a name="users-collection-adox"></a>Users, collection (ADOX)
Contient tous les stockées [utilisateur](../../../ado/reference/adox-api/user-object-adox.md) objets d’un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md) ou [groupe](../../../ado/reference/adox-api/group-object-adox.md).  
  
## <a name="remarks"></a>Notes  
 Le **utilisateurs** collection d’un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md) représente tous les utilisateurs du catalogue. Le **utilisateurs** collection pour un [groupe](../../../ado/reference/adox-api/group-object-adox.md) représente uniquement les utilisateurs qui ont une appartenance au groupe spécifique.  
  
 Le [Append](../../../ado/reference/adox-api/append-method-adox-users.md) méthode pour un **utilisateurs** collection est unique pour ADOX. Vous pouvez :  
  
-   Ajouter un nouvel utilisateur à la collection à l’aide de la **Append** (méthode).  
  
 Les propriétés et les méthodes restantes sont des collections ADO standard. Vous pouvez :  
  
-   Accéder à un utilisateur dans la collection avec le [élément](../../../ado/reference/ado-api/item-property-ado.md) propriété.  
  
-   Retourner le nombre d’utilisateurs contenus dans la collection avec le [nombre](../../../ado/reference/ado-api/count-property-ado.md) propriété.  
  
-   Supprimer un utilisateur de la collection avec le [supprimer](../../../ado/reference/adox-api/delete-method-adox-collections.md) (méthode).  
  
-   Mettre à jour les objets dans la collection afin de refléter le schéma de la base de données actuelle avec le [Actualiser](../../../ado/reference/ado-api/refresh-method-ado.md) (méthode).  
  
> [!NOTE]
>  Avant d’ajouter un **utilisateur** de l’objet à la **utilisateurs** collection d’un **groupe** objet, un **utilisateur** objet comportant le même [nom ](../../../ado/reference/adox-api/name-property-adox.md) que celui à ajouter doit déjà exister dans le **utilisateurs** collection de la **catalogue**.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements de la collection Users](../../../ado/reference/adox-api/users-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [GetPermissions et SetPermissions, exemples de méthodes (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Catalog, objet (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [User, objet (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)
