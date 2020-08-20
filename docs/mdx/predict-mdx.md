---
description: Predict (MDX)
title: Prédiction (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 97d65cec90020b14bba242b4183ada8f02c2c368
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471671"
---
# <a name="predict-mdx"></a>Predict (MDX)


    
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
 La fonction **Predict** évalue l’expression de chaîne spécifiée dans le contexte du modèle d’exploration de données spécifié.  
  
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
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
