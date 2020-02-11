---
title: Catalog, objet (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Catalog
helpviewer_keywords:
- Catalog object [ADOX]
ms.assetid: bb651639-a488-4e38-b6de-0ed99fa4dd92
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f9843ad9ac0a456f7e38e741e08ce9b66f862fd9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67967057"
---
# <a name="catalog-object-adox"></a>Catalog, objet (ADOX)
Contient des collections ([tables](../../../ado/reference/adox-api/tables-collection-adox.md), [vues](../../../ado/reference/adox-api/views-collection-adox.md), [utilisateurs](../../../ado/reference/adox-api/users-collection-adox.md), [groupes](../../../ado/reference/adox-api/groups-collection-adox.md)et [procédures](../../../ado/reference/adox-api/procedures-collection-adox.md)) qui décrivent le catalogue de schémas d’une source de données.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez modifier l’objet **catalogue** en ajoutant ou en supprimant des objets ou en modifiant des objets existants. Certains fournisseurs peuvent ne pas prendre en charge tous les objets de **catalogue** ou ne prendre en charge que l’affichage des informations de schéma.  
  
 Avec les propriétés et les méthodes d’un objet **catalogue** , vous pouvez :  
  
-   Ouvrez le catalogue en affectant à la propriété [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) un objet de [connexion](../../../ado/reference/ado-api/connection-object-ado.md) ADO ou une chaîne de connexion valide.  
  
-   Créez un catalogue à l’aide de la méthode [Create](../../../ado/reference/adox-api/create-method-adox.md) .  
  
-   Déterminez les propriétaires des objets dans un **catalogue** à l’aide des méthodes [GetObjectOwner](../../../ado/reference/adox-api/getobjectowner-method-adox.md) et [SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md) .  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet Catalog](../../../ado/reference/adox-api/catalog-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de propriété ActiveConnection de Catalog (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Command et CommandText, exemples de propriétés (VB)](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Connection Close, méthode, table type, exemple de propriété (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Create, exemple de méthode (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [Méthodes Append des clés, type de clé, RelatedColumn, RelatedTable et UpdateRule, exemple de propriétés (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Parameters (collection), Command, exemple de propriété (VB)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [ParentCatalog, exemple de propriété (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Procedures, exemple de méthode Append (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Procedures, exemple de méthode Delete (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Procedures, exemple de méthode Refresh (VB)](../../../ado/reference/adox-api/procedures-refresh-method-example-vb.md)   
 [Views et Fields, exemple de collections (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Views, exemple de méthode Append (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Views, collection, CommandText, exemple de propriété (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Views, exemple de méthode Delete (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Views, exemple de méthode Refresh (VB)](../../../ado/reference/adox-api/views-refresh-method-example-vb.md)   
 [Groups, collection (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Procedures, collection (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)   
 [Tables, collection (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Users, collection (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)   
 [Views, collection (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
