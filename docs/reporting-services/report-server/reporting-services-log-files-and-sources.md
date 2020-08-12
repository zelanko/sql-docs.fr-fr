---
title: Fichiers journaux et sources de Reporting Services | Microsoft Docs
description: Apprenez-en davantage sur les journaux utilisés par les serveurs de rapports et les environnements de serveur de rapports dans Reporting Services pour enregistrer les informations d’exécution et de trace.
ms.date: 05/10/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting [Reporting Services], log files
- logs [Reporting Services]
- logs [Reporting Services], about log files
- report servers [Reporting Services], log files
- report server log files
- files [Reporting Services], logs
ms.assetid: 80ef0acc-cbef-49d0-87e7-844e3ce19604
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1e9fad0dad3b5a5d90339403d2d596bb95bf0759
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84541441"
---
# <a name="reporting-services-log-files-and-sources"></a>Fichiers journaux et sources de Reporting Services
  Un serveur de rapports et son environnement utilisent un grand nombre de destinations de journaux pour consigner des informations sur les opérations et l'état du serveur. Il existe deux catégories de journalisation de base, la journalisation d'exécution et la journalisation de suivi. La journalisation d'exécution contient des informations sur les statistiques d'exécution des rapports, les audits, les diagnostics de performances et l'optimisation. La journalisation de suivi consigne les informations sur les messages d'erreur et les diagnostics généraux.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif  
  
 Le tableau suivant fournit des liens vers des informations complémentaires sur chaque journal, notamment son emplacement et la manière d'afficher son contenu.  
  
|Journal|Description|  
|---------|-----------------|  
|[Journal d’exécution du serveur de rapports et vue ExecutionLog3](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md)|Le journal d'exécution est un affichage SQL Server enregistré dans la base de données du serveur de rapports.<br /><br /> Le journal d'exécution du serveur de rapports contient des données sur des rapports spécifiques, notamment la date d'exécution du rapport, l'utilisateur qui a procédé à l'exécution, l'endroit où il a été livré et le format de rendu utilisé.|  
|Journal des traces SharePoint|Pour les serveurs de rapports qui s'exécutent dans SharePoint, les journaux de suivi SharePoint contiennent les informations [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Vous pouvez également configurer des informations spécifiques [!INCLUDE[ssRS](../../includes/ssrs.md)] pour le service de journalisation unifiée SharePoint. Pour plus d’informations, consultez [Activer des événements Reporting Services pour le journal des traces SharePoint &#40;ULS&#41;](../../reporting-services/report-server/turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)|  
|[Journal de suivi de service du serveur de rapports](../../reporting-services/report-server/report-server-service-trace-log.md)|Le journal des traces du service contient des informations très détaillées qui sont utiles si vous déboguez une application ou essayez de déterminer l'origine d'un problème ou d'un événement. Les fichiers journaux de suivi sont ReportServerService_\<timestamp>.log et se trouvent dans le dossier suivant :<br /><br /> Dans SQL Server Reporting Services 2016 ou antérieur : `C:\Program Files\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\LogFiles`<br /><br /> Dans SQL Server Reporting Services 2017 : `C:\Program Files\Microsoft SQL Server Reporting Services\SSRS\LogFiles`|  
|[Journal HTTP du serveur de rapports](../../reporting-services/report-server/report-server-http-log.md)|Le fichier journal HTTP contient un enregistrement de toutes les demandes et réponses HTTP gérées par le service web Report Server.|  
|[Journal des applications Windows](../../reporting-services/report-server/windows-application-log.md)|Le journal des applications Microsoft Windows contient des informations sur les événements de serveur de rapports.|  
|Journaux de performances Windows|Les journaux de performances Windows contiennent des données sur les performances du serveur de rapports. Vous pouvez créer des journaux de performances, puis choisir les compteurs qui définissent les données à collecter. Pour plus d’informations, consultez [Analyse des performances d’un serveur de rapports](../../reporting-services/report-server/monitoring-report-server-performance.md).|  
|Fichiers journaux d’installation de SQL Server|Des fichiers journaux sont également créés pendant l'installation. Si l'installation échoue, ou bien si elle s'effectue avec des avertissements ou autres messages, vous pouvez consulter les fichiers journaux pour résoudre les problèmes. Pour plus d'informations, consultez [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).|  
|Journaux d’activité IIS|Fichiers journaux créés par Microsoft Internet (IIS) Information Services. Pour plus d'informations, consultez [Comment activer la journalisation dans les services (IIS)](https://support.microsoft.com/kb/313437) (https://support.microsoft.com/kb/313437).|  
  
## <a name="see-also"></a>Voir aussi  
 [Serveur de rapports Reporting Services &#40;mode natif&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Guide de référence des erreurs et des événements &#40;Reporting Services&#41;](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
