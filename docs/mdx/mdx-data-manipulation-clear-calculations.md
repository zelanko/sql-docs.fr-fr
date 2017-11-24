---
title: "L’instruction CLEAR CALCULATIONS (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CLEAR CALCULATIONS
- clalculations
- clear
dev_langs: kbMDX
helpviewer_keywords:
- clearing calculations
- CLEAR CALCULATIONS statement
- deleting calculations
- removing calculations
- calculations [Analysis Services], clearing
- cubes [Analysis Services], calculations
ms.assetid: aebec9a1-1d1d-4697-aa3f-cc2449625603
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 12302161e25d184e3fcffb2ee9d32636208d13a0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="mdx-data-manipulation---clear-calculations"></a>Manipulation de données MDX - CLEAR CALCULATIONS
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [Instructions MDX de Manipulation de données &#40; MDX &#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
