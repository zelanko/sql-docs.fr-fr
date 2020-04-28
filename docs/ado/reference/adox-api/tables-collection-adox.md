---
title: Tables, collection (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Catalog::Tables
- Tables
helpviewer_keywords:
- Tables collection [ADOX]
ms.assetid: 38d750e7-f3fb-426e-b4b4-55eea4f1a654
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0bf28af10084a30a5c81c76fe7e44781178979ad
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67965134"
---
# <a name="tables-collection-adox"></a>Tables, collection (ADOX)
Contient tous les objets [table](../../../ado/reference/adox-api/table-object-adox.md) d’un catalogue.  
  
## <a name="remarks"></a>Notes  
 La méthode [Append](../../../ado/reference/adox-api/append-method-adox-tables.md) d’une collection **tables** est unique pour ADOX. Vous pouvez :  
  
-   Ajoutez une nouvelle table à la collection à l’aide de la méthode **Append** .  
  
 Les propriétés et les méthodes restantes sont standard pour les collections ADO. Vous pouvez :  
  
-   Accédez à une table de la collection à l’aide de la propriété [Item](../../../ado/reference/ado-api/item-property-ado.md) .  
  
-   Retourne le nombre de tables contenues dans la collection avec la propriété [Count](../../../ado/reference/ado-api/count-property-ado.md) .  
  
-   Supprime une table de la collection à l’aide de la méthode [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md) .  
  
-   Mettez à jour les objets de la collection pour refléter le schéma de base de données actuel avec la méthode [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) .  
  
 Certains fournisseurs peuvent retourner d’autres objets de schéma, tels qu’une vue, dans la collection **tables** . Par conséquent, certaines collections ADOX peuvent contenir plusieurs références au même objet. Si vous supprimez l’objet d’une collection, la modification n’est pas visible dans une autre collection qui fait référence à l’objet supprimé tant que la méthode **Refresh** n’est pas appelée sur la collection. Par exemple, avec le fournisseur de OLE DB pour Microsoft Jet, les vues sont renvoyées avec la collection **tables** . Si vous supprimez une vue, vous devez actualiser la collection **tables** avant que la collection ne reflète la modification.  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de la collection Tables](../../../ado/reference/adox-api/tables-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de propriété ActiveConnection de Catalog (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Columns et tables Append, méthodes, Name, exemple de propriété (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connection Close, méthode, table type, exemple de propriété (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Méthodes Append des clés, type de clé, RelatedColumn, RelatedTable et UpdateRule, exemple de propriétés (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Catalog, objet (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Table, objet (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)
