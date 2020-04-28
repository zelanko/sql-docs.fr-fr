---
title: Collection Members (ADO MD) | Microsoft Docs
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
ms.openlocfilehash: 79394abee5b12bb10f34a34e882d2ac0562722fe
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67949432"
---
# <a name="members-collection-ado-md"></a>Members, collection (ADO MD)
Contient les objets [membres](../../../ado/reference/ado-md-api/member-object-ado-md.md) d’un niveau ou d’une position le long d’un axe.  
  
## <a name="remarks"></a>Notes  
 Une collection **members** est utilisée pour contenir les types de membres suivants :  
  
-   Les membres qui composent un niveau dans un cube. Celles-ci sont contenues dans la collection **members** d’un objet [Level](../../../ado/reference/ado-md-api/level-object-ado-md.md) . Par exemple, à l’aide de l’exemple de [vue d’ensemble des schémas et des données multidimensionnels](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md), les quatre membres du niveau pays sont Canada, États-Unis, Royaume-Uni et Allemagne.  
  
-   Membres qui sont les enfants d’un membre spécifique dans une hiérarchie. Ces membres sont retournés par la propriété [Children](../../../ado/reference/ado-md-api/children-property-ado-md.md) de l’objet **membre** parent. Par exemple, à nouveau à l’aide du même exemple, les deux enfants du membre du Canada sont Canada-est et Canada-Ouest.  
  
-   Membres qui définissent une position spécifique le long d’un axe d’un [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md). À l’aide de l’exemple de l’utilisation [des données multidimensionnelles](../../../ado/guide/multidimensional/working-with-multidimensional-data.md) , les deux membres de la première position sur l’axe des x sont Saint-Valentin et Seattle. Ces membres sont contenus dans la collection de **membres** d’un objet [position](../../../ado/reference/ado-md-api/position-object-ado-md.md) .  
  
 **Members** est une collection ADO standard. Avec les propriétés et les méthodes d’une collection, vous pouvez effectuer les opérations suivantes :  
  
-   Obtenez le nombre d’objets dans la collection avec la propriété [Count](../../../ado/reference/ado-api/count-property-ado.md) .  
  
-   Retourne un objet de la collection avec la propriété [Item](../../../ado/reference/ado-api/item-property-ado.md) par défaut.  
  
-   Mettez à jour les objets de la collection à partir du fournisseur à l’aide de la méthode [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) .  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements](../../../ado/reference/ado-md-api/members-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Members, exemple (VBScript)](../../../ado/reference/ado-md-api/members-example-vbscript.md)   
 [Member, objet (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)
