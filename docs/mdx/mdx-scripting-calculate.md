---
title: Instruction CALCULATE (MDX) | Documents Microsoft
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
- CALCULATE
dev_langs:
- kbMDX
helpviewer_keywords:
- CALCULATE statement
ms.assetid: 41e196a1-d49e-487b-a42a-73e5d441ed1b
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d8e74fd0cd09e050c11d2eb403d31527402f008b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-scripting---calculate"></a>Écriture de scripts MDX - calculer
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Remplit chaque cellule d'un cube d'une valeur d'agrégation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CALCULATE  
```  
  
## <a name="arguments"></a>Arguments  
 Aucun  
  
## <a name="remarks"></a>Notes  
 L'instruction CALCULATE est automatiquement incluse en tant que première instruction d'un script MDX d'un cube lorsque vous créez un cube à l'aide de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Elle indique à chaque cellule au sein du cube de s'agréger à partir de cellules de granularité plus faible. Après avoir agrégé une cellule, si vous remplissez par la suite les cellules à plus faible granularité à l'aide d'expressions, cette opération aura une incidence sur la valeur agrégée des cellules à plus forte granularité. Cette agrégation est quasiment toujours souhaitable mais vous pouvez la supprimer ou forcer l'exécution d'autres instructions avant cette instruction.  
  
 L'instruction CALCULATE ne peut être intégrée à un sous-cube imbriqué au sein du script MDX. Un sous-cube imbriqué se définit à l'aide de l'instruction SCOPE. Pour plus d’informations sur l’instruction SCOPE, consultez [instruction SCOPE &#40; MDX &#41; ](../mdx/mdx-scripting-scope.md).  
  
> [!NOTE]  
>  Les membres calculés ne sont pas agrégés.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de script MDX &#40; MDX &#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [Principes de base de script MDX &#40; Analysis Services &#41;](../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [Définir des attributions et autres commandes de Script](../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md)  
  
  

