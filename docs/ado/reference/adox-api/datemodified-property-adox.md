---
description: DateModified, propriété (ADOX)
title: DateModified, propriété (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 613dbf829009e4e471844b0d49285817d75316b6
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984740"
---
# <a name="datemodified-property-adox"></a>DateModified, propriété (ADOX)
Indique la date à laquelle l’objet a été modifié pour la dernière fois.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne une valeur de **type Variant** spécifiant la date de modification. La valeur est null si **DateModified** n’est pas pris en charge par le fournisseur.  
  
## <a name="remarks"></a>Notes  
 La propriété **DateModified** a la valeur null pour les objets récemment ajoutés. Après avoir ajouté une nouvelle [vue](./view-object-adox.md) ou une nouvelle [procédure](./procedure-object-adox.md), vous devez appeler la méthode [Refresh](../ado-api/refresh-method-ado.md) de la collection [views](./views-collection-adox.md) ou [procedures](./procedures-collection-adox.md) pour obtenir les valeurs de la propriété **DateModified** .  
  
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
 [DateCreated, propriété (ADOX)](./datecreated-property-adox.md)