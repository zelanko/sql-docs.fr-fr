---
title: "Mise à jour de cellules (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
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
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 57edea50d67fa52de99f92b85b40bcd5caf307fb
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="updating-cells-xmla"></a>Mise à jour de cellules (XMLA)
  Vous pouvez utiliser la [UpdateCells](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md) commande pour modifier la valeur d’une ou plusieurs cellules dans un cube activé pour l’écriture différée du cube. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stocke les informations de mise à jour dans une table d’écriture différée distincte pour chaque partition qui contient des cellules à mettre à jour.  
  
> [!NOTE]  
>  Le **UpdateCells** commande ne prend pas en charge les allocations pendant l’écriture différée du cube. Pour utiliser l’écriture différée allouée, vous devez utiliser le [instruction](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) commande à envoyer une instruction MDX (Multidimensional Expressions) UPDATE. Pour plus d’informations, consultez [instruction UPDATE CUBE &#40; MDX &#41; ](../../mdx/mdx-data-manipulation-update-cube.md).  
  
## <a name="specifying-cells"></a>Spécification de cellules  
 Le [cellule](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) propriété de la **UpdateCells** commande contient les cellules à mettre à jour. Vous identifiez chaque cellule dans le **cellule** propriété à l’aide d’un nombre ordinal de cette cellule. Point de vue conceptuel, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] numérote les cellules dans un cube comme si le cube a été un *p*-tableau dimensionnel, où *p* est le nombre d’axes. Les cellules sont traitées dans l'ordre ligne-champ. L'illustration suivante présente la formule permettant de calculer le nombre ordinal d'une cellule.  
  
 ![Formule pour calculer la position ordinale de cellule](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/media/cellordinalformula.gif "formule pour calculer la position ordinale de cellule")  
  
 Une fois que vous connaissez un nombre ordinal d’une cellule, vous pouvez indiquer la valeur prévue de la cellule dans le [valeur](../../analysis-services/xmla/xml-elements-properties/value-element-xmla.md) propriété de la [cellule](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Mettre à jour, élément &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Développement avec XMLA dans Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
