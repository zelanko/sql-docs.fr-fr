---
title: "Définition d’un contexte de Cube dans une requête (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cubes [Analysis Services], MDX
- MDX [Analysis Services], cube context
- SELECT statement [MDX]
- Multidimensional Expressions [Analysis Services], cube context
- queries [MDX], cube context
ms.assetid: 79d6a1e8-2825-4eb9-97df-5071aecae8f0
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1b8d97b906a0ef1121daac5379f4938dfe4b2466
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="establishing-cube-context-in-a-query-mdx"></a>Définition d'un contexte de cube dans une requête (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Chaque requête MDX s’exécute dans un contexte de cube spécifié. Ce contexte définit les membres qui sont évalués par les expressions incluses dans la requête.  
  
 Dans l'instruction SELECT, la clause FROM détermine le contexte de cube. Ce contexte peut être le cube complet ou seulement un sous-cube de ce cube. Après avoir spécifié le contexte de cube à l'aide de la clause FROM, vous pouvez utiliser d'autres fonctions pour développer ou restreindre ce contexte.  
  
> [!NOTE]  
>  Les instructions SCOPE et CALCULATE vous permettent également de gérer le contexte de cube à l'intérieur d'un script MDX. Pour plus d’informations, consultez [Principes de base des scripts MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md).  
  
## <a name="from-clause-syntax"></a>Syntaxe de la clause FROM  
 La syntaxe suivante décrit la clause FROM :  
  
```  
<SELECT subcube clause> ::=  
   Cube_Identifier |   
   (SELECT [  
      * |   
      ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]   
   FROM <SELECT subcube clause> <SELECT slicer axis clause> )  
```  
  
 Dans cette syntaxe, notez que c'est la clause `<SELECT subcube clause>` qui décrit le cube ou le sous-cube sur lequel s'exécute l'instruction SELECT.  
  
 Un exemple simple de clause FROM pourrait s'exécuter sur l'ensemble du cube Adventure Works. Une telle clause FROM aurait le format suivant :  
  
```  
FROM [Adventure Works]  
```  
  
 Pour plus d’informations sur la clause FROM de l’instruction MDX SELECT, consultez [Instruction SELECT &#40;MDX&#41;](../../../mdx/mdx-data-manipulation-select.md).  
  
## <a name="refining-the-context"></a>Affinement du contexte  
 Bien que la clause FROM spécifie le contexte de cube comme dans un cube unique, cela ne doit pas vous empêcher d'utiliser simultanément des données issues de plusieurs cubes.  
  
 Vous pouvez utiliser la fonction [LookupCube](../../../mdx/lookupcube-mdx.md) MDX pour récupérer des données de cubes en dehors du contexte des cubes. De plus, il existe des fonctions telles que [Filter](../../../mdx/filter-mdx.md) qui permettent de restreindre temporairement le contexte durant l’évaluation de la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base des requêtes MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
