---
title: Erreur de gestion (MDX) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5d6679e264ee15fd6a1ba038d3c6492aec07c81c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62802713"
---
# <a name="error-handling-mdx"></a>Gestion des erreurs (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Chaque cube peut contrôler le mode de gestion des erreurs contenues dans un script MDX (Multidimensional Expressions). La gestion des erreurs s’effectue par l’intermédiaire de l’énumérateur **ScriptErrorHandlingMode** . Les valeurs possibles pour cet énumérateur sont les suivantes :  
  
 **IgnoreNone**  
 Entraîne la génération d’une erreur par le serveur si [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] détecte une erreur dans le script MDX.  
  
 **IgnoreAll**  
 Amène le serveur à ignorer toutes les commandes du script MDX qui contiennent une erreur, notamment les erreurs de syntaxe, de résolution de nom, etc.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
