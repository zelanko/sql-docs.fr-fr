---
title: Hierarchize (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- HIERARCHIZE
dev_langs:
- kbMDX
helpviewer_keywords:
- Hierarchize function
ms.assetid: e9795003-70e7-4b4c-9074-45b5b9b817fa
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d0c093d032b587a8935d12c8234ab33da52ee86d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="hierarchize-mdx"></a>Hierarchize (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ordonne les membres d'un jeu en hiérachie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Hierarchize(Set_Expression [ , POST ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 Le **Hierarchize** fonction organise les membres du jeu spécifié en ordre hiérarchique. La fonction conserve toujours les doublons.  
  
-   Si **POST** n’est pas spécifié, la fonction trie les membres d’un niveau dans leur ordre naturel. Leur ordre naturel est l'ordre par défaut des membres dans la hiérarchie lorsque aucune condition de tri n'est spécifiée. Les membres enfants suivent immédiatement leurs membres parents.  
  
-   Si **POST** est spécifié, le **Hierarchize** fonction trie les membres d’un niveau à l’aide d’un ordre post-naturel. En d'autres termes, les membres enfants précèdent leurs parents.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous remonte d'un niveau vers le membre Canada. Le **Hierarchize** fonction est utilisée pour organiser les membres du jeu spécifié dans l’ordre hiérarchique, ce qui est requis par le **DrillUpMember** (fonction).  
  
```  
SELECT DrillUpMember   
   (  
      Hierarchize  
         (  
            {[Geography].[Geography].[Country].[Canada]  
            ,[Geography].[Geography].[Country].[United States]  
            ,[Geography].[Geography].[State-Province].[Alberta]  
            ,[Geography].[Geography].[State-Province].[Brunswick]  
            ,[Geography].[Geography].[State-Province].[Colorado]   
            }  
         ), {[Geography].[Geography].[Country].[United States]}  
   )  
ON 0  
FROM [Adventure Works]  
```  
  
 L’exemple suivant retourne la somme de la `Measures.[Order Quantity]` membre, agrégé sur les neuf premiers mois de 2003 contenus dans le `Date` dimension, à partir de la **Adventure Works** cube. Le **PeriodsToDate** fonction définit les tuples dans le jeu sur lequel la fonction Aggregate opère. Le **Hierarchize** fonction organise les membres du jeu spécifié de membres à partir de la dimension Product dans l’ordre hiérarchique.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS Count  
   (Filter  
      (Existing  
         (Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] <   
               ([Measures].[Reseller Sales Amount],[Date].Calendar.PrevMember)  
        )  
    )  
MEMBER [Geography].[State-Province].x AS Aggregate   
( {[Geography].[State-Province].&[WA]&[US],   
   [Geography].[State-Province].&[OR]&[US] }   
)  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})}  
        )  
    ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
   [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

