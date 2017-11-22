---
title: "Frères (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: SIBLINGS
dev_langs: kbMDX
helpviewer_keywords: Siblings function
ms.assetid: 33e63808-f07e-44f7-8dfa-4dd9fd89ec82
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 367c45f4dc07df267a2a3b64ebe84bf92b70f857
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="siblings-mdx"></a>Siblings (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne les frères d'un membre spécifié, notamment le membre lui-même.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.Siblings   
```  
  
## <a name="arguments"></a>Arguments  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
### <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne la mesure par défaut des frères du mois de mars 2003, soit les mois de janvier, février et mars 2003 inclus.  
  
```  
SELECT [Date].[Calendar].[Month].[March 2003].Siblings ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
