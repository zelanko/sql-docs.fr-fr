---
description: Table, objet (ADOX)
title: Table, objet (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Table
helpviewer_keywords:
- Table object [ADOX]
ms.assetid: a6d74000-0828-49ba-850a-63da865f8802
author: rothja
ms.author: jroth
ms.openlocfilehash: c9bbf6a33eeb76f406a6fd6dc87ef591a3d4f12a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439481"
---
# <a name="table-object-adox"></a>Table, objet (ADOX)
Représente une table de base de données, notamment des colonnes, des index et des clés.  
  
## <a name="remarks"></a>Notes  
 Le code suivant crée une nouvelle **table**:  
  
```  
Dim obj As New Table  
```  
  
 Avec les propriétés et les collections d’un objet **table** , vous pouvez :  
  
-   Identifiez la table à l’aide de la propriété nom de la [propriété (ADOX)](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Déterminez le type de table avec la propriété [type (table) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md) .  
  
-   Accédez aux colonnes de base de données de la table à l’aide de la collection [Columns collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md) .  
  
-   Accédez aux index de la table à l’aide de la [collection d’index (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md).  
  
-   Accédez aux clés de la table à l’aide de la [collection Keys (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md).  
  
-   Spécifiez le catalogue qui possède la table avec la propriété [ParentCatalog Property (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md) .  
  
-   Retournez les informations de date avec les propriétés [DateCreated Property (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md) et [DATEMODIFIED Property (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md) .  
  
-   Accédez aux propriétés de table spécifiques au fournisseur à l’aide de la collection de [Collections Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) .  
  
> [!NOTE]
>  Votre fournisseur de données peut ne pas prendre en charge toutes les propriétés des objets de **table** . Une erreur se produit si vous avez défini une valeur pour une propriété que le fournisseur ne prend pas en charge. Pour les nouveaux objets de **table** , l’erreur se produit lorsque l’objet est ajouté à la collection. Pour les objets existants, l’erreur se produit lors de la définition de la propriété.  
>   
>  Lors de la création d’objets **table** , l’existence d’une valeur par défaut appropriée pour une propriété facultative ne garantit pas que votre fournisseur prenne en charge la propriété. Pour plus d’informations sur les propriétés prises en charge par votre fournisseur, consultez la documentation de votre fournisseur.  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet Table](../../../ado/reference/adox-api/table-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de propriété ActiveConnection de Catalog (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Columns et tables Append, méthodes, Name, exemple de propriété (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connection Close, méthode, table type, exemple de propriété (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Méthodes Append des clés, type de clé, RelatedColumn, RelatedTable et UpdateRule, exemple de propriétés (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog, exemple de propriété (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Columns, collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Indexes, collection (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [Keys, collection (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Tables, collection (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)
