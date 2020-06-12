---
title: Gestion des erreurs (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 357194b9f789fdeacfb65ce3c894d4747867eafb
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546565"
---
# <a name="error-handling-mdx"></a>Gestion des erreurs (MDX)
  Chaque cube peut contrôler le mode de gestion des erreurs contenues dans un script MDX (Multidimensional Expressions). La gestion des erreurs s'effectue par l'intermédiaire de l'énumérateur `ScriptErrorHandlingMode`. Les valeurs possibles pour cet énumérateur sont les suivantes :  
  
 `IgnoreNone`  
 Entraîne le déclenchement d’une erreur par le serveur lorsque [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] détecte une erreur dans le script MDX.  
  
 `IgnoreAll`  
 Amène le serveur à ignorer toutes les commandes du script MDX qui contiennent une erreur, notamment les erreurs de syntaxe, de résolution de nom, etc.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
