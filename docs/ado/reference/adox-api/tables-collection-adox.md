---
title: Tables, Collection (ADOX) | Documents Microsoft
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
- Catalog::Tables
- Tables
helpviewer_keywords:
- Tables collection [ADOX]
ms.assetid: 38d750e7-f3fb-426e-b4b4-55eea4f1a654
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1489bb1716cb29116e385158e6f05dcc3d028431
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="tables-collection-adox"></a>Collection de tables (ADOX)
Contient tous les [Table](../../../ado/reference/adox-api/table-object-adox.md) objets d’un catalogue.  
  
## <a name="remarks"></a>Notes  
 Le [Append](../../../ado/reference/adox-api/append-method-adox-tables.md) méthode pour un **Tables** collection est unique pour ADOX. Vous pouvez :  
  
-   Ajouter une nouvelle table à la collection avec le **Append** (méthode).  
  
 Les autres propriétés et méthodes sont des collections ADO standard. Vous pouvez :  
  
-   Accéder à une table dans la collection avec le [élément](../../../ado/reference/ado-api/item-property-ado.md) propriété.  
  
-   Retourner le nombre de tables contenues dans la collection avec le [nombre](../../../ado/reference/ado-api/count-property-ado.md) propriété.  
  
-   Supprimer une table à partir de la collection avec le [supprimer](../../../ado/reference/adox-api/delete-method-adox-collections.md) (méthode).  
  
-   Mettre à jour les objets dans la collection pour refléter le schéma actuel de la base de données avec le [Actualiser](../../../ado/reference/ado-api/refresh-method-ado.md) (méthode).  
  
 Certains fournisseurs peuvent retourner des autres objets de schéma, tel qu’une vue, dans le **Tables** collection. Par conséquent, certaines collections ADOX peuvent contenir plusieurs références au même objet. Devez vous supprimez l’objet d’une collection, la modification sera pas visible dans une autre collection qui fait référence à l’objet supprimé tant que le **Actualiser** méthode est appelée sur la collection. Par exemple, avec le fournisseur OLE DB pour Microsoft Jet, les vues sont renvoyées avec la **Tables** collection. Si vous supprimez une vue, vous devez actualiser le **Tables** collection avant de la collection reflète la modification.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés de Collection de tables, méthodes et événements](../../../ado/reference/adox-api/tables-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de propriété ActiveConnection catalogue (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Colonnes et Tables ajouter des méthodes, exemple de propriété Name (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Méthode de fermeture de connexion, exemple de propriété Table Type (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Keys Append, méthode, Type de clé, RelatedColumn, RelatedTable et UpdateRule exemple (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Objet catalogue (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Objet table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)
