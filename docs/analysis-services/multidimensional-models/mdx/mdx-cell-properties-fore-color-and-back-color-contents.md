---
title: Contenu de FORE_COLOR et Back_color (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FORE_COLOR contents
- backgrounds [MDX]
- cells [MDX]
- colors [MDX]
- storing cell color information
- cell backgrounds
- BACK_COLOR contents
ms.assetid: ff8f40cb-2ac4-4fc2-9761-7f1b14c17c8c
caps.latest.revision: "25"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1c39713f66b15fcf959f6ba3887b7002cd7a2863
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="mdx-cell-properties---forecolor-and-backcolor-contents"></a>Propriétés de cellule MDX - contenu de FORE_COLOR et Back_color
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Le **FORE_COLOR** et **BACK_COLOR** les propriétés de cellule stockent des informations de couleur pour le texte et l’arrière-plan d’une cellule, respectivement, au format Microsoft Windows système d’exploitation rouge-vert-bleu (RVB) .  
  
 La gamme des valeurs valides pour une couleur RVB ordinaire va de zéro (0) à 16 777 215 (&H00FFFFFF). L'octet de poids fort d'un nombre de cette plage est toujours égal à 0 ; les 3 octets de poids faible, de l'octet le moins significatif à l'octet le plus significatif, déterminent respectivement la quantité de rouge, de vert et de bleu. Chacun des composants rouge, vert et bleu est représenté par un nombre compris entre 0 et 255 (&HFF).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des propriétés de cellule &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)  
  
  
