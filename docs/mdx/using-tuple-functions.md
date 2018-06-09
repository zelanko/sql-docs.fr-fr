---
title: À l’aide des fonctions de Tuple | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 578192fa982b8bbf65527f4ff1d71b6595a2400d
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743820"
---
# <a name="using-tuple-functions"></a>Utilisation de fonctions de tuple


  Une fonction de tuple récupère un tuple à partir d'un jeu ou en résolvant la représentation sous forme de chaîne d'un tuple.  
  
 Les fonctions de tuple, comme les fonctions de membre et les fonctions de définition, sont essentielles à la négociation des structures multidimensionnelles présentes dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Il existe trois fonctions tuple dans MDX, [actuel &#40;MDX&#41;](../mdx/current-mdx.md), [élément &#40;Tuple&#41; &#40;MDX&#41; ](../mdx/item-tuple-mdx.md) et [StrToTuple &#40;MDX&#41;](../mdx/strtotuple-mdx.md). L'exemple de requête suivant montre comment les utiliser :  
  
 `WITH`  
  
 `//Creates a set of tuples consisting of Years and Countries`  
  
 `SET MyTuples AS  [Date].[Calendar Year].[Calendar Year].MEMBERS * [Customer].[Country].[Country].MEMBERS`  
  
 `//Returns a string representation of that set using the Current and Generate functions`  
  
 `MEMBER MEASURES.CURRENTDEMO AS GENERATE(MyTuples, TUPLETOSTR(MyTuples.CURRENT), ", ")`  
  
 `//Retrieves the fourth tuple from that set and displays it as a string`  
  
 `MEMBER MEASURES.ITEMDEMO AS TUPLETOSTR(MyTuples.ITEM(3))`  
  
 `//Creates a tuple consisting of the measure Internet Sales Amount and the country Australia from a string`  
  
 `MEMBER MEASURES.STRTOTUPLEDEMO AS STRTOTUPLE("([Measures].[Internet Sales Amount]" + ", [Customer].[Country].&[Australia])")`  
  
 `SELECT{MEASURES.CURRENTDEMO,MEASURES.ITEMDEMO,MEASURES.STRTOTUPLEDEMO} ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;syntaxe MDX&#41;](../mdx/functions-mdx-syntax.md)   
 [À l’aide des fonctions membres](../mdx/using-member-functions.md)   
 [Utilisation de fonctions de jeu](../mdx/using-set-functions.md)  
  
  
