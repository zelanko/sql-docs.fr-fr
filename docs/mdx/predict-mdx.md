---
title: "Prédire (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: PREDICT
dev_langs: kbMDX
helpviewer_keywords: Predict function
ms.assetid: a82f3edd-249b-4559-98d3-6e10d81a095d
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: c06caa21c9bfcd041cfd25df17d134a317d518fb
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="predict-mdx"></a>Predict (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!CAUTION]  
>  Cette fonction est en cours de suppression en raison d'incohérences internes.  
>   
>  Passez en revue la section d'exemple pour connaître la solution de contournement en cas d'utilisation d'une expression DMX.  
  
 Retourne une valeur d'expression numérique évaluée sur un modèle d'exploration de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Predict(Mining_Model_Name,String_Expression)   
```  
  
## <a name="arguments"></a>Arguments  
 *Mining_Model_Name*  
 Expression de chaîne valide qui représente le nom d'un modèle d'exploration.  
  
 *String_Expression*  
 Expression de chaîne valide qui prend la valeur d'une expression DMX valide pour le modèle d'exploration de données spécifié.  
  
## <a name="remarks"></a>Notes  
 Le **Predict** fonction évalue l’expression de chaîne spécifiée dans le contexte du modèle d’exploration de données spécifié.  
  
 La syntaxe et les fonctions d'exploration de données sont documentées dans les références MDX (Multidimensional Expressions).  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous cite en prévision le nom du cluster et la distance qui le sépare d'un client particulier à l'aide du modèle d'exploration de données des clusters du client :  
  
```  
WITH MEMBER MEASURES.CLNAME AS   
PREDICT("Customer Clusters", "Cluster()")  
MEMBER MEASURES.CLDISTANCE AS   
PREDICT("Customer Clusters", "ClusterDistance(Cluster())")  
SELECT {MEASURES.CLNAME, MEASURES.CLDISTANCE} ON 0   
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Customer].&[12012])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
