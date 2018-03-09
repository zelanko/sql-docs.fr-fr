---
title: RollupChildren (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ROLLUPCHILDREN
dev_langs: kbMDX
helpviewer_keywords: RollupChildren function
ms.assetid: 6f092540-067d-443f-b631-8523836a0d86
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: e3553458eecb094ec76ecb6bf7f65691aaa1c4bd
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="rollupchildren-mdx"></a>RollupChildren (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne une valeur générée par le cumul des valeurs des enfants d'un membre spécifié à l'aide de l'opérateur unaire spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RollupChildren(Member_Expression, Unary_Operator)   
```  
  
## <a name="arguments"></a>Arguments  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
 *Unary_Operator*  
 Expression de chaîne valide qui spécifie un opérateur unaire.  
  
## <a name="remarks"></a>Notes   
 Le **RollupChildren** fonction cumule les valeurs des enfants du membre spécifié à l’aide de l’opérateur unaire spécifié.  
  
 Le tableau ci-dessous décrit les opérateurs unaires valides pour cette fonction.  
  
|Opérateur|Résultats|  
|--------------|------------|  
|**+**|total = total + enfant actuel|  
|**-**|total = total - enfant actuel|  
|**\***|total = total * enfant actuel|  
|**/**|total = total / enfant actuel|  
|**%**|total = (total / enfant actuel) * 100|  
|**~**|L’enfant n’est pas utilisé dans le correctif cumulatif. Sa valeur est ignorée.|  
  
 Si l'opérateur dans la propriété de membre ne figure pas dans la liste, une erreur se produit. L'ordre d'évaluation est déterminé par l'ordre des frères, et non par la priorité des opérateurs.  
  
## <a name="example"></a> Exemple  
 L'exemple ci-dessous utilise une propriété de membre appelée « Alternate Rollup Operator » qui contient des valeurs alternatives permettant aux opérateurs unaires de cumuler les enfants de la hiérarchie Net Profit dans la dimension Account de manière alternative. Cette propriété de membre n'existe pas dans le cube Adventure Works mais peut être créée. Cette utilisation de la **RollupChildren** fonction peut être utilisée dans une application de budgétisation pour l’analyse de simulation.  
  
```  
RollupChildren  
   ( [Account].[Net Profit]  
   , [Account].CurrentMember.Properties ('Alternate Rollup Operator') )  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
