---
title: Niveau (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8406d02e167258901c3a6ce9ed3a1d7de935df54
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741748"
---
# <a name="level-mdx"></a>Level (MDX)


  Retourne le niveau d'un membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.Level  
```  
  
## <a name="arguments"></a>Arguments  
 *Argument*  
 Une valide MDX (Multidimensional Expression) qui retourne un membre.  
  
### <a name="examples"></a>Exemples  
 L’exemple suivant utilise le **niveau** fonction pour retourner tous les mois dans le cube Adventure Works.  
  
```  
SELECT[Date].[Fiscal].[Month].[February 2002].Level.Members ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
 L’exemple suivant utilise le **niveau** fonction pour retourner le nom du niveau d’All-Purpose Bike Stand dans la hiérarchie d’attribut de nom du modèle dans le cube Adventure Works.  
  
```  
WITH MEMBER Measures.x AS   
   [Product].[Model Name].[All-Purpose Bike Stand].Level.Name  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
