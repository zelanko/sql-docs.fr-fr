---
description: Group, objet (ADOX)
title: Group, objet (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 21514bbcbe91e1320a4a2806e545d5f7b40df8d3
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984430"
---
# <a name="group-object-adox"></a>Group, objet (ADOX)
Représente un compte de groupe qui dispose d’autorisations d’accès au sein d’une base de données sécurisée.  
  
## <a name="remarks"></a>Notes  
 La collection [groups](./groups-collection-adox.md) d’un [catalogue](./catalog-object-adox.md) représente tous les comptes de groupe du catalogue. La collection **groups** pour un [utilisateur](./user-object-adox.md) représente uniquement le groupe auquel appartient l’utilisateur.  
  
 Avec les propriétés, collections et méthodes d’un objet **Group** , vous pouvez :  
  
-   Identifiez le groupe à l’aide de la propriété [Name](./name-property-adox.md) .  
  
-   Déterminez si un groupe dispose des autorisations de lecture, d’écriture ou de suppression avec les méthodes [GetPermissions](./getpermissions-method-adox.md) et [SetPermissions](./setpermissions-method-adox.md) .  
  
-   Accédez aux comptes d’utilisateur qui ont des appartenances au groupe avec la collection [Users](./users-collection-adox.md) .  
  
-   Accédez aux propriétés spécifiques au fournisseur avec la collection [Properties](../ado-api/properties-collection-ado.md) .  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet Group](./group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Groups, collection (ADOX)](./groups-collection-adox.md)   
 [Users, collection (ADOX)](./users-collection-adox.md)