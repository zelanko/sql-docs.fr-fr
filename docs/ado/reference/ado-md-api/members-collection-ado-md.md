---
title: Members, Collection (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level::Members
- Members
- Position::Members
helpviewer_keywords:
- Members collection [ADO MD]
ms.assetid: 3a647cde-efdc-4394-b1b9-8cbb1b9d689f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 541e1098dfd18210e7c07a0718ecd3add758c8a4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62659562"
---
# <a name="members-collection-ado-md"></a>Members, collection (ADO MD)
Contient le [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) objets à partir d’un niveau ou une position le long d’un axe.  
  
## <a name="remarks"></a>Notes  
 Un **membres** collection est utilisée pour contenir les types de membres suivants :  
  
-   Les membres qui constituent un niveau dans un cube. Elles se trouvent dans le **membres** collection d’un [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md) objet. Par exemple, utilisez l’exemple [vue d’ensemble de schémas et données multidimensionnels](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md), les quatre membres du niveau pays sont Canada, USA, UK et Allemagne.  
  
-   Les membres qui sont les enfants d’un membre spécifique au sein d’une hiérarchie. Ces membres sont retournés par la [enfants](../../../ado/reference/ado-md-api/children-property-ado-md.md) propriété du parent **membre** objet. Par exemple, en utilisant le même exemple, sont les deux enfants du membre Canada-est du Canada et ouest des États-Unis-Canada.  
  
-   Les membres qui définissent une position spécifique le long d’un axe d’un [cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md). À l’aide de l’ensemble de cellules à partir de [MD](../../../ado/guide/multidimensional/working-with-multidimensional-data.md) par exemple, les deux membres de la première position sur l’axe des x sont Valentine et Seattle. Ces membres sont contenus par le **membres** collection d’un [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md) objet.  
  
 **Membres** est une collection ADO standard. Les propriétés et les méthodes d’une collection, vous pouvez effectuer les tâches suivantes :  
  
-   Obtenir le nombre d’objets dans la collection avec le [nombre](../../../ado/reference/ado-api/count-property-ado.md) propriété.  
  
-   Retourner un objet de la collection avec la valeur par défaut [élément](../../../ado/reference/ado-api/item-property-ado.md) propriété.  
  
-   Mettre à jour les objets dans la collection à partir du fournisseur avec le [Actualiser](../../../ado/reference/ado-api/refresh-method-ado.md) (méthode).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements](../../../ado/reference/ado-md-api/members-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple avec Members (VBScript)](../../../ado/reference/ado-md-api/members-example-vbscript.md)   
 [Member, objet (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)
