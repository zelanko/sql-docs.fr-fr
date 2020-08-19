---
description: Value (MDX)
title: Valeur (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3d6bf8edd7cbeefefa723c1acc374daa8d2c9407
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449611"
---
# <a name="value-mdx"></a>Value (MDX)


  Retourne la valeur du membre actuel de la dimension de mesures située à l'intersection du membre actuel des hiérarchies d'attribut dans le contexte de la requête.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression[.Value]   
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 La fonction **value** retourne la valeur du membre spécifié sous forme de chaîne. L’argument de **valeur** est facultatif, car la valeur d’un membre est la propriété par défaut d’un membre, et est la valeur retournée pour un membre si aucune autre valeur n’est spécifiée. Pour plus d’informations sur les propriétés des membres, consultez [Propriétés de membre intrinsèques &#40;&#41;MDX ](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties) et [Propriétés de membre définies par l’utilisateur &#40;&#41;MDX ](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties).  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous retourne la valeur d'un membre ainsi que le nom du membre de manière explicite.  
  
```  
WITH MEMBER [Date].[Calendar].NumericValue as [Date].[Calendar].[July 1, 2001].Value  
MEMBER [Date].[Calendar].MemberName AS [Date].[Calendar].[July 1, 2001].Name  
  
SELECT {[Date].[Calendar].NumericValue, [Date].[Calendar].MemberName} ON 0  
from [Adventure Works]  
```  
  
 L'exemple ci-dessous retourne la valeur d'un membre en tant que valeur par défaut retournée pour un membre sur un axe.  
  
```  
SELECT {[Date].[Calendar].[July 1, 2001]} ON 0  
from [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [MemberValue&#41;MDX &#40;](../mdx/membervalue-mdx.md)   
 [Propriétés &#40;MDX&#41;](../mdx/properties-mdx.md)   
 [Nom &#40;&#41;MDX ](../mdx/name-mdx.md)   
 [UniqueName &#40;&#41;MDX ](../mdx/uniquename-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
