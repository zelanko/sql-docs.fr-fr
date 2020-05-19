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
author: rothja
ms.author: jroth
ms.openlocfilehash: 840484cbfcb1feeb56022835b6c1b3157101edb8
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763880"
---
# <a name="index-object-adox"></a>Index, objet (ADOX)
Représente un index à partir d’une table de base de données.  
  
## <a name="remarks"></a>Remarques  
 Le code suivant crée un nouvel **index**:  
  
```  
Dim obj As New Index  
```  
  
 Avec les propriétés et les collections d’un objet **index** , vous pouvez :  
  
-   Identifiez l’index avec la propriété [Name](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Accédez aux colonnes de base de données de l’index avec la collection [Columns](../../../ado/reference/adox-api/columns-collection-adox.md) .  
  
-   Spécifiez si les clés d’index doivent être uniques avec la propriété [unique](../../../ado/reference/adox-api/unique-property-adox.md) .  
  
-   Spécifie si l’index est la clé primaire d’une table avec la propriété [PrimaryKey](../../../ado/reference/adox-api/primarykey-property-adox.md) .  
  
-   Spécifiez si les enregistrements qui ont des valeurs NULL dans leurs champs d’index ont des entrées d’index avec la propriété [IndexNulls](../../../ado/reference/adox-api/indexnulls-property-adox.md) .  
  
-   Spécifiez si l’index est ordonné en clusters avec la propriété [Clustered](../../../ado/reference/adox-api/clustered-property-adox.md) .  
  
-   Accédez aux propriétés d’index spécifiques au fournisseur avec la collection [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) .  
  
> [!NOTE]
>  Une erreur se produit lors de l’ajout d’une [colonne](../../../ado/reference/adox-api/column-object-adox.md) à la collection **Columns** d’un **index** si la **colonne** n’existe pas dans un objet [table](../../../ado/reference/adox-api/table-object-adox.md) déjà ajouté à la collection [tables](../../../ado/reference/adox-api/tables-collection-adox.md) .  
  
> [!NOTE]
>  Votre fournisseur de données peut ne pas prendre en charge toutes les propriétés des objets **index** . Une erreur se produit si vous avez défini une valeur pour une propriété qui n’est pas prise en charge par le fournisseur. Pour les nouveaux objets **index** , l’erreur se produit lorsque l’objet est ajouté à la collection. Pour les objets existants, l’erreur se produit lors de la définition de la propriété.  
  
> [!NOTE]
>  Lors de la création d’objets **index** , l’existence d’une valeur par défaut appropriée pour une propriété facultative ne garantit pas que votre fournisseur prenne en charge la propriété. Pour plus d’informations sur les propriétés prises en charge par votre fournisseur, consultez la documentation de votre fournisseur.  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet Index](../../../ado/reference/adox-api/index-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Indexes, exemple de méthode Append (VB)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [IndexNulls, exemple de propriété (VB)](../../../ado/reference/adox-api/indexnulls-property-example-vb.md)   
 [PrimaryKey et unique, exemple de propriétés (VB)](../../../ado/reference/adox-api/primarykey-and-unique-properties-example-vb.md)   
 [SortOrder, exemple de propriété (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Columns, collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Indexes, collection (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
