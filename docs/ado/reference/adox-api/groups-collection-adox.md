---
title: Groupes de Collection (ADOX) | Documents Microsoft
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
- Groups
- User::Groups
- Catalog::Groups
helpviewer_keywords:
- Groups collection [ADOX]
ms.assetid: 09aa7b0a-69d5-4564-80a7-20ad8189670f
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3dfb8a9e2f75fb11caf64b06e34016474d7b9fa7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="groups-collection-adox"></a>Collection de groupes (ADOX)
Contient tous les stockées [groupe](../../../ado/reference/adox-api/group-object-adox.md) objets d’un catalogue ou d’un utilisateur.  
  
## <a name="remarks"></a>Notes  
 Le **groupes** collection d’un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md) représente tous les comptes de groupe du catalogue. Le **groupes** collection pour un [utilisateur](../../../ado/reference/adox-api/user-object-adox.md) représente uniquement le groupe auquel appartient l’utilisateur.  
  
 Le [Append](../../../ado/reference/adox-api/append-method-adox-groups.md) méthode pour un **groupes** collection est unique pour ADOX. Vous pouvez :  
  
-   Ajouter un nouveau groupe de sécurité à la collection avec le **Append** (méthode).  
  
 Les autres propriétés et méthodes sont des collections ADO standard. Vous pouvez :  
  
-   Accéder à un groupe dans la collection avec le [élément](../../../ado/reference/ado-api/item-property-ado.md) propriété.  
  
-   Retourner le nombre de groupes contenus dans la collection avec le [nombre](../../../ado/reference/ado-api/count-property-ado.md) propriété.  
  
-   Supprimer un groupe à partir de la collection avec le [supprimer](../../../ado/reference/adox-api/delete-method-adox-collections.md) (méthode).  
  
-   Mettre à jour les objets dans la collection pour refléter le schéma actuel de la base de données avec le [Actualiser](../../../ado/reference/ado-api/refresh-method-ado.md) (méthode).  
  
> [!NOTE]
>  Avant d’ajouter un **groupe** de l’objet à la **groupes** collection d’un **utilisateur** objet, un **groupe** objet avec le même [nom](../../../ado/reference/adox-api/name-property-adox.md) que celui à ajouter doit déjà exister dans le **groupes** collection de la **catalogue**.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés de Collection de groupes, méthodes et événements](../../../ado/reference/adox-api/groups-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Objet catalogue (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Objet de groupe (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)

