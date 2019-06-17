---
title: Ordinal, propriété (ADO MD cellule) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cell::Ordinal
- Ordinal
helpviewer_keywords:
- Ordinal property [ADO MD]
ms.assetid: a6001168-b954-47f0-ba0d-c05c4cc40c58
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c4a40c59ad222c943cefe089ffaddd53f2cec25a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66708814"
---
# <a name="ordinal-property-ado-md-cell"></a>Ordinal, propriété (objet Cell d’ADO MD)
Identifie de façon unique un [cellule](../../../ado/reference/ado-md-api/cell-object-ado-md.md) par sa position au sein d’un ensemble de cellules.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un **Long** entier et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 Valeur ordinale de la cellule identifie de façon unique la cellule au sein d’un ensemble de cellules. Conceptuellement, les cellules sont numérotées dans un ensemble de cellules comme si ce dernier était un *p*-tableau dimensionnel, où *p* est le nombre de [axes](../../../ado/reference/ado-md-api/axes-collection-ado-md.md). Les cellules sont numérotées à partir de zéro dans l’ordre ligne-champ. Voici la formule pour calculer le nombre ordinal d’une cellule :  
  
 Valeur ordinale de la cellule peut être utilisée avec le [élément](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) propriété de la [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) objet à récupérer rapidement le [cellule](../../../ado/reference/ado-md-api/cell-object-ado-md.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Cell, objet (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple avec Axis (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Cellset, objet (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Propriété Item (ensemble de cellules ADO MD)](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)   
 [Ordinal, propriété (objet Position d’ADO MD)](../../../ado/reference/ado-md-api/ordinal-property-ado-md-position.md)
