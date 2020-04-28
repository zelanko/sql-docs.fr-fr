---
title: Column, objet (ADOX) | Microsoft Docs
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
ms.openlocfilehash: db2c2dbe6af2a50fc2507a9ade92d83e0502f2ee
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67966910"
---
# <a name="column-object-adox"></a>Column, objet (ADOX)
Représente une colonne d’une table, d’un index ou d’une clé.  
  
## <a name="remarks"></a>Notes  
 Le code suivant crée une nouvelle **colonne**:  
  
 `Dim obj As New Column`  
  
 Avec les propriétés et les collections d’un objet **Column** , vous pouvez :  
  
-   Identifiez la colonne avec la propriété nom de la [propriété (ADOX)](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Spécifiez le type de données de la colonne avec la propriété type de la [propriété (ADOX](../../../ado/reference/adox-api/type-property-key-adox.md) ).  
  
-   Déterminez si la colonne est de longueur fixe ou si elle peut contenir des valeurs NULL avec la propriété [Attributes (ADOX)](../../../ado/reference/adox-api/attributes-property-adox.md) .  
  
-   Spécifiez la taille maximale de la colonne avec la propriété [DefinedSize (ADOX)](../../../ado/reference/adox-api/definedsize-property-adox.md) .  
  
-   Pour les valeurs de données numériques, spécifiez l’échelle avec la propriété [NumericScale, propriété (ADOX)](../../../ado/reference/adox-api/numericscale-property-adox.md) .  
  
-   Pour valeur de données numériques, spécifiez la précision maximale avec la propriété de la [propriété de précision (ADOX)](../../../ado/reference/adox-api/precision-property-adox.md) .  
  
-   Spécifiez l' [objet de catalogue (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md) qui est propriétaire de la colonne avec la propriété [PARENTCATALOG Property (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md) .  
  
-   Pour les colonnes clés, spécifiez le nom de la colonne associée dans la table associée à l’aide de la propriété RelatedColumn, propriété [(ADOX)](../../../ado/reference/adox-api/relatedcolumn-property-adox.md) .  
  
-   Pour les colonnes d’index, spécifiez si l’ordre de tri est croissant ou décroissant avec la propriété [SortOrder (ADOX)](../../../ado/reference/adox-api/sortorder-property-adox.md) .  
  
-   Accédez aux propriétés spécifiques au fournisseur avec la collection de [collections de propriétés (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) .  
  
> [!NOTE]
>  Les propriétés des objets de **colonne** ne sont pas toutes prises en charge par votre fournisseur de données. Une erreur se produit si vous avez défini une valeur pour une propriété que le fournisseur ne prend pas en charge. Pour les nouveaux objets de **colonne** , l’erreur se produit lorsque l’objet est ajouté à la collection. Pour les objets existants, l’erreur se produit lors de la définition de la propriété.  
>   
>  Lors de la création d’objets de **colonne** , l’existence d’une valeur par défaut appropriée pour une propriété facultative ne garantit pas que votre fournisseur prenne en charge la propriété. Pour plus d’informations sur les propriétés prises en charge par votre fournisseur, consultez la documentation de votre fournisseur.  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet Column](../../../ado/reference/adox-api/column-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Columns et tables Append, méthodes, Name, exemple de propriété (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connection Close, méthode, table type, exemple de propriété (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Méthodes Append des clés, type de clé, RelatedColumn, RelatedTable et UpdateRule, exemple de propriétés (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Exemple de code ADOX : NumericScale et Precision, exemple de propriétés (VB)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [ParentCatalog, exemple de propriété (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [SortOrder, exemple de propriété (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Columns, collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
