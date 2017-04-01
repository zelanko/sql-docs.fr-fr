---
title: "Contenu de FORE_COLOR et BACK_COLOR (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FORE_COLOR (contenu)"
  - "arrière-plan [MDX]"
  - "cellules [MDX]"
  - "couleurs [MDX]"
  - "stockage d'informations sur les couleurs des cellules"
  - "arrière-plan de cellule"
  - "BACK_COLOR (contenu)"
ms.assetid: ff8f40cb-2ac4-4fc2-9761-7f1b14c17c8c
caps.latest.revision: 25
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Contenu de FORE_COLOR et BACK_COLOR (MDX)
  Les propriétés de cellule **FORE_COLOR** et **BACK_COLOR** permettent de stocker les informations de couleur respectivement pour le texte et l’arrière-plan d’une cellule, selon le format rouge-vert-bleu (RVB) du système d’exploitation Microsoft Windows.  
  
 La gamme des valeurs valides pour une couleur RVB ordinaire va de zéro (0) à 16 777 215 (&H00FFFFFF). L'octet de poids fort d'un nombre de cette plage est toujours égal à 0 ; les 3 octets de poids faible, de l'octet le moins significatif à l'octet le plus significatif, déterminent respectivement la quantité de rouge, de vert et de bleu. Chacun des composants rouge, vert et bleu est représenté par un nombre compris entre 0 et 255 (&HFF).  
  
## Voir aussi  
 [Utilisation des propriétés de cellule &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/using-cell-properties-mdx.md)  
  
  