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
ms.openlocfilehash: 8932d2b71f631f24a9ce825804074b9094f932b9
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769708"
---
# <a name="procedure-object-adox"></a>Procedure, objet (ADOX)
Représente une procédure stockée. Lorsqu’il est utilisé conjointement avec l’objet de [commande](../ado-api/command-object-ado.md) ADO, l’objet de **procédure** peut être utilisé pour ajouter, supprimer ou modifier des procédures stockées.  
  
## <a name="remarks"></a>Notes  
 L’objet **procedure** vous permet de créer une procédure stockée sans avoir à connaître ou à utiliser la syntaxe « CREATE PROCEDURE » du fournisseur.  
  
 Avec les propriétés d’un objet de **procédure** , vous pouvez :  
  
-   Identifiez la procédure avec la propriété [Name](./name-property-adox.md) .  
  
-   Spécifiez l’objet de **commande** ADO qui peut être utilisé pour créer ou exécuter la procédure avec la propriété [Command](./command-property-adox.md) .  
  
-   Retourne les informations de date avec les propriétés [DateCreated](./datecreated-property-adox.md) et [DateModified](./datemodified-property-adox.md) .  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet Procedure](./procedure-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Command et CommandText, exemples de propriétés (VB)](./command-and-commandtext-properties-example-vb.md)   
 [Parameters (collection), Command, exemple de propriété (VB)](./parameters-collection-command-property-example-vb.md)   
 [Procedures, exemple de méthode Append (VB)](./procedures-append-method-example-vb.md)   
 [Procedures, exemple de méthode Delete (VB)](./procedures-delete-method-example-vb.md)   
 [Procedures, collection (ADOX)](./procedures-collection-adox.md)