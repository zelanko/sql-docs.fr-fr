---
title: Niveau (MDX) | Documents Microsoft
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
- LEVEL
dev_langs:
- kbMDX
helpviewer_keywords:
- Level function
ms.assetid: 10bbe4ac-44bc-45c7-81a1-85423fbeaab1
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 311bbd9138a12d7f4013bd5e21538f9acae59ec9
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="level-mdx"></a>Level (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

