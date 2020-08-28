---
description: Axes, collection (ADO MD)
title: Collection axes (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 78113cb7854ec3f56ffe6f7322a6bb732939f27f
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88987410"
---
# <a name="axes-collection-ado-md"></a>Axes, collection (ADO MD)
Contient les objets [Axis](./axis-object-ado-md.md) qui définissent un groupe de cellules.  
  
## <a name="remarks"></a>Notes  
 Un objet [Cellset](./cellset-object-ado-md.md) contient une collection **axes** . Une fois l’ensemble de **cellules** ouvert, ce regroupement contient au moins un **axe**. Consultez l’objet [Axis](./axis-object-ado-md.md) pour obtenir une explication plus détaillée sur l’utilisation des objets **Axis** .  
  
> [!NOTE]
>  L’axe de filtre d’un ensemble de **cellules** n’est pas contenu dans la collection **axes** . Pour plus d’informations, consultez la propriété [FilterAxis](./filteraxis-property-ado-md.md) .  
  
 **Axes** est une collection ADO standard. Avec les propriétés et les méthodes d’une collection, vous pouvez effectuer les opérations suivantes :  
  
-   Obtenez le nombre d’objets dans la collection avec la propriété [Count](../ado-api/count-property-ado.md) .  
  
-   Retourne un objet de la collection avec la propriété [Item](../ado-api/item-property-ado.md) par défaut.  
  
-   Mettez à jour les objets de la collection à partir du fournisseur à l’aide de la méthode [Refresh](../ado-api/refresh-method-ado.md) .  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements](./axes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CellSet, exemple (VB)](./cellset-example-vb.md)   
 [Axis, objet (ADO MD)](./axis-object-ado-md.md)