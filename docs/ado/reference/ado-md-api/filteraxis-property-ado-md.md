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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67938455"
---
# <a name="filteraxis-property-ado-md"></a>FilterAxis, propriété (ADO MD)
Indique les informations de filtre actuel [cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un [axe](../../../ado/reference/ado-md-api/axis-object-ado-md.md) de l’objet et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **FilterAxis** propriété pour retourner des informations sur les dimensions qui ont été utilisés pour découper les données. Le [DimensionCount](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md) propriété de la **axe** retourne le nombre de dimensions de découpage. Cet axe a généralement une seule ligne.  
  
 Le **axe** retourné par **FilterAxis** n’est pas contenue dans le [Axes](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) collection pour un [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) objet.  
  
## <a name="applies-to"></a>S'applique à  
 [Cellset, objet (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Axis, objet (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Dimension, objet (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [DimensionCount, propriété (ADO MD)](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md)
