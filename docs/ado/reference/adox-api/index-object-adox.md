---
title: Index, objet (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Index
helpviewer_keywords:
- Index object [ADOX]
ms.assetid: 6b9578c0-bc94-46b9-b801-c18e14b04b31
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b6fd63de0b6147b86aa0d6b548669c56aefdcf20
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66706716"
---
# <a name="index-object-adox"></a>Index, objet (ADOX)
Représente un index à partir d’une table de base de données.  
  
## <a name="remarks"></a>Notes  
 Le code suivant crée un nouveau **Index**:  
  
```  
Dim obj As New Index  
```  
  
 Avec les propriétés et les collections d’un **Index** de l’objet, vous pouvez :  
  
-   Identifier l’index avec la [nom](../../../ado/reference/adox-api/name-property-adox.md) propriété.  
  
-   Accéder aux colonnes de base de données de l’index avec la [colonnes](../../../ado/reference/adox-api/columns-collection-adox.md) collection.  
  
-   Spécifiez si les clés d’index doivent être uniques dans le [Unique](../../../ado/reference/adox-api/unique-property-adox.md) propriété.  
  
-   Spécifiez si l’index est la clé primaire pour une table avec la [PrimaryKey](../../../ado/reference/adox-api/primarykey-property-adox.md) propriété.  
  
-   Spécifiez si les enregistrements qui ont des valeurs null dans les champs d’index ont des entrées d’index avec la [IndexNulls](../../../ado/reference/adox-api/indexnulls-property-adox.md) propriété.  
  
-   Spécifiez si l’index est groupé avec le [Clustered](../../../ado/reference/adox-api/clustered-property-adox.md) propriété.  
  
-   Accéder aux propriétés spécifiques au fournisseur index avec la [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection.  
  
> [!NOTE]
>  Une erreur se produit lors de l’ajout un [colonne](../../../ado/reference/adox-api/column-object-adox.md) à la **colonnes** collection d’un **Index** si le **colonne** n’existe pas dans un [Table](../../../ado/reference/adox-api/table-object-adox.md) objet déjà ajouté à la [Tables](../../../ado/reference/adox-api/tables-collection-adox.md) collection.  
  
> [!NOTE]
>  Votre fournisseur de données, n’acceptent pas toutes les propriétés de **Index** objets. Une erreur se produit si vous avez défini une valeur pour une propriété qui n’est pas pris en charge par le fournisseur. Pour les nouveaux **Index** objets, l’erreur se produit lorsque l’objet est ajouté à la collection. Pour les objets existants, l’erreur se produit lors de la définition de la propriété.  
  
> [!NOTE]
>  Lors de la création **Index** objets, l’existence d’une valeur par défaut appropriée pour une propriété facultative ne garantit pas que votre fournisseur prend en charge la propriété. Pour plus d’informations sur les propriétés de votre fournisseur prend en charge, consultez la documentation du fournisseur.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements de l’objet Index](../../../ado/reference/adox-api/index-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Indexes, exemple (VB) de la méthode Append](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [IndexNulls, propriété-Exemple (VB)](../../../ado/reference/adox-api/indexnulls-property-example-vb.md)   
 [PrimaryKey et Unique de propriétés, exemple (VB)](../../../ado/reference/adox-api/primarykey-and-unique-properties-example-vb.md)   
 [Propriété SortOrder, exemple (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Columns, Collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Indexes, Collection (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
