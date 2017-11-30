---
title: "L’instruction FREEZE (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: FREEZE
dev_langs: kbMDX
helpviewer_keywords:
- FREEZE statement
- locking cell values [MDX]
ms.assetid: 59f1e860-6f37-41af-97d6-7708bdaac933
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b447ef6b4c4699e652b6093c5d0a10e44ecb4d41
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="mdx-scripting---freeze"></a>Écriture de scripts MDX - FIGER
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Verrouille à leur valeur actuelle les valeurs des cellules d'un sous-cube spécifié. Lorsque les cellules sont verrouillées, les modifications apportées à d'autres cellules n'ont aucun effet sur ces cellules verrouillées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FREEZE Subcube_Expression   
```  
  
## <a name="arguments"></a>Arguments  
 *Subcube_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un sous-cube.  
  
## <a name="remarks"></a>Notes  
 Le **FIGER** instruction verrouille les valeurs des cellules dans un sous-cube spécifié, en empêchant les instructions suivantes dans MDX passe de script à partir de la modification de leurs valeurs dans le calcul ultérieurs.  
  
 Dans l'exemple suivant, A et B représentent des sous-cubes dans un script de calcul MDX :  
  
```  
B = 2;  
A = B;  
B = 3  
```  
  
 À ce stade, A et B équivalent à 3.  
  
 Nous insérons à présent le **Figer** fonction Verrouiller les cellules dans le sous-cube A :  
  
```  
B = 2;  
A = B;  
FREEZE(A);  
B = 3  
```  
  
 A équivaut désormais à 2 et B à 3.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de script MDX &#40; MDX &#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
