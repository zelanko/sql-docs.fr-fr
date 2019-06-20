---
title: La mise à jour de cellules (XMLA) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0cfee2adf9d730b458fd482317d16d963f15ebc1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63262175"
---
# <a name="updating-cells-xmla"></a>Mise à jour de cellules (XMLA)
  Vous pouvez utiliser la [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) commande pour modifier la valeur d’une ou plusieurs cellules dans un cube activé pour l’écriture différée du cube. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stocke les informations mises à jour dans une table d’écriture différée distincte pour chaque partition qui contient les cellules à mettre à jour.  
  
> [!NOTE]  
>  Le **UpdateCells** commande ne prend pas en charge les allocations pendant l’écriture différée du cube. Pour utiliser l’écriture différée allouée, vous devez utiliser le [instruction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) commande à envoyer une instruction MDX (Multidimensional Expressions) UPDATE. Pour plus d’informations, consultez [instruction UPDATE CUBE &#40;MDX&#41;](../../mdx/mdx-data-manipulation-update-cube.md).  
  
## <a name="specifying-cells"></a>Spécification de cellules  
 Le [cellule](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) propriété de la **UpdateCells** commande contient les cellules à mettre à jour. Vous identifiez les cellules dans le **cellule** propriété à l’aide d’un nombre ordinal de cette cellule. Conceptuellement, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] numérote les cellules dans un cube comme si le cube a été un *p*-tableau dimensionnel, où *p* est le nombre d’axes. Les cellules sont traitées dans l'ordre ligne-champ. L'illustration suivante présente la formule permettant de calculer le nombre ordinal d'une cellule.  
  
 ![Formule pour calculer la position ordinale de cellule](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/media/cellordinalformula.gif "formule pour calculer la position ordinale de cellule")  
  
 Une fois que vous connaissez un nombre ordinal d’une cellule, vous pouvez indiquer la valeur prévue de la cellule dans le [valeur](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla) propriété de la [cellule](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Mettre à jour d’élément &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [Développement avec XMLA dans Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
