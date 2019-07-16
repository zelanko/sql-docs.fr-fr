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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67966504"
---
# <a name="datemodified-property-adox"></a>DateModified, propriété (ADOX)
Indique la date de que dernière modification de l’objet.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un **Variant** valeur qui spécifie la date de modification. La valeur est null si **DateModified** n’est pas pris en charge par le fournisseur.  
  
## <a name="remarks"></a>Notes  
 Le **DateModified** propriété a la valeur null pour les objets récemment ajoutés. Après avoir ajouté un nouvel [vue](../../../ado/reference/adox-api/view-object-adox.md) ou [procédure](../../../ado/reference/adox-api/procedure-object-adox.md), vous devez appeler la [Actualiser](../../../ado/reference/ado-api/refresh-method-ado.md) méthode de la [vues](../../../ado/reference/adox-api/views-collection-adox.md) ou [procédures ](../../../ado/reference/adox-api/procedures-collection-adox.md) collection pour obtenir des valeurs pour le **DateModified** propriété.  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Procedure, objet (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Table, objet (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[View, objet (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [DateCreated et DateModified, exemples de propriétés (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [DateCreated, propriété (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)
