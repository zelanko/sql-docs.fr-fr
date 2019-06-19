---
title: Clé d’objet (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Key
helpviewer_keywords:
- Key object [ADOX]
ms.assetid: 55f116fe-4d56-4892-bffe-0cdd6fc727c9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6dbbb81d53755032725ad71ff9bbf49b9beb2f1c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66706475"
---
# <a name="key-object-adox"></a>Key, objet (ADOX)
Représente un champ de clé primaire, étrangère ou unique à partir d’une table de base de données.  
  
## <a name="remarks"></a>Notes  
 Le code suivant crée un nouveau **clé**:  
  
```  
Dim obj As New Key  
```  
  
 Avec les propriétés et les collections d’un **clé** de l’objet, vous pouvez :  
  
-   Identifier la clé avec la [nom](../../../ado/reference/adox-api/name-property-adox.md) propriété.  
  
-   Déterminer si la clé est primaire, étrangère ou unique avec le [Type](../../../ado/reference/adox-api/type-property-key-adox.md) propriété.  
  
-   Accéder aux colonnes de base de données de la clé avec la [colonnes](../../../ado/reference/adox-api/columns-collection-adox.md) collection.  
  
-   Spécifiez le nom de la table associée avec le [RelatedTable](../../../ado/reference/adox-api/relatedtable-property-adox.md) propriété.  
  
-   Déterminer l’action effectuée sur la suppression ou de mise à jour d’une clé primaire et la [DeleteRule](../../../ado/reference/adox-api/deleterule-property-adox.md) et [UpdateRule](../../../ado/reference/adox-api/updaterule-property-adox.md) propriétés.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements de l’objet Key](../../../ado/reference/adox-api/key-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Keys Append, méthode, Type de clé, RelatedColumn, RelatedTable et UpdateRule, exemple de propriétés (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Columns, Collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Keys, collection (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)
