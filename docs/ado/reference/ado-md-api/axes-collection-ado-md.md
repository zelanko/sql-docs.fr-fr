---
title: Axes, Collection (ADO MD) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f30d7fed3748e954410272d8c1a019194c335ea1
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66709944"
---
# <a name="axes-collection-ado-md"></a>Axes, collection (ADO MD)
Contient le [axe](../../../ado/reference/ado-md-api/axis-object-ado-md.md) objets qui définissent un ensemble de cellules.  
  
## <a name="remarks"></a>Notes  
 Un [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) objet contient un **Axes** collection. Une fois le **Cellset** est ouvert, cette collection contiendra au moins un **axe**. Consultez le [axe](../../../ado/reference/ado-md-api/axis-object-ado-md.md) objet pour une explication plus détaillée de l’utilisation de **axe** objets.  
  
> [!NOTE]
>  L’axe de filtre d’un **Cellset** n’est pas contenue dans le **Axes** collection. Consultez le [FilterAxis](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md) propriété pour plus d’informations.  
  
 **Axes** est une collection ADO standard. Les propriétés et les méthodes d’une collection, vous pouvez effectuer les tâches suivantes :  
  
-   Obtenir le nombre d’objets dans la collection avec le [nombre](../../../ado/reference/ado-api/count-property-ado.md) propriété.  
  
-   Retourner un objet de la collection avec la valeur par défaut [élément](../../../ado/reference/ado-api/item-property-ado.md) propriété.  
  
-   Mettre à jour les objets dans la collection à partir du fournisseur avec le [Actualiser](../../../ado/reference/ado-api/refresh-method-ado.md) (méthode).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements](../../../ado/reference/ado-md-api/axes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple avec Cellset (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Axis, objet (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)
