---
title: Groups, collection (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Groups
- User::Groups
- Catalog::Groups
helpviewer_keywords:
- Groups collection [ADOX]
ms.assetid: 09aa7b0a-69d5-4564-80a7-20ad8189670f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e39be3cf32f04a60e554928f66cdc6123322f19c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67966186"
---
# <a name="groups-collection-adox"></a>Groups, collection (ADOX)
Contient tous les objets de [groupe](../../../ado/reference/adox-api/group-object-adox.md) stockés d’un catalogue ou d’un utilisateur.  
  
## <a name="remarks"></a>Notes  
 La collection **groups** d’un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md) représente tous les comptes de groupe du catalogue. La collection **groups** pour un [utilisateur](../../../ado/reference/adox-api/user-object-adox.md) représente uniquement le groupe auquel appartient l’utilisateur.  
  
 La méthode [Append](../../../ado/reference/adox-api/append-method-adox-groups.md) d’une collection **groups** est unique pour ADOX. Vous pouvez :  
  
-   Ajoutez un nouveau groupe de sécurité à la collection à l’aide de la méthode **Append** .  
  
 Les propriétés et les méthodes restantes sont standard pour les collections ADO. Vous pouvez :  
  
-   Accédez à un groupe dans la collection à l’aide de la propriété [Item](../../../ado/reference/ado-api/item-property-ado.md) .  
  
-   Retourne le nombre de groupes contenus dans la collection avec la propriété [Count](../../../ado/reference/ado-api/count-property-ado.md) .  
  
-   Supprimez un groupe de la collection à l’aide de la méthode [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md) .  
  
-   Mettez à jour les objets de la collection pour refléter le schéma de base de données actuel avec la méthode [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) .  
  
> [!NOTE]
>  Avant d’ajouter un objet **groupe** à la collection **groups** d’un objet **User** , un objet **Group** portant le même [nom](../../../ado/reference/adox-api/name-property-adox.md) que celui à ajouter doit déjà exister dans la collection **groups** du **catalogue**.  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de la collection Groups](../../../ado/reference/adox-api/groups-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Catalog, objet (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Group, objet (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)
