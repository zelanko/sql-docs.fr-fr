---
title: Contenu de FORE_COLOR et Back_color (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
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
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e7e22839611c1a9060b66850371d0ac2b551337c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043714"
---
# <a name="forecolor-and-backcolor-contents-mdx"></a>Contenu de FORE_COLOR et BACK_COLOR (MDX)
  Les propriétés de cellule `FORE_COLOR` et `BACK_COLOR` permettent de stocker les informations de couleur respectivement pour le texte et l'arrière-plan d'une cellule, selon le format rouge-vert-bleu (RVB) du système d'exploitation Microsoft Windows.  
  
 La gamme des valeurs valides pour une couleur RVB ordinaire va de zéro (0) à 16 777 215 (&H00FFFFFF). L'octet de poids fort d'un nombre de cette plage est toujours égal à 0 ; les 3 octets de poids faible, de l'octet le moins significatif à l'octet le plus significatif, déterminent respectivement la quantité de rouge, de vert et de bleu. Chacun des composants rouge, vert et bleu est représenté par un nombre compris entre 0 et 255 (&HFF).  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des propriétés de cellule &#40;MDX&#41;](mdx-cell-properties-using-cell-properties.md)  
  
  