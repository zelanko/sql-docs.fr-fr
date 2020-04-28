---
title: Group, objet (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Group
helpviewer_keywords:
- group object [ADOX]
ms.assetid: 55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b4b3de5f445ddd09bf7d069b0b93d82c6f8de978
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67966214"
---
# <a name="group-object-adox"></a>Group, objet (ADOX)
Représente un compte de groupe qui dispose d’autorisations d’accès au sein d’une base de données sécurisée.  
  
## <a name="remarks"></a>Notes  
 La collection [groups](../../../ado/reference/adox-api/groups-collection-adox.md) d’un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md) représente tous les comptes de groupe du catalogue. La collection **groups** pour un [utilisateur](../../../ado/reference/adox-api/user-object-adox.md) représente uniquement le groupe auquel appartient l’utilisateur.  
  
 Avec les propriétés, collections et méthodes d’un objet **Group** , vous pouvez :  
  
-   Identifiez le groupe à l’aide de la propriété [Name](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Déterminez si un groupe dispose des autorisations de lecture, d’écriture ou de suppression avec les méthodes [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md) et [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) .  
  
-   Accédez aux comptes d’utilisateur qui ont des appartenances au groupe avec la collection [Users](../../../ado/reference/adox-api/users-collection-adox.md) .  
  
-   Accédez aux propriétés spécifiques au fournisseur avec la collection [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) .  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet Group](../../../ado/reference/adox-api/group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Groups, collection (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Users, collection (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
