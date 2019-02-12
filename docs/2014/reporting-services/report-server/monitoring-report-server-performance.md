---
title: Analyse des performances d’un serveur de rapports | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- performance counters [Reporting Services]
- report servers [Reporting Services], performance
- counters [Reporting Services]
- monitoring performance [Reporting Services]
- SQL Server Reporting Services, performance
- performance [Reporting Services]
- Reporting Services, performance
ms.assetid: c1bc13d4-8297-4daf-bb19-4c1e5ba292a6
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 6e0bebad59894c150a77dd7b8fc3036fe50029e7
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56023650"
---
# <a name="monitoring-report-server-performance"></a>Analyse des performances d'un serveur de rapports
  Utilisez les outils d'analyse des performances sur un serveur de rapports pour évaluer l'activité du serveur, observer les tendances, diagnostiquer les goulots d'étranglement du système ou collecter des données permettant de déterminer si la configuration actuelle est suffisante. Pour optimiser les performances du serveur, vous pouvez spécifier la fréquence de recyclage du domaine d'application du serveur de rapports. Pour plus d’informations, consultez [Configurer la mémoire disponible pour les applications du serveur de rapports](../report-server/configure-available-memory-for-report-server-applications.md).  
  
## <a name="sources-of-performance-data"></a>Sources des données de performances  
 Utilisez une combinaison de technologies et d'outils pour obtenir des informations exhaustives sur les performances du système. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Les systèmes d’exploitation Windows Server fournissent des informations sur les performances au moyen des outils suivants :  
  
-   Gestionnaire des tâches  
  
-   Observateur d'événements  
  
-   Console de performance  
  
 Le Gestionnaire des tâches fournit des informations sur les programmes et les processus en cours d'exécution sur votre ordinateur. Il vous permet de surveiller les indicateurs clés des performances de votre serveur de rapports. Vous pouvez également évaluer l'activité des processus en cours d'exécution et afficher des graphiques et des données sur l'utilisation de l'UC et de la mémoire. Pour plus d'informations sur l'utilisation du Gestionnaire des tâches, consultez la documentation du produit [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 Vous pouvez utiliser la Console de performance et l'Observateur d'événements pour créer des journaux et des alertes à propos du traitement des rapports et de la consommation de ressources. Pour plus d’informations sur les événements Windows générés par [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consultez [Journal des applications Windows](windows-application-log.md). Pour plus d'informations sur la Console de performance, consultez la section « Compteurs de performances Windows » plus loin dans cette rubrique.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les utilitaires fournissent également des informations sur la base de données du serveur de rapports et sur les bases de données temporaires utilisées pour la gestion des sessions et de la mise en cache.  
  
## <a name="windows-performance-counters"></a>Compteurs de performances Windows  
 La surveillance de compteurs de performances spécifiques vous permet de :  
  
-   estimer la configuration requise nécessaire pour prendre en charge une charge de travail prédite ;  
  
-   créer une ligne de base des performances pour mesurer l'effet de modifications apportées à une configuration ou de mises à niveau d'applications ;  
  
-   observer les performances des applications sous certaines charges créées réellement ou artificiellement ;  
  
-   vérifier que les mises à niveau matérielles ont l'effet escompté sur les performances ;  
  
-   Valider que les modifications qui ont été apportées à la configuration du système ont l'effet souhaité sur les performances.  
  
## <a name="reporting-services-performance-objects"></a>Objets de performance de Reporting Services  
 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] comprend les objets de performance suivants :  
  
-   **Service Web MSRS 2011** et `MSRS 2011 SharePoint Mode Web Service` pour surveiller les performances du serveur de rapports. Ces objets de performance incluent une collection de compteurs utilisée pour suivre le traitement du serveur de rapports initialisé en général via des opérations de consultation du rapport interactives. Ces compteurs sont réinitialisés à chaque interruption du service Web Report Server par [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] .  
  
