---
description: Instruction FREEZE (MDX)
title: Instruction FREEZE (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 41c71987fec932b2693740792a8d86e200fcf526
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429741"
---
# <a name="mdx-scripting---freeze"></a>Écriture de scripts MDX - FREEZE


  Verrouille à leur valeur actuelle les valeurs des cellules d'un sous-cube spécifié. Lorsque les cellules sont verrouillées, les modifications apportées à d'autres cellules n'ont aucun effet sur ces cellules verrouillées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FREEZE Subcube_Expression   
```  
  
## <a name="arguments"></a>Arguments  
 *Subcube_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un sous-cube.  
  
## <a name="remarks"></a>Notes  
 L’instruction **Freeze** verrouille les valeurs des cellules dans un sous-cube spécifié, empêchant les instructions suivantes dans un script MDX de modifier leurs valeurs dans les tests de calcul suivants.  
  
 Dans l'exemple suivant, A et B représentent des sous-cubes dans un script de calcul MDX :  
  
```  
B = 2;  
A = B;  
B = 3  
```  
  
 À ce stade, A et B équivalent à 3.  
  
 Nous allons maintenant insérer la fonction **Freeze** pour verrouiller les cellules dans un sous-cube :  
  
```  
B = 2;  
A = B;  
FREEZE(A);  
B = 3  
```  
  
 A équivaut désormais à 2 et B à 3.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de script MDX &#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
