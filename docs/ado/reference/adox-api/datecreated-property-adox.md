---
title: DateCreated, propriété (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::get_DateCreated
- _Table::DateCreated
- _Table::GetDateCreated
helpviewer_keywords:
- DateCreated property [ADOX]
ms.assetid: 2bf4b00d-045c-444e-8af7-8af6297ed418
author: rothja
ms.author: jroth
ms.openlocfilehash: 2a94ea4d86d727bc2258b853285eaa7ebc1e48bc
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942432"
---
# <a name="datecreated-property-adox"></a>DateCreated, propriété (ADOX)
Indique la date à laquelle l’objet a été créé.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne une valeur de **type Variant** qui spécifie la date de création. La valeur est null si **DateCreated** n’est pas pris en charge par le fournisseur.  
  
## <a name="remarks"></a>Notes  
 La propriété **DateCreated** a la valeur null pour les objets récemment ajoutés. Après avoir ajouté une nouvelle [vue](../../../ado/reference/adox-api/view-object-adox.md) ou une nouvelle [procédure](../../../ado/reference/adox-api/procedure-object-adox.md), vous devez appeler la méthode [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) de la collection [views](../../../ado/reference/adox-api/views-collection-adox.md) ou [procedures](../../../ado/reference/adox-api/procedures-collection-adox.md) pour obtenir les valeurs de la propriété **DateCreated** .  
  
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
 [DateModified, propriété (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md)
