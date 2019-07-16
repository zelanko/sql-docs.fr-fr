---
title: Utilisation d’Expressions de membre | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 41ff63d47a62b9b83fb583c55ff2405638de22cf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097112"
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
  
 De nombreuses fonctions MDX retournent des membres. Pour obtenir la liste complète, consultez [référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
> [!NOTE]  
>  Pour plus d’informations sur les noms de membre et les clés de membre, consultez [utilisation de membres, Tuples et jeux &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions &#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
