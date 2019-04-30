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
manager: craigg
ms.openlocfilehash: 02731da2b023b7230b3407e0eb386fe8e5aaaf87
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281561"
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
