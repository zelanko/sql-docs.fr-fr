---
title: '! (Non logique) (expression SSIS) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- logical Not (!)
- '! (logical Not)'
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 30d3e56f69335b4dc90f7af31790c3c1e02242de
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48169115"
---
# <a name="-logical-not-ssis-expression"></a>! (Non logique) (expression SSIS)
  Inverse un opérande booléen.  
  
> [!NOTE]  
>  L'opérateur « ! » ne peut pas être utilisé en combinaison avec d'autres opérateurs. Par exemple, vous ne pouvez pas combiner les opérateurs « ! » et > pour former l'opérateur « !> » .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
!boolean_expression  
  
```  
  
## <a name="arguments"></a>Arguments  
 *boolean_expression*  
 Toute expression valide qui s'évalue à une valeur booléenne. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types de résultats  
 DT_BOOL  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant indique le résultat de l'opération « ! » publication.  
  
|Expression booléenne initiale|Après application de l'opérateur « ! » operator|  
|---------------------------------|------------------------------------|  
|TRUE|FALSE|  
|NULL|NULL|  
|FALSE|TRUE|  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L’exemple suivant donne la valeur FALSE si la colonne **Color** a pour valeur « red ».  
  
```  
!(Color == "red")  
```  
  
 L’exemple suivant donne la valeur TRUE si la valeur de la variable **MonthNumber** et celle de l’entier qui représente le mois actuel sont identiques. Pour plus d’informations, consultez [MONTH &#40;expression SSIS&#41;](month-ssis-expression.md) et [GETDATE &#40;expression SSIS&#41;](getdate-ssis-expression.md).  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs et associativité](operator-precedence-and-associativity.md)   
 [Opérateurs &#40;SSIS Expression&#41;](operators-ssis-expression.md)  
  
  
