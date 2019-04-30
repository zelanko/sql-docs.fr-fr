---
title: L’instruction CALL (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4052134e9fd7d3c6877894c61480897e40982b59
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63187677"
---
# <a name="mdx-data-manipulation---call"></a>Manipulation de données MDX - CALL


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
 Le **appeler** instruction exécute une procédure stockée inscrite spécifiée, en incluant éventuellement un ou plusieurs arguments pour la procédure stockée spécifiée. Le **appeler** instruction doit être utilisé uniquement avec des procédures stockées qui retournent des valeurs vides. Cette instruction ne peut pas être combinée avec d'autres fonctions ou opérateurs au sein d'une expression MDX. Les procédures stockées enregistrées qui retournent des valeurs peuvent être appelées directement au sein d'expressions MDX et combinées avec d'autres fonctions et opérateurs MDX.  
  
 Si aucun cube n'est spécifié, l'instruction exécute la procédure stockée sur le cube actuel.  
  
> [!NOTE]  
>  Si la procédure stockée n’est pas inscrit sur le client, le **appeler** instruction tente d’appeler la procédure stockée à partir d’une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de Manipulation de données MDX &#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [Utilisation de procédures stockées &#40;MDX&#41;](../mdx/using-stored-procedures-mdx.md)  
  
  
