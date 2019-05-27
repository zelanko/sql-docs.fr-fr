---
title: Contenu de FORE_COLOR et BACK_COLOR (contenu) (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- FORE_COLOR contents
- backgrounds [MDX]
- cells [MDX]
- colors [MDX]
- storing cell color information
- cell backgrounds
- BACK_COLOR contents
ms.assetid: ff8f40cb-2ac4-4fc2-9761-7f1b14c17c8c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ecd8bb157d7b501d29230c91d87f148ae738ff45
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66074408"
---
# <a name="forecolor-and-backcolor-contents-mdx"></a>Contenu de FORE_COLOR et BACK_COLOR (MDX)
  Les propriétés de cellule `FORE_COLOR` et `BACK_COLOR` permettent de stocker les informations de couleur respectivement pour le texte et l'arrière-plan d'une cellule, selon le format rouge-vert-bleu (RVB) du système d'exploitation Microsoft Windows.  
  
 La gamme des valeurs valides pour une couleur RVB ordinaire va de zéro (0) à 16 777 215 (&H00FFFFFF). L'octet de poids fort d'un nombre de cette plage est toujours égal à 0 ; les 3 octets de poids faible, de l'octet le moins significatif à l'octet le plus significatif, déterminent respectivement la quantité de rouge, de vert et de bleu. Chacun des composants rouge, vert et bleu est représenté par un nombre compris entre 0 et 255 (&HFF).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des propriétés de cellule &#40;MDX&#41;](mdx-cell-properties-using-cell-properties.md)  
  
  
