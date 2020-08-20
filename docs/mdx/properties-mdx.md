---
description: Properties (MDX)
title: Propriétés (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d571ed020c1b36ea2e09beca7d2ccbef5899951f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500472"
---
# <a name="properties-mdx"></a>Properties (MDX)


  Retourne une chaîne ou une valeur fortement typée, contenant une valeur de propriété de membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.Properties(Property_Name [, TYPED])  
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
 *Property_Name*  
 Expression de chaîne valide du nom d'une propriété de membre.  
  
## <a name="remarks"></a>Notes  
 La fonction **Properties** retourne la valeur du membre spécifié pour la propriété de membre spécifiée. La propriété de membre peut être n’importe laquelle des propriétés de membre intrinsèques, telles que le **nom**, l' **ID**, la **clé**ou la **légende**, ou elle peut être une propriété de membre définie par l’utilisateur. Pour plus d’informations, consultez [Propriétés de membre intrinsèques &#40;&#41;MDX ](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties) et [Propriétés de membre définies par l’utilisateur &#40;&#41;MDX ](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties).  
  
 Par défaut, la valeur est définie comme une chaîne. Si l' **entrée** est spécifiée, la valeur de retour est fortement typée.  
  
-   Si le type de propriété est intrinsèque, la fonction retourne le type d'origine du membre.  
  
-   Si le type de propriété est défini par l’utilisateur, le type de la valeur de retour est le même que le type de la valeur de retour de la fonction **MemberValue** .  
  
> [!NOTE]  
>  Properties('Key') retourne le même résultat que Key0, sauf en ce qui concerne les clés composites. Properties('Key') retourne la valeur Null pour les clés composites. Utilisez la syntaxe Key*x* pour les clés composites, comme illustré dans l’exemple. Properties('Key0'), Properties('Key1'), Properties('Key2'), etc., forment collectivement la clé composite.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne à la fois des propriétés de membres intrinsèques et définies par l'utilisateur en se servant de l'argument TYPED pour retourner la valeur fortement typée de la propriété de membre Day Name (Jour).  
  
```  
WITH MEMBER Measures.MemberName AS   
   [Date].[Calendar].[July 1, 2003].Properties('Name')  
MEMBER Measures.MemberVal AS   
   [Date].[Calendar].[July 1, 2003].Properties('Member_Value')  
MEMBER Measures.MemberKey AS   
   [Date].[Calendar].[July 1, 2003].Properties('Key')  
MEMBER Measures.MemberID AS   
   [Date].[Calendar].[July 1, 2003].Properties('ID')  
MEMBER Measures.MemberCaption AS   
   [Date].[Calendar].[July 1, 2003].Properties('Caption')  
MEMBER Measures.DayName AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day Name', TYPED)  
MEMBER Measures.DayNameTyped AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day Name')  
MEMBER Measures.DayofWeek AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Week')  
MEMBER Measures.DayofMonth AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Month')  
MEMBER Measures.DayofYear AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Year')  
  
SELECT {Measures.MemberName  
   , Measures.MemberVal  
   , Measures.MemberKey  
   , Measures.MemberID  
   , Measures.MemberCaption  
   , Measures.DayName  
   , Measures.DayNameTyped  
   , Measures.DayofWeek  
   , Measures.DayofMonth  
   , Measures.DayofYear  
   }  ON 0  
FROM [Adventure Works]  
```  
  
 L’exemple suivant illustre l’utilisation de la propriété KEY*x* .  
  
```  
WITH   
MEMBER Measures.MemberKey AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key')  
MEMBER Measures.MemberKey0 AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key0')  
MEMBER Measures.MemberKey1 AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key1')  
  
SELECT {Measures.MemberKey  
   , Measures.MemberKey0  
   , Measures.MemberKey1     
   }  ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des propriétés de membre &#40;MDX&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-member-properties)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
