---
title: Mise à jour de cellules (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- modifying cells
- XMLA, cells
- updating cells
- cells [Analysis Services]
- XML for Analysis, cells
ms.assetid: a1c61496-36ee-4bce-98d9-d13440d349aa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f0eab50aa7e70aedee93eef2cefee648e6ceb5c9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81387889"
---
# <a name="updating-cells-xmla"></a>Mise à jour de cellules (XMLA)
  Vous pouvez utiliser la commande [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) pour modifier la valeur d’une ou plusieurs cellules dans un cube activé pour l’écriture différée de cube. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stocke les informations mises à jour dans une table d’écriture différée distincte pour chaque partition qui contient des cellules à mettre à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] jour.  
  
> [!NOTE]  
>  La commande `UpdateCells` ne prend pas en charge les allocations pendant l'écriture différée du cube. Pour utiliser l’écriture différée allouée, vous devez utiliser la commande [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) pour envoyer une instruction Update MDX (Multidimensional Expressions). Pour plus d’informations, consultez [instruction UPDATE CUBE &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube).  
  
## <a name="specifying-cells"></a>Spécification de cellules  
 La propriété de [cellule](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) de `UpdateCells` la commande contient les cellules à mettre à jour. Vous pouvez identifier chaque cellule dans la propriété `Cell` en utilisant leur nombre ordinal. D’un plan [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] conceptuel, les cellules d’un cube sont numérotées comme si le cube était un tableau de dimensions *p*, où *p* est le nombre d’axes. Les cellules sont traitées dans l'ordre ligne-champ. L'illustration suivante présente la formule permettant de calculer le nombre ordinal d'une cellule.  
  
 ![Formule de calcul de position ordinale de cellule](../../analysis-services/dev-guide/media/cellordinalformula.gif "Formule de calcul de position ordinale de cellule")  
  
 Une fois que vous connaissez le nombre ordinal d’une cellule, vous pouvez indiquer la valeur prévue de la cellule dans la propriété [value](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla) de la propriété de [cellule](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) .  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Update &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [Développement avec XMLA dans Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
