---
title: CEILING (expression SSIS) | Microsoft Docs
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
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6b7b6afd3879805c0badc1c15e6113971dcb776a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043397"
---
# <a name="ceiling-ssis-expression"></a>CEILING (expression SSIS)
  Renvoie le plus petit entier qui est supérieur ou égal à une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CEILING(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Expression numérique valide.  
  
## <a name="result-types"></a>Types de résultats  
 Type de données de l'expression numérique envoyée à la fonction.  
  
## <a name="remarks"></a>Notes  
 La fonction CEILING renvoie un résultat NULL si l'argument est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Les exemples suivants appliquent la fonction CEILING à une valeur successivement positive, négative et nulle.  
  
```  
CEILING(123.74)  
```  
  
 Retourne 124.00  
  
```  
CEILING(-124.27)  
```  
  
 Retourne -124.00  
  
```  
CEILING(0.00)  
```  
  
 Renvoie 0,00  
  
## <a name="see-also"></a>Voir aussi  
 [FLOOR &#40;Expression SSIS&#41;](floor-ssis-expression.md)   
 [Fonctions &#40;Expression SSIS&#41;](functions-ssis-expression.md)  
  
  