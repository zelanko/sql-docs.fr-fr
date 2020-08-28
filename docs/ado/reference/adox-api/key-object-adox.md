---
description: Key, objet (ADOX)
title: Key, objet (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: d8b2f37dd12f7243f2c5fcb8e577dc35e350c6a9
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984050"
---
# <a name="key-object-adox"></a>Key, objet (ADOX)
Représente un champ clé primaire, étrangère ou unique d’une table de base de données.  
  
## <a name="remarks"></a>Notes  
 Le code suivant crée une nouvelle **clé**:  
  
```  
Dim obj As New Key  
```  
  
 Avec les propriétés et les collections d’un objet **clé** , vous pouvez :  
  
-   Identifiez la clé avec la propriété [Name](./name-property-adox.md) .  
  
-   Déterminez si la clé est primaire, étrangère ou unique avec la propriété [type](./type-property-key-adox.md) .  
  
-   Accédez aux colonnes de base de données de la clé avec la collection [Columns](./columns-collection-adox.md) .  
  
-   Spécifiez le nom de la table associée à l’aide de la propriété [RelatedTable](./relatedtable-property-adox.md) .  
  
-   Déterminez l’action effectuée lors de la suppression ou de la mise à jour d’une clé primaire avec les propriétés [DeleteRule](./deleterule-property-adox.md) et [UpdateRule](./updaterule-property-adox.md) .  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet Key](./key-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes Append des clés, type de clé, RelatedColumn, RelatedTable et UpdateRule, exemple de propriétés (VB)](./keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Columns, collection (ADOX)](./columns-collection-adox.md)   
 [Keys, collection (ADOX)](./keys-collection-adox.md)