---
title: Utilisation d’expressions de membre | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8d40d6a3b6cacb65cf1463b0eeb8b29e59e079e4
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893513"
---
# <a name="using-member-expressions"></a>Utilisation d'expressions de membre


  Une expression de membre contient un identificateur de membre, une fonction membre ou une expression pouvant être convertie en membre.  
  
 Les identificateurs de membre sont disponibles dans plusieurs formats. La forme la plus simple d'un identificateur de membre se compose du nom du membre. Exemple :  
  
```  
SELECT Amount ON 0  
FROM [Adventure Works]  
  
```  
  
 Toutefois, en présence de plusieurs membres avec le même nom sur des hiérarchies différentes, il n'existe aucune méthode pour déterminer quel membre est retourné par la requête. Par exemple, la requête suivante demande des données pour un membre avec le nom [CY 2004]. La requête s'exécute correctement, mais il existe au moins six membres avec ce nom dans le cube Adventure Works :  
  
```  
SELECT [CY 2004] ON 0  
FROM [Adventure Works]  
  
```  
  
 Par conséquent, le formulaire le plus fiable de l'identificateur membre est le nom unique du membre qui permet d'identifier un membre spécifique dans un cube. Analysis Services peut générer des noms uniques de plusieurs façons, mais un nom unique est toujours composé d'au moins deux identificateurs : le nom de la dimension et le nom ou la clé du membre. Un nom unique se présente sous la forme suivante :  
  
```  
  
Dimension_Name  
.[Hierarchy_Name.] [[{Member_Name | &Member_Key}.]... ] {Member_Name | &Member_Key}  
  
```  
  
 Voici des exemples de noms uniques de membre du cube Adventure Works :  
  
```  
[Measures].[Amount]  
[Date].[Calendar Year].&[2004]  
[Date].[Calendar].[Calendar Quarter].&[2004]&[1]  
[Employee].[Employees].&[112]  
[Product].[Product Categories].[All Products]  
  
```  
  
 De nombreuses fonctions MDX retournent des membres. Pour obtenir une liste complète, consultez MDX [Function &#40;Reference&#41; MDX](../mdx/mdx-function-reference-mdx.md)  
  
> [!NOTE]  
>  Pour plus d’informations sur les noms de membres et les clés de membre, consultez [utilisation de membres, &#40;de&#41;tuples et de paramètres MDX](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx).  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions &#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
