---
title: (MDX) de la gestion des erreurs | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8679c6d912e6dab8fa89f4f67ddfa9070c04460f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="error-handling-mdx"></a>Gestion des erreurs (MDX)
  Chaque cube peut contrôler le mode de gestion des erreurs contenues dans un script MDX (Multidimensional Expressions). La gestion des erreurs s’effectue par l’intermédiaire de l’énumérateur **ScriptErrorHandlingMode** . Les valeurs possibles pour cet énumérateur sont les suivantes :  
  
 **IgnoreNone**  
 Entraîne la génération d’une erreur par le serveur si [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] détecte une erreur dans le script MDX.  
  
 **IgnoreAll**  
 Amène le serveur à ignorer toutes les commandes du script MDX qui contiennent une erreur, notamment les erreurs de syntaxe, de résolution de nom, etc.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
