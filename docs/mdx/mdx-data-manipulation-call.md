---
title: CALL, instruction (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: de74590ac4c43a9141c0ab2092babf41ffd23ba5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68106302"
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
 L’instruction **Call** exécute une procédure stockée inscrite spécifiée, en incluant éventuellement un ou plusieurs arguments pour la procédure stockée spécifiée. L’instruction **Call** est destinée à être utilisée uniquement avec des procédures stockées qui retournent des insertions. Cette instruction ne peut pas être combinée avec d'autres fonctions ou opérateurs au sein d'une expression MDX. Les procédures stockées enregistrées qui retournent des valeurs peuvent être appelées directement au sein d'expressions MDX et combinées avec d'autres fonctions et opérateurs MDX.  
  
 Si aucun cube n'est spécifié, l'instruction exécute la procédure stockée sur le cube actuel.  
  
> [!NOTE]  
>  Si la procédure stockée n’est pas inscrite sur le client, l’instruction **Call** tente d’appeler la procédure stockée [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]à partir d’une instance de.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de manipulation de données MDX &#40;&#41;MDX](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [Utilisation de procédures stockées &#40;&#41;MDX](../mdx/using-stored-procedures-mdx.md)  
  
  
