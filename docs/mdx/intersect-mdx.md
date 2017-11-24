---
title: Intersect (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: INTERSECT
dev_langs: kbMDX
helpviewer_keywords: Intersect function
ms.assetid: 0de8fbb4-e2db-480c-86f1-2abbbcfdb1d8
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 5b0c893ae58a1040912366492b8cec0ddcbc4a86
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="intersect-mdx"></a>Intersect (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne l'intersection de deux ensembles d'entrée, en conservant éventuellement les doublons.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Intersect(Set_Expression1 , Set_Expression2 [ , ALL ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression1*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Set_Expression2*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 Le **Intersect** fonction retourne l’intersection de deux jeux. Par défaut, cette fonction supprime les doublons des deux ensembles avant l'intersection. Les deux ensembles spécifiés doivent avoir le même dimensionnement.  
  
 Le paramètre facultatif **tous les** indicateur conserve les doublons. Si **tous les** est spécifié, le **Intersect** fonction entre en intersection avec les éléments qui comme d’habitude et que l’intersection de chaque doublon dans le premier jeu qui a un doublon correspondant dans le deuxième jeu. Les deux ensembles spécifiés doivent avoir le même dimensionnement.  
  
## <a name="example"></a>Exemple  
 La requête suivante retourne les années 2003 et 2004, les deux membres qui apparaissent dans les deux ensembles spécifiés :  
  
 `SELECT`  
  
 `INTERSECT(`  
  
 `{[Date].[Calendar Year].&[2001], [Date].[Calendar Year].&[2002],[Date].[Calendar Year].&[2003]}`  
  
 `, {[Date].[Calendar Year].&[2002],[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]})`  
  
 `ON 0`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 La requête suivante est inopérante, car les deux jeux spécifiés contiennent des membres rattachés à des hiérarchies différentes :   
  
 `SELECT`  
  
 `INTERSECT(`  
  
 `{[Date].[Calendar Year].&[2001]}`  
  
 `, {[Customer].[City].&[Abingdon]&[ENG]})`  
  
 `ON 0`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
