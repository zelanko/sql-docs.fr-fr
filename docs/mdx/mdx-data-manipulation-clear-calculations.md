---
title: L’instruction CLEAR CALCULATIONS (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CLEAR CALCULATIONS
- clalculations
- clear
dev_langs:
- kbMDX
helpviewer_keywords:
- clearing calculations
- CLEAR CALCULATIONS statement
- deleting calculations
- removing calculations
- calculations [Analysis Services], clearing
- cubes [Analysis Services], calculations
ms.assetid: aebec9a1-1d1d-4697-aa3f-cc2449625603
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 84cfc46ea64b0d4fb1dd79532bc6bdba9af71ded
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-manipulation---clear-calculations"></a>Manipulation de données MDX - CLEAR CALCULATIONS
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Supprime tous les calculs du cube et retourne le cube au test de calcul 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CLEAR CALCULATIONS [FROMCube_Expression]  
```  
  
## <a name="arguments"></a>Arguments  
 *Cube_Expression*  
 Expression de cube MDX (Multidimensional Expressions) valide.  
  
## <a name="remarks"></a>Notes  
 Le **FROM** clause peut être omise lorsque le contexte du cube est connu, par exemple, dans un script MDX.  
  
> [!NOTE]  
>  Cette instruction peut uniquement être exécutée par l'administrateur d'un serveur ou d'une base de données, ou bien par le membre d'un rôle ayant accès aux données source du cube (soit ReadSourceData=true)  
  
## <a name="see-also"></a>Voir aussi  
 [Les instructions de Manipulation de données MDX &#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
