---
description: DateCreated, propriété (ADOX)
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
ms.openlocfilehash: 7ae2c0fcfdc164906f0216abb45f98f705de9cd4
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88770738"
---
# <a name="datecreated-property-adox"></a>DateCreated, propriété (ADOX)
Indique la date à laquelle l’objet a été créé.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne une valeur de **type Variant** qui spécifie la date de création. La valeur est null si **DateCreated** n’est pas pris en charge par le fournisseur.  
  
## <a name="remarks"></a>Notes  
 La propriété **DateCreated** a la valeur null pour les objets récemment ajoutés. Après avoir ajouté une nouvelle [vue](./view-object-adox.md) ou une nouvelle [procédure](./procedure-object-adox.md), vous devez appeler la méthode [Refresh](../ado-api/refresh-method-ado.md) de la collection [views](./views-collection-adox.md) ou [procedures](./procedures-collection-adox.md) pour obtenir les valeurs de la propriété **DateCreated** .  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [Procedure, objet (ADOX)](./procedure-object-adox.md)  
    :::column-end:::
    :::column:::
        [Table, objet (ADOX)](./table-object-adox.md)  
    :::column-end:::
    :::column:::
        [View, objet (ADOX)](./view-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi  
 [DateCreated et DateModified, exemple de propriétés (VB)](./datecreated-and-datemodified-properties-example-vb.md)   
 [DateModified, propriété (ADOX)](./datemodified-property-adox.md)