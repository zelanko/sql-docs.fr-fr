---
title: CalculationCurrentPass (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: CALCULATIONCURRENTPASS
dev_langs: kbMDX
helpviewer_keywords: CalculationCurrentPass function
ms.assetid: 7069f7a0-8ec8-4293-8db3-b35b9327f437
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 675c708517d2624919c926248a91455842111ac4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="calculationcurrentpass-mdx"></a>CalculationCurrentPass (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le test de calcul actuel d'un cube pour le contexte de requête spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CalculationCurrentPass()  
```  
  
## <a name="remarks"></a>Notes  
 Le **CalculationCurrentPass** fonction retourne l’index de base zéro de la passe de calcul pour le contexte de requête actuel. Avec une résolution automatique de la récursivité dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], cette fonction a peu utilisation pratique.  
  
## <a name="see-also"></a>Voir aussi  
 [CalculationPassValue &#40; MDX &#41;](../mdx/calculationpassvalue-mdx.md)   
 [IIf &#40; MDX &#41;](../mdx/iif-mdx.md)   
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
