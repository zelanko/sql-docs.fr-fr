---
title: Mise à jour des cellules (XMLA) Microsoft Docs
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
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81387889"
---
# <a name="updating-cells-xmla"></a>Mise à jour de cellules (XMLA)
  Vous pouvez utiliser la commande [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) pour modifier la valeur d’une ou plusieurs cellules d’un cube activé pour la rédaction de cubes. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stocke les informations mises à jour dans un tableau de rédaction distinct pour chaque partition qui contient des cellules à mettre à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] jour.  
  
> [!NOTE]  
>  La commande `UpdateCells` ne prend pas en charge les allocations pendant l'écriture différée du cube. Pour utiliser la lecture allouée, vous devez utiliser la commande [De déclaration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) pour envoyer une déclaration UPDATE d’expressions multidimensionnelles (MDX). Pour plus d’informations, voir [UPDATE CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube).  
  
## <a name="specifying-cells"></a>Spécification de cellules  
 La propriété cell `UpdateCells` [de](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) la commande contient les cellules à mettre à jour. Vous pouvez identifier chaque cellule dans la propriété `Cell` en utilisant leur nombre ordinal. Conceptuellement, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] les cellules de nombre dans un cube comme si le cube étaient un tableau de p-dimensionnel, où *p* est le nombre de haches. *p* Les cellules sont traitées dans l'ordre ligne-champ. L'illustration suivante présente la formule permettant de calculer le nombre ordinal d'une cellule.  
  
 ![Formule de calcul de position ordinale de cellule](../../analysis-services/dev-guide/media/cellordinalformula.gif "Formule de calcul de position ordinale de cellule")  
  
 Une fois que vous connaissez le numéro ordinaire d’une cellule, vous pouvez indiquer la valeur prévue de la cellule dans la propriété [De valeur](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla) de la propriété [Cell.](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla)  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à jour Élément &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [Développement avec XMLA dans Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
