---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f5af59dbc50f6e1a2cd95cbdf99874d860eceeb1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622337"
---
# <a name="table-object-adox"></a>Table, objet (ADOX)
Représente une table de base de données, y compris les colonnes, les index et les clés.  
  
## <a name="remarks"></a>Notes  
 Le code suivant crée un nouveau **Table**:  
  
```  
Dim obj As New Table  
```  
  
 Avec les propriétés et les collections d’un **Table** de l’objet, vous pouvez :  
  
-   Identifiez la table avec la [nom de propriété (ADOX)](../../../ado/reference/adox-api/name-property-adox.md) propriété.  
  
-   Déterminer le type de table avec la [Type, propriété (Table) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md) propriété.  
  
-   Accéder aux colonnes de base de données de la table contenant la [colonnes Collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md) collection.  
  
-   Accéder à l’index de la table contenant la [index de Collection (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md).  
  
-   Accéder aux clés de la table contenant la [clés de Collection (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md).  
  
-   Spécifier le catalogue auquel appartient la table avec la [ParentCatalog propriété (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md) propriété.  
  
-   Retourner des informations de date avec la [DateCreated propriété (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md) et [DateModified propriété (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md) propriétés.  
  
-   Accéder aux propriétés spécifiques au fournisseur table avec la [propriétés de Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) collection.  
  
> [!NOTE]
>  Votre fournisseur de données, n’acceptent pas toutes les propriétés de **Table** objets. Une erreur se produit si vous avez défini une valeur pour une propriété qui le fournisseur ne prend pas en charge. Pour les nouveaux **Table** objets, l’erreur se produit lorsque l’objet est ajouté à la collection. Pour les objets existants, l’erreur se produit lors de la définition de la propriété.  
>   
>  Lors de la création **Table** objets, l’existence d’une valeur par défaut appropriée pour une propriété facultative ne garantit pas que votre fournisseur prend en charge la propriété. Pour plus d’informations sur les propriétés de votre fournisseur prend en charge, consultez la documentation du fournisseur.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements de l’objet Table](../../../ado/reference/adox-api/table-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de propriété ActiveConnection de catalogue (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Tables et colonnes ajouter des méthodes, exemple de nom de propriété (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Méthode Close de connexion, exemple de propriété de Type de Table (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Keys Append, méthode, Type de clé, RelatedColumn, RelatedTable et UpdateRule, exemple de propriétés (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog, propriété-Exemple (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Columns, Collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Indexes, Collection (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [Keys, Collection (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)   
 [Collection de propriétés (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Tables, collection (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)
