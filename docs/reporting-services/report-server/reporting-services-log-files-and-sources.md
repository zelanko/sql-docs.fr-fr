---
title: Fichiers journaux et des Sources de Reporting Services | Documents Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting [Reporting Services], log files
- logs [Reporting Services]
- logs [Reporting Services], about log files
- report servers [Reporting Services], log files
- report server log files
- files [Reporting Services], logs
ms.assetid: 80ef0acc-cbef-49d0-87e7-844e3ce19604
caps.latest.revision: 49
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 08686f83b78c783e1d82c144e4a06f9ecd52bde0
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="reporting-services-log-files-and-sources"></a>Fichiers journaux et sources de Reporting Services
  Un serveur de rapports et son environnement utilisent un grand nombre de destinations de journaux pour consigner des informations sur les opérations et l'état du serveur. Il existe deux catégories de journalisation de base, la journalisation d'exécution et la journalisation de suivi. La journalisation d'exécution contient des informations sur les statistiques d'exécution des rapports, les audits, les diagnostics de performances et l'optimisation. La journalisation de suivi consigne les informations sur les messages d'erreur et les diagnostics généraux.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode  
  
 Le tableau suivant fournit des liens vers des informations complémentaires sur chaque journal, notamment son emplacement et la manière d'afficher son contenu.  
  
|Log|Description|  
|---------|-----------------|  
|[Journal des exécutions du serveur de rapports et vue ExecutionLog3](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md)|Le journal d'exécution est un affichage SQL Server enregistré dans la base de données du serveur de rapports.<br /><br /> Le journal d'exécution du serveur de rapports contient des données sur des rapports spécifiques, notamment la date d'exécution du rapport, l'utilisateur qui a procédé à l'exécution, l'endroit où il a été livré et le format de rendu utilisé.|  
|Journal des traces SharePoint|Pour les serveurs de rapports qui s'exécutent dans SharePoint, les journaux de suivi SharePoint contiennent les informations [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Vous pouvez également configurer des informations spécifiques [!INCLUDE[ssRS](../../includes/ssrs-md.md)] pour le service de journalisation unifiée SharePoint. Pour plus d’informations, consultez [Activer des événements Reporting Services pour le journal des traces SharePoint &#40;ULS&#41;](../../reporting-services/report-server/turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)|  
|[Journal de Trace de Service de serveur de rapports](../../reporting-services/report-server/report-server-service-trace-log.md)|Le journal des traces du service contient des informations très détaillées qui sont utiles si vous déboguez une application ou essayez de déterminer l'origine d'un problème ou d'un événement. Les fichiers journaux de suivi sont ReportServerService_\<timestamp > .log et sont situés dans le dossier suivant :<br /><br /> `C:\Program Files\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\LogFiles`|  
|[Journal HTTP Report Server](../../reporting-services/report-server/report-server-http-log.md)|Le fichier journal HTTP contient un enregistrement de toutes les requêtes et réponses HTTP gérées par le service Web Report Server et le Gestionnaire de rapports.|  
|[Journal des applications Windows](../../reporting-services/report-server/windows-application-log.md)|Le journal des applications Microsoft Windows contient des informations sur les événements de serveur de rapports.|  
|Journaux de performances Windows|Les journaux de performances Windows contiennent des données sur les performances du serveur de rapports. Vous pouvez créer des journaux de performances, puis choisir les compteurs qui définissent les données à collecter. Pour plus d'informations, consultez [Monitoring Report Server Performance](../../reporting-services/report-server/monitoring-report-server-performance.md).|  
|Fichiers journaux d’installation de SQL Server|Des fichiers journaux sont également créés pendant l'installation. Si l'installation échoue, ou bien si elle s'effectue avec des avertissements ou autres messages, vous pouvez consulter les fichiers journaux pour résoudre les problèmes. Pour plus d'informations, consultez [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).|  
|journaux IIS|Fichiers journaux créés par Microsoft Internet (IIS) Information Services. Pour plus d’informations, consultez [Comment activer la journalisation dans les services IIS](http://support.microsoft.com/kb/313437) (http://support.microsoft.com/kb/313437).|  
  
## <a name="see-also"></a>Voir aussi  
 [Serveur de rapports Reporting Services &#40;mode natif&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Guide de référence des erreurs et des événements &#40;Reporting Services&#41;](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
