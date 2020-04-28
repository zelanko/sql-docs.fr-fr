---
title: DateModified, propriété (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::get_DateModified
- _Table::DateModified
- _Table::GetDateModified
helpviewer_keywords:
- DateModified property [ADOX]
ms.assetid: fed09266-1547-4bda-9088-c254d81cc738
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cc41c630b8201651e933f5d6538e6887e7933c95
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67966504"
---
# <a name="datemodified-property-adox"></a>DateModified, propriété (ADOX)
Indique la date à laquelle l’objet a été modifié pour la dernière fois.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne une valeur de **type Variant** spécifiant la date de modification. La valeur est null si **DateModified** n’est pas pris en charge par le fournisseur.  
  
## <a name="remarks"></a>Notes  
 La propriété **DateModified** a la valeur null pour les objets récemment ajoutés. Après avoir ajouté une nouvelle [vue](../../../ado/reference/adox-api/view-object-adox.md) ou une nouvelle [procédure](../../../ado/reference/adox-api/procedure-object-adox.md), vous devez appeler la méthode [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) de la collection [views](../../../ado/reference/adox-api/views-collection-adox.md) ou [procedures](../../../ado/reference/adox-api/procedures-collection-adox.md) pour obtenir les valeurs de la propriété **DateModified** .  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Procedure, objet (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Table, objet (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[View, objet (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [DateCreated et DateModified, exemple de propriétés (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [DateCreated, propriété (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)
