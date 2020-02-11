---
title: FilterAxis, propriété (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset::FilterAxis
- FilterAxis
helpviewer_keywords:
- FilterAxis property [ADO MD]
ms.assetid: 9c656963-531e-4cd1-b698-d5f42a9b7ba3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d44ac908c04338f80c18699319f75a068370c3e0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938455"
---
# <a name="filteraxis-property-ado-md"></a>FilterAxis, propriété (ADO MD)
Indique les informations de filtre relatives à l' [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)actuel.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un objet [Axis](../../../ado/reference/ado-md-api/axis-object-ado-md.md) , et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **FilterAxis** pour retourner des informations sur les dimensions qui ont été utilisées pour découper les données. La propriété [DimensionCount](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md) de l' **axe** retourne le nombre de dimensions de découpage. Cet axe n’a généralement qu’une seule ligne.  
  
 L' **axe** retourné par **FilterAxis** n’est pas contenu dans la collection [axes](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) d’un objet [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) .  
  
## <a name="applies-to"></a>S'applique à  
 [Cellset, objet (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [AXIS, objet (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Objet dimension (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [DimensionCount, propriété (ADO MD)](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md)
