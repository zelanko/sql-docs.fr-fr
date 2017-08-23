---
title: RollupChildren (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ROLLUPCHILDREN
dev_langs:
- kbMDX
helpviewer_keywords:
- RollupChildren function
ms.assetid: 6f092540-067d-443f-b631-8523836a0d86
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b29a351d8425d235adc29b8a5b997915b70de047
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="rollupchildren-mdx"></a>RollupChildren (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
|Opérateur|Résultat|  
|--------------|------------|  
|**+**|total = total + enfant actuel|  
|**-**|total = total - enfant actuel|  
|**\***|total = total * enfant actuel|  
|**/**|total = total / enfant actuel|  
|**%**|total = (total / enfant actuel) * 100|  
|**~**|L’enfant n’est pas utilisé dans le correctif cumulatif. Sa valeur est ignorée.|  
  
 Si l'opérateur dans la propriété de membre ne figure pas dans la liste, une erreur se produit. L'ordre d'évaluation est déterminé par l'ordre des frères, et non par la priorité des opérateurs.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous utilise une propriété de membre appelée « Alternate Rollup Operator » qui contient des valeurs alternatives permettant aux opérateurs unaires de cumuler les enfants de la hiérarchie Net Profit dans la dimension Account de manière alternative. Cette propriété de membre n'existe pas dans le cube Adventure Works mais peut être créée. Cette utilisation de la **RollupChildren** fonction peut être utilisée dans une application de budgétisation pour l’analyse de simulation.  
  
```  
RollupChildren  
   ( [Account].[Net Profit]  
   , [Account].CurrentMember.Properties ('Alternate Rollup Operator') )  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

