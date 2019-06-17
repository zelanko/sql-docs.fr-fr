---
title: Erreur de gestion (MDX) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 611e7636f9a5cd6393da4a8412b6c02bcc9ddaf8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66074674"
---
# <a name="error-handling-mdx"></a>Gestion des erreurs (MDX)
  Chaque cube peut contrôler le mode de gestion des erreurs contenues dans un script MDX (Multidimensional Expressions). La gestion des erreurs s'effectue par l'intermédiaire de l'énumérateur `ScriptErrorHandlingMode`. Les valeurs possibles pour cet énumérateur sont les suivantes :  
  
 `IgnoreNone`  
 Entraîne la génération d’une erreur par le serveur si [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] détecte une erreur dans le script MDX.  
  
 `IgnoreAll`  
 Amène le serveur à ignorer toutes les commandes du script MDX qui contiennent une erreur, notamment les erreurs de syntaxe, de résolution de nom, etc.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
