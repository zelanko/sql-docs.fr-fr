---
title: Notions de base (Analysis Services) des scripts MDX | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], scripts
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [MDX]
- cubes [Analysis Services], calculations
- Multidimensional Expressions [Analysis Services], scripts
ms.assetid: fdecb3ce-7c87-4bab-8000-532ba7a29f96
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 17cb2b326ed510a952249da6a73693b6be6ab252
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66073857"
---
# <a name="mdx-scripting-fundamentals-analysis-services"></a>Principes de base des scripts MDX (Analysis Services)
  Dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], un script MDX (Multidimensional Expressions) est constitué d’une ou plusieurs expressions ou instructions MDX qui remplissent un cube avec des calculs.  
  
 Un script MDX définit le processus de calcul pour un cube. Il est également considéré comme un élément du cube proprement dit. Par conséquent, la modification d'un script MDX associé à un cube entraîne immédiatement la modification de son processus de calcul.  
  
 Pour créer des scripts MDX, vous pouvez utiliser le Concepteur de cube disponible dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Pour plus d’informations, consultez [Définir des attributions et d’autres commandes de script](../define-assignments-and-other-script-commands.md) et [Introduction aux scripts MDX dans Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892).  
  
 Pour résoudre les problèmes de performance liés aux calculs et aux requêtes MDX, consultez la section relative à l’optimisation de MDX du [Guide des performances de SQL Server Analysis Services](https://go.microsoft.com/fwlink/p/?LinkId=399050).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Script MDX de base &#40;MDX&#41;](the-basic-mdx-script-mdx.md)|Décrit en détail le script MDX de base, notamment le script MDX par défaut fourni dans chaque cube, ainsi que le mode de fonctionnement général des scripts MDX au sein d’un cube dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Gestion de la portée et du contexte &#40;MDX&#41;](managing-scope-and-context-mdx.md)|Décrit l’utilisation de l’instruction [CALCULATE](/sql/mdx/mdx-scripting-calculate) , de l’instruction [SCOPE](/sql/mdx/mdx-scripting-scope) et de la fonction [This](/sql/mdx/this-mdx) pour gérer le contexte et la portée au sein d’un script MDX.|  
|[Utilisation de variables et de paramètres &#40;MDX&#41;](using-variables-and-parameters-mdx.md)|Décrit l'utilisation de variables et de paramètres dans un script MDX.|  
|[Gestion des erreurs &#40;MDX&#41;](error-handling-mdx.md)|Explique la gestion des erreurs au sein d'un script MDX.|  
|[Prise en charge de MDX &#40;MDX&#41;](supported-mdx-mdx.md)|Fournit la liste des opérateurs, instructions et fonctions MDX pris en charge dans un script MDX.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence du langage MDX &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx)  
  
  
