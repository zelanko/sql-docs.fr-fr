---
title: Instruction DROP ACTION (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP
- DROP ACTION
- Action
- DROP_ACTION
dev_langs: kbMDX
helpviewer_keywords:
- DROP ACTION statement
- deleting actions
- removing actions
- actions [MDX]
- dropping actions
ms.assetid: 74b3cfee-dea8-4968-a54c-1754d52ee1bd
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 22233dcfb79c9e2cf86e0c9fd7168ae321ed2034
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="mdx-data-definition---drop-action"></a>Définition de données MDX - ACTION DROP
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime une action spécifiée d'un cube spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP ACTION CURRENTCUBE | Cube_Name  
   .Action_Name   
```  
  
## <a name="arguments"></a>Arguments  
 *Cube_Name*  
 Une expression de chaîne valide qui fournit le nom du cube.  
  
 *Action_Name*  
 Expression de chaîne valide qui précise le nom de l'action supprimée.  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER une instruction ACTION &#40; MDX &#41;](../mdx/mdx-data-definition-create-action.md)   
 [Instructions MDX de définition de données &#40; MDX &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
