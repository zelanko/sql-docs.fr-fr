---
title: EXP (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- exponential functions
- EXP function
ms.assetid: 4cd96d3c-58c9-4a67-a6f6-b72758232912
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 17fb9a07b4121c0ed49e865f6786d12a42d14e81
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229369"
---
# <a name="exp-ssis-expression"></a>EXP (expression SSIS)
  Renvoie l'exposant en base e d'une expression numérique. La fonction EXP est complémentaire de l'action LN et est parfois appelée « antilogarithme ».  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
EXP(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Expression numérique valide.  
  
## <a name="result-types"></a>Types de résultats  
 DT_R8  
  
## <a name="remarks"></a>Notes  
 L'expression numérique est convertie vers le type de données DT_R8 avant le calcul du l'exposant. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
 Le résultat obtenu est toujours un nombre positif.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Les exemples suivants appliquent la fonction EXP à des valeurs positive, négative, ainsi qu'à la valeur zéro.  
  
```  
EXP(74)  
```  
  
 Renvoie 1,373382979540176E+32.  
  
```  
EXP(-27)  
```  
  
 Renvoie 1,879528816539083E-12.  
  
```  
EXP(0)  
```  
  
 Renvoie 1.  
  
## <a name="see-also"></a>Voir aussi  
 [JOURNAL &#40;SSIS Expression&#41;](log-ssis-expression.md)   
 [Fonctions &#40;SSIS Expression&#41;](functions-ssis-expression.md)  
  
  
