---
description: Procedure, objet (ADOX)
title: PROCEDURE, objet (ADOX) | Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: ee804ac6f4668f28d5f13754109b0f038d7e1ec4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439651"
---
# <a name="procedure-object-adox"></a>Procedure, objet (ADOX)
Représente une procédure stockée. Lorsqu’il est utilisé conjointement avec l’objet de [commande](../../../ado/reference/ado-api/command-object-ado.md) ADO, l’objet de **procédure** peut être utilisé pour ajouter, supprimer ou modifier des procédures stockées.  
  
## <a name="remarks"></a>Notes  
 L’objet **procedure** vous permet de créer une procédure stockée sans avoir à connaître ou à utiliser la syntaxe « CREATE PROCEDURE » du fournisseur.  
  
 Avec les propriétés d’un objet de **procédure** , vous pouvez :  
  
-   Identifiez la procédure avec la propriété [Name](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Spécifiez l’objet de **commande** ADO qui peut être utilisé pour créer ou exécuter la procédure avec la propriété [Command](../../../ado/reference/adox-api/command-property-adox.md) .  
  
-   Retourne les informations de date avec les propriétés [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) et [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) .  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet Procedure](../../../ado/reference/adox-api/procedure-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Command et CommandText, exemples de propriétés (VB)](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Parameters (collection), Command, exemple de propriété (VB)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [Procedures, exemple de méthode Append (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Procedures, exemple de méthode Delete (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Procedures, collection (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)
