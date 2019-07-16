---
title: Columns, Collection (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Index::Columns
- Table::Columns
- Key::Columns
- Columns
helpviewer_keywords:
- Columns collection [ADOX]
ms.assetid: 23b9fea8-4f76-4a51-95ce-1a6ce4560b34
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bc3686ac69d7afeeebec14939a42e073f796b1ec
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67966844"
---
# <a name="columns-collection-adox"></a>Columns, collection (ADOX)
Contient tous les [colonne](../../../ado/reference/adox-api/column-object-adox.md) objets d’une table, un index ou une clé.  
  
## <a name="remarks"></a>Notes  
 Le [Append](../../../ado/reference/adox-api/append-method-adox-columns.md) méthode pour un **colonnes** collection est unique pour ADOX. Vous pouvez :  
  
-   Ajouter une nouvelle colonne à la collection avec le **Append** (méthode).  
  
 Les propriétés et les méthodes restantes sont des collections ADO standard. Vous pouvez :  
  
-   Accès à une colonne dans la collection avec le [élément](../../../ado/reference/ado-api/item-property-ado.md) propriété.  
  
-   Retourner le nombre de colonnes contenues dans la collection avec le [nombre](../../../ado/reference/ado-api/count-property-ado.md) propriété.  
  
-   Supprimer une colonne de la collection avec le [supprimer](../../../ado/reference/adox-api/delete-method-adox-collections.md) (méthode).  
  
-   Mettre à jour les objets dans la collection afin de refléter le schéma de la base de données actuelle avec le [Actualiser](../../../ado/reference/ado-api/refresh-method-ado.md) (méthode).  
  
> [!NOTE]
>  Une erreur se produit lors de l’ajout un **colonne** à la **colonnes** collection d’un [Index](../../../ado/reference/adox-api/index-object-adox.md) si le **colonne** n’existe pas dans un [Table](../../../ado/reference/adox-api/table-object-adox.md) déjà ajouté à la [Tables](../../../ado/reference/adox-api/tables-collection-adox.md) collection.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements de la collection Columns](../../../ado/reference/adox-api/columns-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et colonnes ajouter des méthodes, exemple de nom de propriété (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Méthode Close de connexion, exemple de propriété de Type de Table (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Keys Append, méthode, Type de clé, RelatedColumn, RelatedTable et UpdateRule, exemple de propriétés (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog, propriété-Exemple (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Propriété SortOrder, exemple (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Column, objet (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)
