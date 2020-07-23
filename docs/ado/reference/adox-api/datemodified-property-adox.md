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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c3a2a8ba0890dd50621fac143aa102091abcc19
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942711"
---
# <a name="datemodified-property-adox"></a>DateModified, propriété (ADOX)
Indique la date à laquelle l’objet a été modifié pour la dernière fois.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne une valeur de **type Variant** spécifiant la date de modification. La valeur est null si **DateModified** n’est pas pris en charge par le fournisseur.  
  
## <a name="remarks"></a>Remarques  
 La propriété **DateModified** a la valeur null pour les objets récemment ajoutés. Après avoir ajouté une nouvelle [vue](../../../ado/reference/adox-api/view-object-adox.md) ou une nouvelle [procédure](../../../ado/reference/adox-api/procedure-object-adox.md), vous devez appeler la méthode [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) de la collection [views](../../../ado/reference/adox-api/views-collection-adox.md) ou [procedures](../../../ado/reference/adox-api/procedures-collection-adox.md) pour obtenir les valeurs de la propriété **DateModified** .  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [Procedure, objet (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)  
    :::column-end:::
    :::column:::
        [Table, objet (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)  
    :::column-end:::
    :::column:::
        [View, objet (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi  
 [DateCreated et DateModified, exemple de propriétés (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [DateCreated, propriété (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)