-   `MSRS 2011 Windows Service` et `MSRS 2011 Windows Service SharePoint Mode` pour surveiller les opérations planifiées et la remise de rapport. Ces objets de performance incluent une collection de compteurs utilisée pour suivre le traitement des rapports initialisé via des opérations planifiées. Les opérations planifiées englobent l'abonnement et la remise, les instantanés d'exécution de rapport et l'historique de rapport.  
  
-   `ReportServer:Service` et `ReportServerSharePoint:Service` pour surveiller des événements liés à HTTP et la gestion de la mémoire. Ces compteurs sont spécifiques à [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], et ils suivent les événements liés à HTTP pour le serveur de rapports, notamment les demandes, les connexions et les tentatives d’ouverture de session. Cet objet de performance inclut également des compteurs liés à la gestion de la mémoire.  
  
 Si vous possédez plusieurs instances de serveurs de rapports sur un seul ordinateur, vous pouvez les analyser collectivement ou individuellement. Choisissez les instances à inclure au moment où vous ajoutez un compteur. Pour plus d’informations sur l’utilisation de la Console de performances (perfmon.msc) et l’ajout de compteurs, consultez la documentation du produit [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
## <a name="other-performance-counters"></a>Autres compteurs de performance  
 Les compteurs de performances [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] personnalisés sont fournis uniquement pour `MSRS 2008 Web Service`, `MSRS 2008 Windows Service`, et `ReportServer:Service`. Les objets de performance suivants fournissent des données d'analyse des performances supplémentaires pour le serveur de rapports.  
  
|Objet de performance|Remarques|  
|------------------------|-----------|  
|`.NET CLR Data` et `.NET CLR Memory`|Le Gestionnaire de rapports utilise les compteurs de performances d' [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] . Pour plus d'informations, consultez la rubrique relative à l'amélioration des performances et de l'évolutivité des applications .NET, « Improving .NET Application Performance and Scalability » (en anglais) sur MSDN.|  
|`Process`|Ajoutez les compteurs de performances `Elapsed Time` et `ID Process` pour une instance ReportingServicesService de façon à suivre le temps de fonctionnement de processus par ID de processus.|  
  
## <a name="sharepoint-events"></a>Événements SharePoint  
 En plus des objets de performance [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vous pouvez également vouloir configurer des événements SharePoint si vous exécutez un serveur de rapports en mode intégré SharePoint et avez configuré votre environnement de création de rapports de façon à utiliser un produit SharePoint. Dans cette section, utilisez les événements d'un serveur de rapports en mode intégré SharePoint pour examiner les événements de diagnostic qui peuvent fournir des informations utiles si votre environnement de création de rapports est intégré SharePoint.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Compteurs de performance pour le Service Web MSRS 2014 et les objets de Performance Service MSRS 2014 Windows &#40;en Mode natif&#41;](performance-counters-msrs-2011-web-service-performance-objects.md)  
 Décrit les compteurs de performances utilisés par le service Web Report Server.  
  
 [Compteurs de performance pour les objets de Performance MSRS 2014 Windows Service SharePoint Mode MSRS 2014 Web Service SharePoint Mode &#40;Mode SharePoint&#41;](performance-counters-msrs-2011-sharepoint-mode-performance-objects.md)  
 Décrit les compteurs de performances utilisés par le service Windows Report Server.  
  
 [Compteurs de performances pour des objets de performances ReportServer:Service  et ReportServerSharePoint:Service](performance-counters-reportserver-service-performance-objects.md)  
 Décrit les compteurs de performance liés à HTTP et relatifs à la mémoire dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Événements pour un serveur de rapports en mode intégré SharePoint  
 Décrit les événements de diagnostic utiles pour enregistrer lorsque vous exécutez un environnement de création de rapports avec un produit SharePoint.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la mémoire disponible pour les applications du serveur de rapports](../report-server/configure-available-memory-for-report-server-applications.md)   
 [Serveur de rapports Reporting Services &#40;mode natif&#41;](reporting-services-report-server-native-mode.md)   
 [Outils de Reporting Services](../tools/reporting-services-tools.md)  
  
  
