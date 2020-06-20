---
title: SIGN (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- positive values [Integration Services]
- SIGN function
- negative values
ms.assetid: 1547db08-4329-4781-91c2-36898ed71b15
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 42b0e1d2c91bf7c66065fc8c5a3bcee03e8475c6
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966579"
---
# <a name="sign-ssis-expression"></a>SIGN (expression SSIS)
  Renvoie le nombre positif (+1), le nombre négatif (-1) ou zéro (0) selon le signe d'une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SIGN(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Expression numérique signée valide. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types des résultats  
 DT_I4  
  
## <a name="remarks"></a>Notes  
 La fonction SIGN renvoie un résultat NULL si l'argument est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant renvoie le signe d'un littéral numérique. Le résultat obtenu est -1.  
  
```  
SIGN(-123.45)  
```  
  
 L’exemple suivant retourne le signe du résultat de la soustraction de la colonne **StandardCost** de la colonne **DealerPrice** .  
  
```  
SIGN(DealerPrice - StandardCost)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)  
  
  
