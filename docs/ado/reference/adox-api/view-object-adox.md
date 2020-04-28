---
title: View, objet (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- View
helpviewer_keywords:
- View object [ADOX]
ms.assetid: 653421ce-7b94-43d0-9bc6-4900f8f2af45
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6bc26e8d59c29bd7b1b0fbdd0a3a4fdb39f8fee1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67964847"
---
# <a name="view-object-adox"></a>View, objet (ADOX)
Représente un jeu d’enregistrements filtré ou une table virtuelle. Lorsqu’il est utilisé conjointement avec l’objet [Command](../../../ado/reference/ado-api/command-object-ado.md) ADO, l’objet **View** peut être utilisé pour ajouter, supprimer ou modifier des vues.  
  
## <a name="remarks"></a>Notes  
 Une vue est une table virtuelle créée à partir d’autres tables ou vues de base de données. L’objet **View** vous permet de créer une vue sans avoir à connaître ou à utiliser la syntaxe « CREATE VIEW » du fournisseur.  
  
 Avec les propriétés d’un objet **View** , vous pouvez :  
  
-   Identifiez la vue à l’aide de la propriété [Name](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Spécifiez l’objet de **commande** ADO qui peut être utilisé pour ajouter, supprimer ou modifier des vues avec la propriété [Command](../../../ado/reference/adox-api/command-property-adox.md) .  
  
-   Retourne les informations de date avec les propriétés [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) et [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) .  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet View](../../../ado/reference/adox-api/view-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Views et Fields, exemple de collections (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Views, exemple de méthode Append (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Views, collection, CommandText, exemple de propriété (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Views, exemple de méthode Delete (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Views, collection (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
