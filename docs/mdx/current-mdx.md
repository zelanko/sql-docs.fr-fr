---
title: En cours (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 821d517419b90df44b7943a1e0edde12ef667b6e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
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
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 À chaque étape d'une itération, le tuple utilisé est le tuple actif. La fonction **active** retourne ce tuple. Cette fonction est valide uniquement lors d'une itération sur un jeu.  
  
 Les fonctions MDX qui itèrent au sein d’un jeu incluent la fonction [generate](../mdx/generate-mdx.md) .  
  
> [!NOTE]  
>  Cette fonction agit uniquement avec des jeux nommés, soit par le biais d'un alias spécifique, soit en définissant un jeu nommé.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant montre comment utiliser la fonction **active** dans **generate**:  
  
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
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
