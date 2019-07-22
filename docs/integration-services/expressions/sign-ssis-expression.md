---
title: SIGN (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
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
ms.openlocfilehash: 962f92044ea81cb7bb420176103a3df63c4b7ddd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67967809"
---
# <a name="sign-ssis-expression"></a>SIGN (expression SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Renvoie le nombre positif (+1), le nombre négatif (-1) ou zéro (0) selon le signe d'une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SIGN(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Expression numérique signée valide. Pour plus d’informations, consultez [Types de données Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
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
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
