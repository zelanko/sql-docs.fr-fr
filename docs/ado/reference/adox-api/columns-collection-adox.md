---
title: Collection de colonnes (ADOX) | Documents Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Index::Columns
- Table::Columns
- Key::Columns
- Columns
helpviewer_keywords:
- Columns collection [ADOX]
ms.assetid: 23b9fea8-4f76-4a51-95ce-1a6ce4560b34
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 21bf59bef5782c63a272fb16ba1a07889c6fad67
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="columns-collection-adox"></a>Collection de colonnes (ADOX)
Contient tous les [colonne](../../../ado/reference/adox-api/column-object-adox.md) les objets d’une table, un index ou une clé.  
  
## <a name="remarks"></a>Notes  
 Le [Append](../../../ado/reference/adox-api/append-method-adox-columns.md) méthode pour un **colonnes** collection est unique pour ADOX. Vous pouvez :  
  
-   Ajouter une nouvelle colonne à la collection avec le **Append** (méthode).  
  
 Les autres propriétés et méthodes sont des collections ADO standard. Vous pouvez :  
  
-   Accéder à une colonne dans la collection avec le [élément](../../../ado/reference/ado-api/item-property-ado.md) propriété.  
  
-   Retourner le nombre de colonnes contenues dans la collection avec le [nombre](../../../ado/reference/ado-api/count-property-ado.md) propriété.  
  
-   Supprimer une colonne de la collection avec le [supprimer](../../../ado/reference/adox-api/delete-method-adox-collections.md) (méthode).  
  
-   Mettre à jour les objets dans la collection pour refléter le schéma de la base de données en cours avec le [Actualiser](../../../ado/reference/ado-api/refresh-method-ado.md) (méthode).  
  
> [!NOTE]
>  Une erreur se produit lors de l’ajout un **colonne** à la **colonnes** collection d’un [Index](../../../ado/reference/adox-api/index-object-adox.md) si le **colonne** n’existe pas dans un [Table](../../../ado/reference/adox-api/table-object-adox.md) déjà ajouté à la [Tables](../../../ado/reference/adox-api/tables-collection-adox.md) collection.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés de Collection de colonnes, des méthodes et des événements](../../../ado/reference/adox-api/columns-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Colonnes et Tables ajouter des méthodes, exemple de propriété Name (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Méthode de fermeture de connexion, exemple de propriété Table Type (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Keys Append, méthode, Type de clé, RelatedColumn, RelatedTable et UpdateRule exemple (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Exemple de propriété ParentCatalog (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Exemple de propriété SortOrder (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Objet de colonne (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)

