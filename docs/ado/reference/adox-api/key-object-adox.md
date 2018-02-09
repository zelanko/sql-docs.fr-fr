---
title: "La clé d’objet (ADOX) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
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
- Key
helpviewer_keywords:
- Key object [ADOX]
ms.assetid: 55f116fe-4d56-4892-bffe-0cdd6fc727c9
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9a1f971c07571c54cc74e4a750fde505e60af2f2
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="key-object-adox"></a>Objet clé (ADOX)
Représente un champ de clé unique, primaire ou étrangère d’une table de base de données.  
  
## <a name="remarks"></a>Notes  
 Le code suivant crée un nouveau **clé**:  
  
```  
Dim obj As New Key  
```  
  
 Avec les propriétés et les collections d’un **clé** de l’objet, vous pouvez :  
  
-   Identifier la clé avec la [nom](../../../ado/reference/adox-api/name-property-adox.md) propriété.  
  
-   Déterminer si la clé est primaire, étrangère ou unique avec le [Type](../../../ado/reference/adox-api/type-property-key-adox.md) propriété.  
  
-   Accéder aux colonnes de base de données de la clé avec la [colonnes](../../../ado/reference/adox-api/columns-collection-adox.md) collection.  
  
-   Spécifiez le nom de la table en relation avec la [RelatedTable](../../../ado/reference/adox-api/relatedtable-property-adox.md) propriété.  
  
-   Déterminer l’action effectuée sur la suppression ou la mise à jour d’une clé primaire avec les [DeleteRule](../../../ado/reference/adox-api/deleterule-property-adox.md) et [UpdateRule](../../../ado/reference/adox-api/updaterule-property-adox.md) propriétés.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements de l’objet Key](../../../ado/reference/adox-api/key-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Keys Append, méthode, Type de clé, RelatedColumn, RelatedTable et UpdateRule exemple (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Collection de colonnes (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Keys, collection (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)
