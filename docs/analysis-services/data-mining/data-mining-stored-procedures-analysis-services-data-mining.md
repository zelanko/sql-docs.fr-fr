---
title: Procédures stockées d’exploration de données (Analysis Services - Exploration de données) | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services], data mining
ms.assetid: a751856d-33bd-4788-9593-317b2826132d
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bf4b9b0fb2fe19d084c47d78d215f0001309af20
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="data-mining-stored-procedures-analysis-services---data-mining"></a>Procédures stockées d'exploration de données (Analysis Services - Exploration de données)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]À compter de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les procédures stockées qui peuvent être écrits dans n’importe quel langage managé. Les langages managés pris en charge incluent .NET [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , C# et C++ managé. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous pouvez appeler directement les procédures stockées à l’aide de l’instruction **CALL** ou dans le cadre d’une requête DMX (Data Mining Extensions).  
  
 Pour plus d’informations sur l’appel de procédures stockées [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , consultez [Appel des procédures stockées](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/calling-stored-procedures.md).  
  
 Pour obtenir des informations générales sur les fonctionnalités de programmation, consultez [programmation d’exploration de données](../../analysis-services/data-mining-programming.md).  
  
 Pour plus d’informations sur la programmation d’objets d’exploration de données, consultez l’article «[SQL Server Data Mining Programmability](http://go.microsoft.com/fwlink/?LinkId=93735)» (Programmation de l’exploration de données SQL Server) dans la bibliothèque MSDN.  
  
> [!NOTE]  
>  Lorsque vous interrogez des modèles d'exploration de données, surtout lorsque vous testez de nouvelles solutions d'exploration de données, vous voudrez peut-être appeler les procédures stockées système qui sont utilisées en interne par le moteur d'exploration de données. Vous pouvez afficher le nom de ces procédures stockées système en utilisant [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour créer une trace sur le serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , puis en créant, parcourant et interrogeant les modèles d’exploration de données. Toutefois, [!INCLUDE[msCoName](../../includes/msconame-md.md)] ne garantit pas la compatibilité des procédures stockées système entre les versions, et vous ne devez jamais utiliser des appels de procédures stockées système dans un système de production. Pour des raisons de compatibilité, vous devez à la place créer vos propres requêtes à l'aide des langages DMX ou XML/A.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [SystemGetCrossValidationResults &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterCrossValidationResults &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetAccuracyResults &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterAccuracyResults &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Validation croisée &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)   
 [Onglet Validation croisée &#40; Vue graphique d’analyse de précision d’exploration de données &#41;](http://msdn.microsoft.com/library/bd215a68-1ad7-4046-9c44-ec8e2be13a64)   
 [Appel d’une procédure stockée](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md)  
  
  
