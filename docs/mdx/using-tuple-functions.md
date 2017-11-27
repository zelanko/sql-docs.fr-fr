---
title: "À l’aide des fonctions de Tuple | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- tuple functions
ms.assetid: fe41e3e5-a675-4169-a966-b42c18e8d741
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b92f048f50f26d6ba5c98e28193a44a68e3ceb39
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="using-tuple-functions"></a>Utilisation de fonctions de tuple
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Une fonction de tuple récupère un tuple à partir d'un jeu ou en résolvant la représentation sous forme de chaîne d'un tuple.  
  
 Les fonctions de tuple, comme les fonctions de membre et les fonctions de définition, sont essentielles à la négociation des structures multidimensionnelles présentes dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Il existe trois fonctions tuple dans MDX, [actuel &#40; MDX &#41; ](../mdx/current-mdx.md), [Élément &#40; Tuple &#41; &#40; MDX &#41; ](../mdx/item-tuple-mdx.md) et [StrToTuple &#40; MDX &#41; ](../mdx/strtotuple-mdx.md). L'exemple de requête suivant montre comment les utiliser :  
  
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
 [Fonctions &#40; La syntaxe MDX &#41;](../mdx/functions-mdx-syntax.md)   
 [À l’aide des fonctions membres](../mdx/using-member-functions.md)   
 [À l’aide des fonctions de jeu](../mdx/using-set-functions.md)  
  
  

