---
title: Contenu de FORE_COLOR et Back_color (MDX) | Documents Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e79767762431ca6f95badfde8cee40ea65975a4a
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="mdx-cell-properties---forecolor-and-backcolor-contents"></a>Propriétés de cellule MDX - contenu de FORE_COLOR et Back_color
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Les propriétés de cellule **FORE_COLOR** et **BACK_COLOR** permettent de stocker les informations de couleur respectivement pour le texte et l’arrière-plan d’une cellule, selon le format rouge-vert-bleu (RVB) du système d’exploitation Microsoft Windows.  
  
 La gamme des valeurs valides pour une couleur RVB ordinaire va de zéro (0) à 16 777 215 (&H00FFFFFF). L'octet de poids fort d'un nombre de cette plage est toujours égal à 0 ; les 3 octets de poids faible, de l'octet le moins significatif à l'octet le plus significatif, déterminent respectivement la quantité de rouge, de vert et de bleu. Chacun des composants rouge, vert et bleu est représenté par un nombre compris entre 0 et 255 (&HFF).  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des propriétés de cellule & #40 ; MDX & #41 ;](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)  
  
  
