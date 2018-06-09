---
title: En cours (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4e4962dfd9eba7d3a21710fef33aa39256dcfbfa
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739478"
---
# <a name="current-mdx"></a>Current (MDX)


  Retourne le tuple actif dans un jeu lors d'une itération.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set_Expression.Current   
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 À chaque étape d'une itération, le tuple utilisé est le tuple actif. Le **actuel** fonction retourne ce tuple. Cette fonction est valide uniquement lors d'une itération sur un jeu.  
  
 Incluent des fonctions MDX qui itèrent au sein d’un ensemble le [générer](../mdx/generate-mdx.md) (fonction).  
  
> [!NOTE]  
>  Cette fonction agit uniquement avec des jeux nommés, soit par le biais d'un alias spécifique, soit en définissant un jeu nommé.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant montre comment utiliser le **actuel** à l’intérieur de fonction **générer**:  
  
 `WITH`  
  
 `//Creates a set of tuples consisting of all Calendar Years crossjoined with`  
  
 `//all Product Categories`  
  
 `SET MyTuples AS CROSSJOIN(`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS,`  
  
 `[Product].[Category].[Category].MEMBERS)`  
  
 `//Iterates through each tuple in the set and returns the name of the Calendar`  
  
 `//Year in each tuple`  
  
 `MEMBER MEASURES.CURRENTDEMO AS`  
  
 `GENERATE(MyTuples, MyTuples.CURRENT.ITEM(0).NAME, ", ")`  
  
 `SELECT MEASURES.CURRENTDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
