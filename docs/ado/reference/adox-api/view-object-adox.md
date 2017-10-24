---
title: "Afficher l’objet (ADOX) | Documents Microsoft"
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
- View
helpviewer_keywords:
- View object [ADOX]
ms.assetid: 653421ce-7b94-43d0-9bc6-4900f8f2af45
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a9b3b61a1874528ab6bf649bc62a0c5114148691
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="view-object-adox"></a>Objet de vue (ADOX)
Représente un ensemble filtré d’enregistrements ou une table virtuelle. Lorsqu’il est utilisé conjointement avec ADO [commande](../../../ado/reference/ado-api/command-object-ado.md) objet, le **vue** objet peut être utilisé pour l’ajout, la suppression ou la modification des vues.  
  
## <a name="remarks"></a>Notes  
 Une vue est une table virtuelle, créée à partir d’autres tables de base de données ou des vues. Le **vue** objet vous permet de créer une vue sans avoir à connaître ou utiliser la syntaxe du fournisseur « CREATE VIEW ».  
  
 Avec les propriétés d’un **vue** de l’objet, vous pouvez :  
  
-   Identifier la vue avec le [nom](../../../ado/reference/adox-api/name-property-adox.md) propriété.  
  
-   Spécifiez le ADO **commande** objet qui peut être utilisé pour ajouter, supprimer ou modifier les vues avec la [commande](../../../ado/reference/adox-api/command-property-adox.md) propriété.  
  
-   Retourner des informations de date avec la [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) et [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) propriétés.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Afficher les propriétés de l’objet, méthodes et événements](../../../ado/reference/adox-api/view-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vues et exemple de Collections de champs (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Views Append, méthode-exemple (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Collection de vues, exemple de propriété CommandText (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Exemple de méthode (VB) de suppression de vues](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Collection de vues (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)

