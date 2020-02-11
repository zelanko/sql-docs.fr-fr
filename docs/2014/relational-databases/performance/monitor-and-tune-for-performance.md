---
title: Surveillance et réglage des performances | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- instances of SQL Server, monitoring performance
- monitoring server performance [SQL Server]
- Database Engine [SQL Server], performance
- monitoring performance [SQL Server], about performance
- server performance [SQL Server]
- monitoring performance [SQL Server]
- database performance [SQL Server], about performance
- tuning databases [SQL Server], about performance
- status information [SQL Server], performance monitoring
- database monitoring [SQL Server], about performance
- monitoring [SQL Server], queries performance
- server performance [SQL Server], about performance
- tuning databases [SQL Server]
- database performance [SQL Server]
- monitoring [SQL Server], server performance
- database monitoring [SQL Server]
- monitoring server performance [SQL Server], about monitoring server performance
ms.assetid: 87f23f03-0f19-4b2e-bfae-efa378f7a0d4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 683e8044b235828741fe429f133af82d1977031a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63150714"
---
# <a name="monitor-and-tune-for-performance"></a>Surveiller et régler les performances
  Le but de la surveillance des bases de données est d'évaluer le fonctionnement d'un serveur. Une surveillance efficace implique la prise d'instantanés périodiques des performances actuelles afin d'isoler les processus à l’origine des problèmes, ainsi que la collecte de données en continu pour suivre de près les tendances des performances.  
  
 L'évaluation continue des performances de la base de données vous permet de réduire les temps de réponse et accélère le débit, ce qui optimise les performances. Un trafic réseau efficace, des E/S disque et l'utilisation de l'UC sont essentiels pour maximiser les performances. Vous devez analyser soigneusement les besoins de l'application, comprendre la structure logique et physique des données, évaluer l'utilisation de la base de données et négocier les compromis entre des utilisations conflictuelles telles que le traitement transactionnel en ligne par rapport à l'aide à la décision.  
  
## <a name="benefits-of-monitoring-and-tuning-databases-for-performance"></a>Avantages de la surveillance des bases de données et du paramétrage des performances  
 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le système d'exploitation Microsoft Windows fournissent des utilitaires qui vous permettent de contrôler les conditions actuelles de la base de données et de suivre l'évolution des performances en fonction de l'évolution de ces conditions. Il existe un large éventail d’outils et de techniques qui peuvent être utilisés [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]pour surveiller. Comprendre comment surveiller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut vous aider à :  
  
-   Déterminer si vous pouvez améliorer les performances. Par exemple, en surveillant les temps de réponse des requêtes les plus fréquentes, vous pouvez déterminer s'il faut modifier les requêtes ou les index des tables.  
  
-   Évaluer l'activité des utilisateurs. Par exemple, en surveillant les utilisateurs qui tentent de se connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez déterminer si la sécurité est correctement configurée et tester les applications et les systèmes de développement. Par exemple, en surveillant les requêtes SQL au fur et à mesure de leur exécution, vous pouvez déterminer si elles sont correctement rédigées et si elles produisent les résultats attendus.  
  
-   Résoudre les éventuels problèmes ou déboguer des composants d'application, comme des procédures stockées.  
  
### <a name="monitoring-in-a-dynamic-environment"></a>Surveillance dans un environnement dynamique  
 La surveillance est importante car [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit un service dans un environnement dynamique. La modification des conditions aboutit à un changement des performances. Dans vos évaluations, vous pouvez voir les changements de performances au fur et à mesure que le nombre d'utilisateurs augmente, que les accès des utilisateurs et les méthodes de connexion changent, que la base de données se remplit, que les applications clientes changent, que les données des applications changent, que les requêtes deviennent plus complexes et que le trafic réseau augmente. Grâce aux outils de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permettant de surveiller les performances, vous pouvez associer certaines modifications des performances à des modifications de conditions et des requêtes complexes. Les scénarios suivants fournissent des exemples :  
  
-   en surveillant les temps de réponse des requêtes les plus fréquentes, vous pouvez déterminer s'il faut modifier, soit les requêtes, soit les index des tables ;  
  
-   en surveillant les requêtes [!INCLUDE[tsql](../../includes/tsql-md.md)] au fur et à mesure de leur exécution, vous pouvez déterminer si elles sont correctement rédigées et si elles produisent les résultats attendus ;  
  
-   en surveillant les utilisateurs qui tentent de se connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez déterminer si la sécurité est correctement configurée et tester les applications et les systèmes de développement.  
  
 Le temps de réponse est la durée requise pour le renvoi de la première ligne de l'ensemble de résultats à l’utilisateur sous forme de confirmation visuelle qu’une requête est en cours de traitement. Le débit mesure le nombre total de requêtes gérées par le serveur pendant une période donnée.  
  
 La demande des ressources du serveur croît proportionnellement au nombre d'utilisateurs, augmentant ainsi le temps de réponse et, par conséquent, diminuant le débit global.  
  
## <a name="monitoring-and-tuning-performance-tasks"></a>Tâches de surveillance et de paramétrage des performances  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|[Surveiller les composants SQL Server](monitor-sql-server-components.md)|Fournit les étapes nécessaires requises pour surveiller efficacement n'importe quel composant de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Outils d'analyse et de paramétrage des performances](performance-monitoring-and-tuning-tools.md)|Répertorie les outils de surveillance et de paramétrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Établir un niveau de référence des performances](establish-a-performance-baseline.md)|Fournit des informations sur l'établissement d'une a génération d'une ligne de base des performances.|  
|[Isoler les problèmes de performance](isolate-performance-problems.md)|Explique comment isoler les problèmes de performances de base de données.|  
|[Identifier les goulots d'étranglement](identify-bottlenecks.md)|Explique comment surveiller et suivre les performances du serveur afin d'identifier les goulots d'étranglement.|  
|[Analyse des performances et surveillance de l'activité du serveur](server-performance-and-activity-monitoring.md)|Explique comment utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les outils de surveillance de l'activité et des performances Windows.|  
|[Afficher et enregistrer des plans d'exécution](display-and-save-execution-plans.md)|Explique comment afficher et enregistrer des plans d'exécution dans un fichier au format XML.|  
|[Analyse des performances à l'aide du magasin de requêtes](monitoring-performance-by-using-the-query-store.md)|Le magasin de requête capture automatiquement l'historique des requêtes, des plans et des statistiques d'exécution et les conserve à des fins de consultation.|  
  
## <a name="see-also"></a>Voir aussi  
 [Administration automatisée à l’échelle d’une entreprise](../../ssms/agent/automated-administration-across-an-enterprise.md)   
 [Assistant Paramétrage du moteur de base de données](database-engine-tuning-advisor.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
