---
title: Dimensions (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b2703122b67debf0749abcd2ea01114fb6ecaa06
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63248147"
---
# <a name="dimensions-mdx"></a>Dimensions (MDX)


  Retourne la hiérarchie spécifiée par une expression numérique ou de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Numeric expression syntax  
Dimensions(Hierarchy_Number)  
  
String expression syntax  
Dimensions(Hierarchy_Name)  
```  
  
## <a name="arguments"></a>Arguments  
 *Hierarchy_Number*  
 Expression numérique valide qui spécifie un numéro de hiérarchie.  
  
 *Hierarchy_Name*  
 Expression de chaîne valide qui spécifie un nom de hiérarchie.  
  
## <a name="remarks"></a>Notes  
 Si un numéro de hiérarchie est spécifié, le **Dimensions** fonction retourne une hiérarchie dont la position de base zéro dans le cube est spécifiée de numéro de hiérarchie.  
  
 Si un nom de la hiérarchie est spécifié, le **Dimensions** fonction retourne la hiérarchie spécifiée. En général, vous utilisez cette version de chaîne de la **Dimensions** fonction avec les fonctions définies par l’utilisateur.  
  
> [!NOTE]  
>  Le **mesures** dimension est toujours représentée par `Dimensions(0)`.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants utilisent le **Dimensions** fonction pour retourner le nom, le nombre de niveaux et le nombre de membres d’une hiérarchie spécifiée, à l’aide d’une expression numérique et une expression de chaîne.  
  
```  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Levels.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Members.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Levels.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
