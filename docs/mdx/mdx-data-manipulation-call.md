---
title: "L’instruction CALL (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CALL
dev_langs:
- kbMDX
helpviewer_keywords:
- voids [MDX]
- stored procedures [MDX]
- CALL statement
ms.assetid: b534a20b-924c-43b8-832d-24e57d50425c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3d5bc0d9875d602135fd92722b73c07176a1df59
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-manipulation---call"></a>Manipulation de données MDX - appel
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Exécute une procédure stockée qui retourne une valeur vide soit dans l'étendue actuelle soit, éventuellement, sur un cube spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CALL SP_Name   
   [ (SP_Argument   
      [, SP_Argument ,...n]  
      ) ]   
[ONCube_Expression]  
```  
  
## <a name="arguments"></a>Arguments  
 *SP_Name*  
 Chaîne d'expression valide qui précise le nom d'une procédure stockée.  
  
 *SP_Argument*  
 Chaîne d'expression valide qui précise un argument pour la procédure stockée appelée.  
  
 *Cube_Expression*  
 Expression de cube de chaîne valide qui précise le nom du cube.  
  
## <a name="remarks"></a>Notes  
 Le **appeler** instruction exécute une procédure stockée inscrite spécifiée, comprenant éventuellement un ou plusieurs arguments pour la procédure stockée spécifiée. Le **appeler** instruction doit être utilisé uniquement avec des procédures stockées qui retournent des valeurs vides. Cette instruction ne peut pas être combinée avec d'autres fonctions ou opérateurs au sein d'une expression MDX. Les procédures stockées enregistrées qui retournent des valeurs peuvent être appelées directement au sein d'expressions MDX et combinées avec d'autres fonctions et opérateurs MDX.  
  
 Si aucun cube n'est spécifié, l'instruction exécute la procédure stockée sur le cube actuel.  
  
> [!NOTE]  
>  Si la procédure stockée n’est pas inscrit sur le client, le **appeler** instruction tente d’appeler la procédure stockée à partir d’une instance de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions MDX de Manipulation de données &#40; MDX &#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [À l’aide de procédures stockées &#40; MDX &#41;](../mdx/using-stored-procedures-mdx.md)  
  
  

