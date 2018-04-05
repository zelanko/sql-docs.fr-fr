---
title: Instructions de définition de données MDX (MDX) | Documents Microsoft
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
dev_langs:
- kbMDX
helpviewer_keywords:
- MDX [Analysis Services], data manipulation
- data manipulation [MDX]
- data definition statements [MDX]
- Multidimensional Expressions [Analysis Services], data manipulation
ms.assetid: 1f975d7f-8875-43b6-a571-9d5cd7c70217
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 501f3a53b5c9ccaee8229ed99f0a37dc50b05e88
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-data-definition-statements-mdx"></a>Instructions MDX de définition de données (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Dans MDX (Multidimensional Expressions), les instructions de définition de données créent, suppriment et manipulent des objets multidimensionnels. Le tableau ci-dessous énumère les instructions de définition de données disponibles.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Instruction ALTER CUBE &#40; MDX &#41;](../mdx/mdx-data-definition-alter-cube.md)|Modifie la structure d'un cube spécifié.|  
|[CRÉER une instruction ACTION &#40; MDX &#41;](../mdx/mdx-data-definition-create-action.md)|Crée une action qui peut être associée à un cube, une dimension, une hiérarchie ou un objet subordonné.|  
|[CRÉER une instruction de calcul de cellule &#40; MDX &#41;](../mdx/mdx-data-definition-create-cell-calculation.md)|Crée un calcul qui évalue une expression MDX par rapport à un ensemble spécifié de tuples au sein d'un cube.|  
|[CREATE GLOBAL CUBE instruction &#40; MDX &#41;](../mdx/mdx-data-definition-create-global-cube.md)|Crée et remplit un cube persistant localement, en fonction d'un sous-cube issu d'un cube sur le serveur. Aucune connexion au serveur n'est nécessaire pour se connecter au cube conservé localement.|  
|[CRÉER une instruction MEMBER &#40; MDX &#41;](../mdx/mdx-data-definition-create-member.md)|Crée un membre calculé.|  
|[CRÉER une instruction de CUBE de SESSION &#40; MDX &#41;](../mdx/mdx-data-definition-create-session-cube.md)|Crée et remplit un cube disponible pour toutes les requêtes dans la même session, en fonction des cubes sur le serveur.|  
|[CRÉER une instruction SET &#40; MDX &#41;](../mdx/mdx-data-definition-create-set.md)|Crée un jeu nommé pour un cube spécifié.|  
|[CRÉER une instruction de sous-cube &#40; MDX &#41;](../mdx/mdx-data-definition-create-subcube.md)|Redéfinit l'espace du cube d'un cube ou d'un sous-cube spécifié en un sous-cube spécifié.|  
|[Supprimez l’instruction ACTION &#40; MDX &#41;](../mdx/mdx-data-definition-drop-action.md)|Supprime une action spécifiée d'un cube spécifié.|  
|[Supprimez l’instruction de calcul de cellule &#40; MDX &#41;](../mdx/mdx-data-definition-drop-cell-calculation.md)|Supprime le calcul de cellule spécifié.|  
|[Supprimez l’instruction MEMBER &#40; MDX &#41;](../mdx/mdx-data-definition-drop-member.md)|Supprime un membre calculé.|  
|[Supprimez l’instruction SET &#40; MDX &#41;](../mdx/mdx-data-definition-drop-set.md)|Supprime un jeu nommé.|  
|[Instruction de sous-cube DROP &#40; MDX &#41;](../mdx/mdx-data-definition-drop-subcube.md)|Supprime un sous-cube spécifié, et restaure la définition de cube ou de sous-cube antérieurement définie portant le nom spécifié.|  
|[Actualiser le CUBE instruction &#40; MDX &#41;](../mdx/mdx-data-definition-refresh-cube.md)|Actualise le cache client pour un cube.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des instructions MDX &#40; MDX &#41;](../mdx/mdx-statement-reference-mdx.md)   
 [Instructions MDX de Manipulation de données &#40; MDX &#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [Instructions de script MDX &#40; MDX &#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
