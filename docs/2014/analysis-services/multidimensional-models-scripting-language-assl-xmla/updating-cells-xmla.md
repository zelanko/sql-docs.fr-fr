---
title: Mise à jour de cellules (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- modifying cells
- XMLA, cells
- updating cells
- cells [Analysis Services]
- XML for Analysis, cells
ms.assetid: a1c61496-36ee-4bce-98d9-d13440d349aa
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f2a4a8976602080f28f736814783397bc6611e64
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143590"
---
# <a name="updating-cells-xmla"></a>Mise à jour de cellules (XMLA)
  Vous pouvez utiliser la [UpdateCells](../xmla/xml-elements-commands/updatecells-element-xmla.md) commande pour modifier la valeur d’une ou plusieurs cellules dans un cube activé pour l’écriture différée du cube. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stocke les informations de mise à jour dans une table d’écriture différée distincte pour chaque partition qui contient des cellules à mettre à jour.  
  
> [!NOTE]  
>  La commande `UpdateCells` ne prend pas en charge les allocations pendant l'écriture différée du cube. Pour utiliser l’écriture différée allouée, vous devez utiliser le [instruction](../xmla/xml-elements-commands/statement-element-xmla.md) commande à envoyer une instruction MDX (Multidimensional Expressions) UPDATE. Pour plus d’informations, consultez [instruction UPDATE CUBE &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube).  
  
## <a name="specifying-cells"></a>Spécification de cellules  
 Le [cellule](../xmla/xml-elements-properties/cell-element-xmla.md) propriété de la `UpdateCells` commande contient les cellules à mettre à jour. Vous pouvez identifier chaque cellule dans la propriété `Cell` en utilisant leur nombre ordinal. Point de vue conceptuel, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] numérote les cellules dans un cube comme si le cube a été un *p*-tableau dimensionnel, où *p* est le nombre d’axes. Les cellules sont traitées dans l'ordre ligne-champ. L'illustration suivante présente la formule permettant de calculer le nombre ordinal d'une cellule.  
  
 ![Formule pour calculer la position ordinale de cellule](../../../2014/analysis-services/dev-guide/media/cellordinalformula.gif "formule pour calculer la position ordinale de cellule")  
  
 Une fois que vous connaissez un nombre ordinal d’une cellule, vous pouvez indiquer la valeur prévue de la cellule dans le [valeur](../xmla/xml-elements-properties/value-element-xmla.md) propriété de la [cellule](../xmla/xml-elements-properties/cell-element-xmla.md) propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Mettre à jour d’élément &#40;XMLA&#41;](../xmla/xml-elements-commands/update-element-xmla.md)   
 [Développement avec XMLA dans Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
