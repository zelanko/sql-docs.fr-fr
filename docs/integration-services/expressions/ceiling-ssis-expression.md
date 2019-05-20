---
title: CEILING (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b0b9c9c7ab5ed0067d86b3beaa69461ab6e90672
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65725574"
---
# <a name="ceiling-ssis-expression"></a>CEILING (expression SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Renvoie le plus petit entier qui est supérieur ou égal à une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CEILING(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Expression numérique valide.  
  
## <a name="result-types"></a>Types des résultats  
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
  
## <a name="see-also"></a> Voir aussi  
 [FLOOR &#40;expression SSIS&#41;](../../integration-services/expressions/floor-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
