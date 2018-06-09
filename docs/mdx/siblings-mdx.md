---
title: Frères (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a4414e134d3b837406c3cb72566084029cf522c9
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742848"
---
# <a name="siblings-mdx"></a>Siblings (MDX)


  Retourne les frères d'un membre spécifié, notamment le membre lui-même.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.Siblings   
```  
  
## <a name="arguments"></a>Arguments  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
### <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne la mesure par défaut des frères du mois de mars 2003, soit les mois de janvier, février et mars 2003 inclus.  
  
```  
SELECT [Date].[Calendar].[Month].[March 2003].Siblings ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
