---
title: "La clé d’objet (ADOX) | Documents Microsoft"
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
- Key
helpviewer_keywords:
- Key object [ADOX]
ms.assetid: 55f116fe-4d56-4892-bffe-0cdd6fc727c9
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7d05a52614694bc9464c609ab4f4ed0965f3b81e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

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
  
-   [Propriétés de l’objet clé, méthodes et événements](../../../ado/reference/adox-api/key-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Keys Append, méthode, Type de clé, RelatedColumn, RelatedTable et UpdateRule exemple (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Collection de colonnes (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Collection de clés (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)

