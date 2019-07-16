---
title: Current (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 821d517419b90df44b7943a1e0edde12ef667b6e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68047120"
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
  
 Incluent des fonctions MDX qui parcourir un ensemble la [générer](../mdx/generate-mdx.md) (fonction).  
  
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
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
