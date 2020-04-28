---
title: AddCalculatedMembers (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 982484b729b59a7106b6195e361110c1d4012653
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68017186"
---
# <a name="addcalculatedmembers-mdx"></a>AddCalculatedMembers (MDX)


  Retourne un jeu généré par l'ajout de membres calculés à un jeu spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
AddCalculatedMembers(Set_Expression)   
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 Par défaut, MDX exclut les membres calculés lorsqu'il résout des fonctions Set. La fonction **AddCalculatedMembers** examine l’expression d’ensemble spécifiée dans *set_expression,* et comprend les membres calculés qui sont des frères des membres contenus dans la portée de cette expression d’ensemble.  
  
> [!NOTE]  
>  Cette fonction ne peut être utilisée qu'avec des expressions d'ensemble unidimensionnelles.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de cette fonction.  
  
```  
-- This query returns the calculated members for the cube  
-- by retrieving all members, and then excluding non-calculated members.  
SELECT   
   AddCalculatedMembers(  
      {[Measures].Members}  
      )-[Measures].Members ON COLUMNS  
FROM [Adventure Works]   
```  
  
 L’exemple suivant retourne le `Measures.[Unit Price]` membre, en plus de tous les membres calculés de la dimension **Measures** , à partir du cube **Adventure Works** .  
  
```  
SELECT  
   AddCalculatedMembers({Measures.[Unit Price]}) ON COLUMNS  
FROM   
   [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
