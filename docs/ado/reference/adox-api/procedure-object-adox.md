---
title: Objet de procédure (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Procedure
helpviewer_keywords:
- Procedure object [ADOX]
ms.assetid: 927bcf3e-32f5-4a80-98d3-600779f0732e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2c275322fbe65585e100907f25009d2d3e6e0d0f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718851"
---
# <a name="procedure-object-adox"></a>Procedure, objet (ADOX)
Représente une procédure stockée. Lorsqu’il est utilisé conjointement avec le ADO [commande](../../../ado/reference/ado-api/command-object-ado.md) objet, le **procédure** objet peut être utilisé pour l’ajout, suppression ou modification des procédures stockées.  
  
## <a name="remarks"></a>Notes  
 Le **procédure** objet vous permet de créer une procédure stockée sans avoir à connaître ou utiliser la syntaxe du fournisseur « CREATE PROCEDURE ».  
  
 Avec les propriétés d’un **procédure** de l’objet, vous pouvez :  
  
-   Identifier la procédure avec le [nom](../../../ado/reference/adox-api/name-property-adox.md) propriété.  
  
-   Spécifiez le ADO **commande** objet qui peut être utilisé pour créer ou exécuter la procédure avec le [commande](../../../ado/reference/adox-api/command-property-adox.md) propriété.  
  
-   Retourner des informations de date avec la [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) et [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) propriétés.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements de l’objet Procedure](../../../ado/reference/adox-api/procedure-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Command et CommandText, exemple de propriétés (VB)](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Collection de paramètres, exemple de commande de propriété (VB)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [Procedures Append, méthode-exemple (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Procédures Delete, exemple de méthode (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Procedures, collection (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)
