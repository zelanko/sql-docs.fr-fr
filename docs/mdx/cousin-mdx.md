---
title: Cousin (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: COUSIN
dev_langs: kbMDX
helpviewer_keywords: Cousin function
ms.assetid: 9a416685-d35d-4d9c-a9f6-4574cbe59aea
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a15b6a97574e9e4abde7bfd5606bd08a57b27529
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="cousin-mdx"></a>Cousin (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le membre enfant avec la même position relative sous un membre parent que le membre enfant spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Cousin( Member_Expression , Ancestor_Member_Expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
 *Ancestor_Member_Expression*  
 Expression de membre MDX (Multidimensional Expressions) valide qui retourne un membre ancêtre.  
  
## <a name="remarks"></a>Notes  
 Cette fonction agit sur l'ordre et la position des membres au sein des niveaux. En présence de deux hiérarchies, lorsque la première possède quatre niveaux et la deuxième cinq, le cousin du troisième niveau de la première hiérarchie est le troisième niveau de la deuxième hiérarchie.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous récupère le cousin du quatrième trimestre de l'année fiscale 2002 en se basant sur son ancêtre au niveau de l'année fiscale 2003. Le cousin récupéré est le quatrième trimestre de l'année fiscale 2003.  
  
```  
SELECT Cousin   
   ( [Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002],  
     [Date].[Fiscal].[FY 2003]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
 L'exemple ci-dessous récupère le cousin du mois de juillet de l'année fiscale 2002 en se basant sur son ancêtre au niveau du deuxième trimestre de l'année fiscale 2004. Le cousin récupéré est le mois d'octobre 2003.  
  
```  
SELECT Cousin   
   ([Date].[Fiscal].[Month].[July 2002] ,  
    [Date].[Fiscal].[Fiscal Quarter].[Q2 FY 2004]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
