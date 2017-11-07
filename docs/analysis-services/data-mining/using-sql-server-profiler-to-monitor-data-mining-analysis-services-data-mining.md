---
title: "À l’aide de SQL Server Profiler pour contrôler l’exploration de données | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 655ac93c-5c5c-4565-914b-915327f7d349
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 96b5485ebddba8823f262ba6a2229018d82a72fd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="using-sql-server-profiler-to-monitor-data-mining-analysis-services---data-mining"></a>Utilisation de SQL Server Profiler pour contrôler l'exploration de données (Analysis Services – Exploration de données)
  Si vous avez les autorisations nécessaires, vous pouvez utiliser SQL Server Profiler pour contrôler les activités d'exploration de données émises sous la forme de demandes envoyées à une instance de SQL Server Analysis Services. L'activité d'exploration de données peut inclure le traitement de modèles ou de structures, de requêtes de prédiction ou de requêtes de contenu ou la création de nouveaux modèles ou structures.  
  
 SQL Server Profiler utilise une **trace** pour contrôler les requêtes envoyées par plusieurs clients, notamment [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], SQL Server Management Studio, les services web ou les compléments d’exploration de données pour Excel, à condition que l’ensemble des activités utilisent la même instance de SQL Server Analysis Services. Vous devez créer un suivi séparé pour chaque instance de SQL Server Analysis Services que vous souhaitez contrôler. Pour obtenir des informations générales sur les traces et l’utilisation de SQL Server Profiler, consultez [Utiliser SQL Server Profiler pour contrôler Analysis Services](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md).  
  
 Pour obtenir des conseils spécifiques sur les types d’événements à capturer, consultez [Créer des traces de SQL Server Profiler pour la relecture &#40;Analysis Services&#41;](../../analysis-services/instances/create-profiler-traces-for-replay-analysis-services.md).  
  
## <a name="using-traces-to-monitor-data-mining"></a>Utilisation des suivis pour contrôler l'exploration de données  
 Lorsque vous capturez des informations dans un suivi, vous pouvez spécifier si les informations sont enregistrées dans un fichier ou dans une table sur une instance de SQL Server. Indépendamment de la méthode utilisée pour stocker les données, vous pouvez utiliser SQL Server Profiler pour consulter le suivi et filtrer par événements. Le tableau suivant répertorie certains événements et sous-classes de la trace [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] par défaut qui sont pertinents pour l'exploration de données.  
  
|EventClass|EventSubclass|Description|  
|----------------|-------------------|-----------------|  
|**Query Begin**<br /><br /> **Query End**|**0 - MDXQuery**|Contient le texte de tous les appels aux procédures stockées [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|**Query Begin**<br /><br /> **Query End**|**1 - DMXQuery**|Contient le texte et les résultats des instructions DMX (Data Mining Extensions).|  
|**Progress Report Begin**<br /><br /> **Progress Report End**|**34 - DataMiningProgress**|Fournit des informations sur la progression de l'algorithme d'exploration de données : par exemple, si vous générez un modèle de clustering, le message de progression indique quel cluster de candidat est construit|  
|**Query Begin**<br /><br /> **Query End**|EXECUTESQL|Contient le texte de la requête Transact-SQL en cours d'exécution.|  
|**Query Begin**<br /><br /> **Query End**|**2 - SQLQuery**|Contient le texte des requêtes sur les ensembles de lignes de schéma dans le formulaire de tables système.|  
|**DISCOVER Begin**<br /><br /> **DISCOVER End**|Multiple|Contient le texte des appels de fonction DMX ou des instructions DISCOVER, encapsulés dans XMLA.|  
|**Erreur**|(aucun)|Contient le texte des erreurs envoyées par le serveur au client.<br /><br /> Des messages d’erreur précédés de **Erreur (Exploration de données) :** ou **Informationnel (Exploration de données) :** sont générés spécifiquement en réponse aux requêtes DMX. Toutefois, il n'est pas suffisant de consulter uniquement ces messages d'erreur. D'autres erreurs, telles que celles générées par l'analyseur, sont parfois liées à l'exploration de données mais elles n'ont pas ce préfixe.|  
  
 En consultant les instructions de commande dans le journal des traces, vous pouvez également voir la syntaxe des instructions complexes envoyées par le client au serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , notamment les appels aux procédures stockées système. Ces informations peuvent être utiles pour le débogage, ou vous pouvez utiliser des instructions valides comme modèle pour créer de nouvelles requêtes ou de nouveaux modèles de prédiction. Pour obtenir des exemples d’appels de procédure stockée que vous pouvez capturer par l’intermédiaire d’une trace, consultez [Exemples de requêtes de modèle de clustering](../../analysis-services/data-mining/clustering-model-query-examples.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser une instance Analysis Services](../../analysis-services/instances/monitor-an-analysis-services-instance.md)   
 [Surveiller Analysis Services avec des événements étendus SQL Server](../../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)  
  
  

