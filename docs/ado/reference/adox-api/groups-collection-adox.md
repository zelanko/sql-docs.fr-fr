---
description: Groups, collection (ADOX)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 5edecbbfebeea82d28f97bc31d15e04bf28c576a
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88770328"
---
# <a name="groups-collection-adox"></a>Groups, collection (ADOX)
Contient tous les objets de [groupe](./group-object-adox.md) stockés d’un catalogue ou d’un utilisateur.  
  
## <a name="remarks"></a>Notes  
 La collection **groups** d’un [catalogue](./catalog-object-adox.md) représente tous les comptes de groupe du catalogue. La collection **groups** pour un [utilisateur](./user-object-adox.md) représente uniquement le groupe auquel appartient l’utilisateur.  
  
 La méthode [Append](./append-method-adox-groups.md) d’une collection **groups** est unique pour ADOX. Vous pouvez :  
  
-   Ajoutez un nouveau groupe de sécurité à la collection à l’aide de la méthode **Append** .  
  
 Les propriétés et les méthodes restantes sont standard pour les collections ADO. Vous pouvez :  
  
-   Accédez à un groupe dans la collection à l’aide de la propriété [Item](../ado-api/item-property-ado.md) .  
  
-   Retourne le nombre de groupes contenus dans la collection avec la propriété [Count](../ado-api/count-property-ado.md) .  
  
-   Supprimez un groupe de la collection à l’aide de la méthode [Delete](./delete-method-adox-collections.md) .  
  
-   Mettez à jour les objets de la collection pour refléter le schéma de base de données actuel avec la méthode [Refresh](../ado-api/refresh-method-ado.md) .  
  
> [!NOTE]
>  Avant d’ajouter un objet **groupe** à la collection **groups** d’un objet **User** , un objet **Group** portant le même [nom](./name-property-adox.md) que celui à ajouter doit déjà exister dans la collection **groups** du **catalogue**.  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de la collection Groups](./groups-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Catalog, objet (ADOX)](./catalog-object-adox.md)   
 [Group, objet (ADOX)](./group-object-adox.md)