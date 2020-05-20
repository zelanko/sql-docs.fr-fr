---
title: Collection axes (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Axes
- Cellset::Axes
helpviewer_keywords:
- Axes collection [ADO MD]
ms.assetid: 072fb21a-ec0f-4b02-9022-1cef3ad4bfff
author: rothja
ms.author: jroth
ms.openlocfilehash: 36c6a55b5ba59fab0fab3f873225f67b18d2d384
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765210"
---
# <a name="axes-collection-ado-md"></a>Axes, collection (ADO MD)
Contient les objets [Axis](../../../ado/reference/ado-md-api/axis-object-ado-md.md) qui définissent un groupe de cellules.  
  
## <a name="remarks"></a>Remarques  
 Un objet [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) contient une collection **axes** . Une fois l’ensemble de **cellules** ouvert, ce regroupement contient au moins un **axe**. Consultez l’objet [Axis](../../../ado/reference/ado-md-api/axis-object-ado-md.md) pour obtenir une explication plus détaillée sur l’utilisation des objets **Axis** .  
  
> [!NOTE]
>  L’axe de filtre d’un ensemble de **cellules** n’est pas contenu dans la collection **axes** . Pour plus d’informations, consultez la propriété [FilterAxis](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md) .  
  
 **Axes** est une collection ADO standard. Avec les propriétés et les méthodes d’une collection, vous pouvez effectuer les opérations suivantes :  
  
-   Obtenez le nombre d’objets dans la collection avec la propriété [Count](../../../ado/reference/ado-api/count-property-ado.md) .  
  
-   Retourne un objet de la collection avec la propriété [Item](../../../ado/reference/ado-api/item-property-ado.md) par défaut.  
  
-   Mettez à jour les objets de la collection à partir du fournisseur à l’aide de la méthode [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) .  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements](../../../ado/reference/ado-md-api/axes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CellSet, exemple (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Axis, objet (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)
