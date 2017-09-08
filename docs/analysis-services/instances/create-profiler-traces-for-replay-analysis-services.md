---
title: "Créer des Traces du Générateur de profils pour la relecture (Analysis Services) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- replaying queries
- replaying discovers
- events [Analysis Services]
- replaying commands
- Profiler [SQL Server Profiler], Analysis Services
- performance [Analysis Services], replays
- traces [Analysis Services]
ms.assetid: 93b2fc46-7cfb-4ab5-abeb-1475a7d6f0f2
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c992aa2f5d666b38290b928bf44e6e5680ba701e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-profiler-traces-for-replay-analysis-services"></a>Créer des traces de SQL Server Profiler pour la relecture (Analysis Services)
  Pour relire les requêtes, les découvertes et les commandes soumises par des utilisateurs à [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] doit collecter les événements requis. Pour lancer la collecte de ces événements, les classes d’événements appropriées doivent être sélectionnées sous l’onglet **Sélection des événements** de la boîte de dialogue **Propriétés de la trace** . Par exemple, si la classe d'événements Query Begin est sélectionnée, les événements qui contiennent des requêtes sont collectés et utilisés pour la relecture. De même, le fichier de trace contient suffisamment d'informations pour autoriser la relecture des transactions serveur dans un environnement distribué dans leur ordre d'origine.  
  
## <a name="replay-for-queries"></a>Relecture des requêtes  
 Pour relire les requêtes, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] doit capturer les événements suivants :  
  
-   Classe d’événements Audit Login avec toutes ses colonnes de données. Cette classe d'événements fournit des informations sur les utilisateurs qui se sont connectés et sur les paramètres de leurs sessions. Le SPID (Server Process ID) fournit la référence à la session utilisateur. Pour plus d’informations, consultez [Colonnes de données Audit de sécurité](../../analysis-services/trace-events/security-audit-data-columns.md).  
  
-   Classe d’événements Query Begin avec toutes ses colonnes de données. Cette classe d’événements fournit des informations sur la requête qui a été soumise à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. La colonne Event Subclass fournit des informations sur le type de requête. La colonne TextData fournit le texte réel de la requête. La colonne RequestParameters fournit les paramètres des requêtes paramétrables, et la colonne RequestProperties fournit les propriétés des demandes XMLA (XML for Analysis). Pour plus d’informations, consultez [Colonnes de données des événements de requêtes](../../analysis-services/trace-events/queries-events-data-columns.md).  
  
-   Classe d’événements Query End avec toutes ses colonnes de données. Cette classe d'événements vérifie l'état de l'exécution de la requête. Pour plus d’informations, consultez [Colonnes de données des événements de requêtes](../../analysis-services/trace-events/queries-events-data-columns.md).  
  
## <a name="replay-for-discovers"></a>Relecture des découvertes  
 Pour relire les découvertes, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] doit capturer les événements suivants :  
  
-   Classe d’événements Audit Login avec toutes ses colonnes de données. Cette classe d'événements fournit des informations sur les utilisateurs qui se sont connectés et sur les paramètres de leurs sessions. Le SPID fournit la référence à la session utilisateur. Pour plus d’informations, consultez [Colonnes de données Audit de sécurité](../../analysis-services/trace-events/security-audit-data-columns.md).  
  
-   Classe d’événements Discover Begin avec toutes ses colonnes de données. La colonne TextData fournit le \<RequestType > partie de la demande de découverte et de la colonne RequestProperties fournit le \<Propriétés > partie de la demande de découverte. La colonne EventSubclass fournit le type de découverte. Pour plus d’informations, consultez [Colonnes de données des événements de découverte](../../analysis-services/trace-events/discover-events-data-columns.md).  
  
-   Classe d'événements Discover End avec toutes ses colonnes de données. Cette classe d'événements vérifie l'état de la demande de découverte. Pour plus d’informations, consultez [Colonnes de données des événements de découverte](../../analysis-services/trace-events/discover-events-data-columns.md).  
  
## <a name="replay-for-commands"></a>Relecture des commandes  
 Pour relire les commandes, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] doit capturer les événements suivants :  
  
-   Classe d’événements Command Begin avec toutes ses colonnes de données. La colonne TextData fournit les détails des commandes, par exemple le type du processus, l’ID de base de données et l’ID de cube. La colonne RequestParameters fournit les paramètres des commandes paramétrables, et la colonne RequestProperties fournit les propriétés des demandes XMLA. Pour plus d’informations, consultez [Colonnes de données des événements de commande](../../analysis-services/trace-events/command-events-data-columns.md).  
  
-   Classe d'événements Command End avec toutes ses colonnes de données. Cette classe d'événements vérifie l'état de la commande. Pour plus d’informations, consultez [Colonnes de données des événements de commande](../../analysis-services/trace-events/command-events-data-columns.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Événements de trace Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)   
 [Introduction à la surveillance de Analysis Services à l'aide de SQL Server Profiler](../../analysis-services/instances/introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)  
  
  
