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
ms.openlocfilehash: 71279981c5fd3879d633e0fdd8cdec74bed6deac
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68887711"
---
# <a name="updating-cells-xmla"></a>Mise à jour de cellules (XMLA)
  Vous pouvez utiliser la commande [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) pour modifier la valeur d’une ou plusieurs cellules dans un cube activé pour l’écriture différée de cube. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stockelesinformationsmisesàjourdansunetabled’écrituredifféréedistinctepourchaquepartitionquicontientdescellules[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à mettre à jour.  
  
> [!NOTE]  
>  La commande `UpdateCells` ne prend pas en charge les allocations pendant l'écriture différée du cube. Pour utiliser l’écriture différée allouée, vous devez utiliser la commande [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) pour envoyer une instruction Update MDX (Multidimensional Expressions). Pour plus d’informations, consultez [Update cube &#40;Statement&#41;MDX](/sql/mdx/mdx-data-manipulation-update-cube).  
  
## <a name="specifying-cells"></a>Spécification de cellules  
 La propriété de [cellule](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) de `UpdateCells` la commande contient les cellules à mettre à jour. Vous pouvez identifier chaque cellule dans la propriété `Cell` en utilisant leur nombre ordinal. D’un plan [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] conceptuel, les cellules d’un cube sont numérotées comme si le cube était un tableau de dimensions *p*, où *p* est le nombre d’axes. Les cellules sont traitées dans l'ordre ligne-champ. L'illustration suivante présente la formule permettant de calculer le nombre ordinal d'une cellule.  
  
 ![Formule permettant de calculer la position ordinale de la cellule](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/cellordinalformula.gif "Formule permettant de calculer la position ordinale de la cellule")  
  
 Une fois que vous connaissez le nombre ordinal d’une cellule, vous pouvez indiquer la valeur prévue de la cellule dans la propriété [value](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla) de la propriété de [cellule](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) .  
  
## <a name="see-also"></a>Voir aussi  
 [Élément &#40;de mise à jour XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [Développement avec XMLA dans Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
