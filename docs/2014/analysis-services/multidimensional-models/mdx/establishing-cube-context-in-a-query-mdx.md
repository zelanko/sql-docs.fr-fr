---
title: Définition d’un contexte de Cube dans une requête (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cubes [Analysis Services], MDX
- MDX [Analysis Services], cube context
- SELECT statement [MDX]
- Multidimensional Expressions [Analysis Services], cube context
- queries [MDX], cube context
ms.assetid: 79d6a1e8-2825-4eb9-97df-5071aecae8f0
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 972b630aea4ebcc427803e226d27d52f919da4a0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139680"
---
# <a name="establishing-cube-context-in-a-query-mdx"></a>Définition d'un contexte de cube dans une requête (MDX)
  Chaque requête MDX s'exécute dans un contexte de cube spécifié. Ce contexte définit les membres qui sont évalués par les expressions incluses dans la requête.  
  
 Dans l'instruction SELECT, la clause FROM détermine le contexte de cube. Ce contexte peut être le cube complet ou seulement un sous-cube de ce cube. Après avoir spécifié le contexte de cube à l'aide de la clause FROM, vous pouvez utiliser d'autres fonctions pour développer ou restreindre ce contexte.  
  
> [!NOTE]  
>  Les instructions SCOPE et CALCULATE vous permettent également de gérer le contexte de cube à l'intérieur d'un script MDX. Pour plus d’informations, consultez [Principes de base des scripts MDX &#40;Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md).  
  
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
  
 Pour plus d’informations sur la clause FROM de l’instruction MDX SELECT, consultez [Instruction SELECT &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select).  
  
## <a name="refining-the-context"></a>Affinement du contexte  
 Bien que la clause FROM spécifie le contexte de cube comme dans un cube unique, cela ne doit pas vous empêcher d'utiliser simultanément des données issues de plusieurs cubes.  
  
 Vous pouvez utiliser la fonction [LookupCube](/sql/mdx/lookupcube-mdx) MDX pour récupérer des données de cubes en dehors du contexte des cubes. De plus, il existe des fonctions telles que [Filter](/sql/mdx/filter-mdx) qui permettent de restreindre temporairement le contexte durant l’évaluation de la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base de requête MDX &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
