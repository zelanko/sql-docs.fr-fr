---
title: Objet de colonne (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Column
helpviewer_keywords:
- Column object [ADOX]
ms.assetid: 6e772783-1bc8-4ea7-94b2-7d7a52ea5c47
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7dcec7e665fec8ea1eb1e1dff8d08bb59ee92133
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66708015"
---
# <a name="column-object-adox"></a>Column, objet (ADOX)
Représente une colonne de table, d’index ou de clé.  
  
## <a name="remarks"></a>Notes  
 Le code suivant crée un nouveau **colonne**:  
  
 `Dim obj As New Column`  
  
 Avec les propriétés et les collections d’un **colonne** de l’objet, vous pouvez :  
  
-   Identifier la colonne avec le [nom de propriété (ADOX)](../../../ado/reference/adox-api/name-property-adox.md) propriété.  
  
-   Spécifier le type de données de la colonne avec le [Type, propriété (clé) (ADOX)](../../../ado/reference/adox-api/type-property-key-adox.md) propriété.  
  
-   Déterminer si la colonne est de longueur fixe ou si elle peut contenir des valeurs null avec le [attributs de propriété (ADOX)](../../../ado/reference/adox-api/attributes-property-adox.md) propriété.  
  
-   Spécifiez la taille maximale de la colonne avec le [DefinedSize propriété (ADOX)](../../../ado/reference/adox-api/definedsize-property-adox.md) propriété.  
  
-   Pour les valeurs de données numériques, spécifiez l’échelle avec le [NumericScale propriété (ADOX)](../../../ado/reference/adox-api/numericscale-property-adox.md) propriété.  
  
-   Valeur des données numériques, spécifier la précision maximale avec les [précision propriété (ADOX)](../../../ado/reference/adox-api/precision-property-adox.md) propriété.  
  
-   Spécifiez le [catalogue objet (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md) qui possède la colonne avec le [ParentCatalog propriété (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md) propriété.  
  
-   Pour les colonnes clés, spécifiez le nom de la colonne associée dans la table associée avec le [RelatedColumn propriété (ADOX)](../../../ado/reference/adox-api/relatedcolumn-property-adox.md) propriété.  
  
-   Pour les colonnes d’index, spécifier si l’ordre de tri est croissant ou décroissant avec le [SortOrder propriété (ADOX)](../../../ado/reference/adox-api/sortorder-property-adox.md) propriété.  
  
-   Accéder aux propriétés spécifiques au fournisseur avec le [propriétés de Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) collection.  
  
> [!NOTE]
>  Pas toutes les propriétés de **colonne** objets peuvent être pris en charge par votre fournisseur de données. Une erreur se produit si vous avez défini une valeur pour une propriété qui le fournisseur ne prend pas en charge. Pour les nouveaux **colonne** objets, l’erreur se produit lorsque l’objet est ajouté à la collection. Pour les objets existants, l’erreur se produit lors de la définition de la propriété.  
>   
>  Lors de la création **colonne** objets, l’existence d’une valeur par défaut appropriée pour une propriété facultative ne garantit pas que votre fournisseur prend en charge la propriété. Pour plus d’informations sur les propriétés de votre fournisseur prend en charge, consultez la documentation du fournisseur.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements de l’objet Column](../../../ado/reference/adox-api/column-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et colonnes ajouter des méthodes, exemple de nom de propriété (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Méthode Close de connexion, exemple de propriété de Type de Table (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Keys Append, méthode, Type de clé, RelatedColumn, RelatedTable et UpdateRule, exemple de propriétés (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Exemple de Code ADOX : NumericScale et Precision, propriétés, exemple (VB)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [ParentCatalog, propriété-Exemple (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Propriété SortOrder, exemple (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Columns, Collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
