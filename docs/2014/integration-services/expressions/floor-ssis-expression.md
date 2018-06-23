---
title: FLOOR (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- largest integer less than or equal to expression
- FLOOR function [SSIS]
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: cae43e01a262258fa2fce824797b3d20682c3829
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043890"
---
# <a name="floor-ssis-expression"></a>FLOOR (expression SSIS)
  Renvoie l'entier le plus élevé inférieur ou égal à une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Expression numérique valide.  
  
## <a name="result-types"></a>Types de résultats  
 Type de données numérique de l'expression de l'argument. Le résultat est la partie entière de la valeur calculée dans le même type de données que *numeric_expression.*  
  
## <a name="remarks"></a>Notes  
 La fonction FLOOR renvoie un résultat NULL si l'argument est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Les exemples suivants appliquent la fonction FLOOR à une valeur successivement positive, négative et nulle.  
  
```  
FLOOR(123.45)  
```  
  
 Retourne 123.00  
  
```  
FLOOR(-123.45)  
```  
  
 Retourne -124.00  
  
```  
FLOOR(0.00)  
```  
  
 Renvoie 0,00  
  
## <a name="see-also"></a>Voir aussi  
 [PLAFOND &#40;Expression SSIS&#41;](ceiling-ssis-expression.md)   
 [Fonctions &#40;Expression SSIS&#41;](functions-ssis-expression.md)  
  
  