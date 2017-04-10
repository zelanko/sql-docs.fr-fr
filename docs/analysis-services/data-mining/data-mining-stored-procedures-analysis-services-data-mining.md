---
title: "Proc&#233;dures stock&#233;es d&#39;exploration de donn&#233;es (Analysis Services - Exploration de donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "procédures stockées [Analysis Services], exploration de données"
ms.assetid: a751856d-33bd-4788-9593-317b2826132d
caps.latest.revision: 26
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 26
---
# Proc&#233;dures stock&#233;es d&#39;exploration de donn&#233;es (Analysis Services - Exploration de donn&#233;es)
  Depuis [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge des procédures stockées qui peuvent être écrites dans tout langage managé. Les langages managés pris en charge incluent .NET [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], C# et C++ managé. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous pouvez appeler directement les procédures stockées à l’aide de l’instruction **CALL** ou dans le cadre d’une requête DMX (Data Mining Extensions).  
  
 Pour plus d’informations sur l’appel de procédures stockées [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], consultez [Appel des procédures stockées](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/calling-stored-procedures.md).  
  
 Pour des informations générales sur les fonctionnalités de programmation de [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)], consultez [Programmation de l’exploration de données](../../analysis-services/data-mining-programming.md).  
  
 Pour plus d’informations sur la programmation d’objets d’exploration de données, consultez l’article « [SQL Server Data Mining Programmability](http://go.microsoft.com/fwlink/?LinkId=93735) » (Programmation de l’exploration de données SQL Server) dans la bibliothèque MSDN.  
  
> [!NOTE]  
>  Lorsque vous interrogez des modèles d'exploration de données, surtout lorsque vous testez de nouvelles solutions d'exploration de données, vous voudrez peut-être appeler les procédures stockées système qui sont utilisées en interne par le moteur d'exploration de données. Vous pouvez afficher le nom de ces procédures stockées système en utilisant [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour créer une trace sur le serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], puis en créant, parcourant et interrogeant les modèles d’exploration de données. Toutefois, [!INCLUDE[msCoName](../../includes/msconame-md.md)] ne garantit pas la compatibilité des procédures stockées système entre les versions, et vous ne devez jamais utiliser des appels de procédures stockées système dans un système de production. Pour des raisons de compatibilité, vous devez à la place créer vos propres requêtes à l'aide des langages DMX ou XML/A.  
  
## Dans cette section  
  
-   [SystemGetCrossValidationResults &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterCrossValidationResults &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetAccuracyResults &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterAccuracyResults &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
## Référence  
 [Tâches d'administration à l'aide de scripts dans Analysis Services](../../analysis-services/instances/script-administrative-tasks-in-analysis-services.md)  
  
## Voir aussi  
 [Validation croisée &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)   
 [Onglet Validation croisée &#40;Vue Graphique d’analyse de précision de l’exploration de données&#41;](../Topic/Cross-Validation%20Tab%20\(Mining%20Accuracy%20Chart%20View\).md)   
 [Appel d'une procédure stockée](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md)  
  
  