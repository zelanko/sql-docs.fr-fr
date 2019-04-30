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
manager: craigg
ms.openlocfilehash: 5547090443e2f22a135234853b76480fb8295e14
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63184202"
---
# <a name="catalog-object-adox"></a>Catalog, objet (ADOX)
Contient des collections ([Tables](../../../ado/reference/adox-api/tables-collection-adox.md), [vues](../../../ado/reference/adox-api/views-collection-adox.md), [utilisateurs](../../../ado/reference/adox-api/users-collection-adox.md), [groupes](../../../ado/reference/adox-api/groups-collection-adox.md), et [procédures](../../../ado/reference/adox-api/procedures-collection-adox.md)) qui décrire le catalogue de schémas d’une source de données.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez modifier le **catalogue** objet en ajoutant ou supprimant des objets ou en modifiant des objets existants. Certains fournisseurs peuvent tous les prend pas en charge la **catalogue** objets ou peuvent prendre en charge uniquement les informations de schéma d’affichage.  
  
 Avec les propriétés et méthodes d’un **catalogue** de l’objet, vous pouvez :  
  
-   Ouvrir le catalogue en définissant le [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) propriété ADO [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet ou une chaîne de connexion valide.  
  
-   Créer un nouveau catalogue avec le [créer](../../../ado/reference/adox-api/create-method-adox.md) (méthode).  
  
-   Identifier les propriétaires des objets dans un **catalogue** avec la [GetObjectOwner](../../../ado/reference/adox-api/getobjectowner-method-adox.md) et [SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md) méthodes.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements de l’objet Catalog](../../../ado/reference/adox-api/catalog-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de propriété ActiveConnection de catalogue (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Command et CommandText, exemple de propriétés (VB)](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Méthode Close de connexion, exemple de propriété de Type de Table (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Créer l’exemple de méthode (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [Keys Append, méthode, Type de clé, RelatedColumn, RelatedTable et UpdateRule, exemple de propriétés (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Collection de paramètres, exemple de commande de propriété (VB)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [ParentCatalog, propriété-Exemple (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Procedures Append, méthode-exemple (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Procédures Delete, exemple de méthode (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Procédures Refresh, exemple de méthode (VB)](../../../ado/reference/adox-api/procedures-refresh-method-example-vb.md)   
 [Vues et les Collections de champs exemple (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Views Append, méthode-exemple (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Views, Collection, exemple de propriété CommandText (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Vues de supprimer l’exemple de méthode (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Vues Refresh, exemple de méthode (VB)](../../../ado/reference/adox-api/views-refresh-method-example-vb.md)   
 [Collection de groupes (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Procedures, Collection (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)   
 [Tables, Collection (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Les utilisateurs, Collection (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)   
 [Views, collection (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
