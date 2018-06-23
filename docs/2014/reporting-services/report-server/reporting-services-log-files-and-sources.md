---
title: Fichiers journaux et sources de Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting [Reporting Services], log files
- logs [Reporting Services]
- logs [Reporting Services], about log files
- report servers [Reporting Services], log files
- report server log files
- files [Reporting Services], logs
ms.assetid: 80ef0acc-cbef-49d0-87e7-844e3ce19604
caps.latest.revision: 48
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: da8c4e45c0472844b5351ad6ad02e39bba1d5e50
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042164"
---
# <a name="reporting-services-log-files-and-sources"></a>Fichiers journaux et sources de Reporting Services
  Un serveur de rapports [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] et son environnement prennent en charge un grand nombre de destinations de journaux pour consigner des informations sur les opérations et l'état du serveur. Il existe deux catégories de journalisation de base, la journalisation d'exécution et la journalisation de suivi. La journalisation d'exécution contient des informations sur les statistiques d'exécution des rapports, les audits, les diagnostics de performances et l'optimisation. La journalisation de suivi consigne les informations sur les messages d'erreur et les diagnostics généraux.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] en mode SharePoint | [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] en mode natif  
  
 Le tableau suivant fournit des liens vers des informations complémentaires sur chaque journal, notamment son emplacement et la manière d'afficher son contenu.  
  
|Log|Description|  
|---------|-----------------|  
|[Journal de l’exécution du serveur de rapports et vue ExecutionLog3](report-server-executionlog-and-the-executionlog3-view.md)|Le journal d'exécution est un affichage SQL Server enregistré dans la base de données du serveur de rapports.<br /><br /> Le journal d'exécution du serveur de rapports contient des données sur des rapports spécifiques, notamment la date d'exécution du rapport, l'utilisateur qui a procédé à l'exécution, l'endroit où il a été livré et le format de rendu utilisé.|  
|Journal des traces SharePoint|Pour les serveurs de rapports qui s'exécutent dans SharePoint, les journaux de suivi SharePoint contiennent les informations [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Vous pouvez également configurer [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] des informations spécifiques pour le service de journalisation unifiée SharePoint. Pour plus d’informations, consultez [Activer des événements Reporting Services pour le journal des traces SharePoint &#40;ULS&#41;](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md).|  
|[Journal de suivi de service du serveur de rapports](report-server-service-trace-log.md)|Le journal des traces du service contient des informations très détaillées qui sont utiles si vous déboguez une application ou essayez de déterminer l'origine d'un problème ou d'un événement.<br /><br /> `C:\Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\LogFiles`|  
|[Journal HTTP du serveur de rapports](report-server-http-log.md)|Le fichier journal HTTP contient un enregistrement de toutes les requêtes et réponses HTTP gérées par le service Web Report Server et le Gestionnaire de rapports.|  
|[Journal des applications Windows](windows-application-log.md)|Le journal des applications Microsoft Windows contient des informations sur les événements de serveur de rapports.|  
|Journaux de performances Windows|Les journaux de performances Windows contiennent des données sur les performances du serveur de rapports. Vous pouvez créer des journaux de performances, puis choisir les compteurs qui définissent les données à collecter. Pour plus d'informations, consultez [Monitoring Report Server Performance](monitoring-report-server-performance.md).|  
|Fichiers journaux du programme d'installation|Des fichiers journaux sont également créés pendant l'installation. Si l'installation échoue, ou bien si elle s'effectue avec des avertissements ou autres messages, vous pouvez consulter les fichiers journaux pour résoudre les problèmes. Pour plus d'informations, consultez [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).|  
|journaux IIS|Fichiers journaux créés par Microsoft Internet (IIS) Information Services. Pour plus d'informations, consultez [Comment activer la journalisation dans les services IIS](http://support.microsoft.com/kb/313437).|  
|Vidéo|Visualiser une courte vidéo qui montre l'utilisation de Microsoft Power Query pour afficher des fichiers journaux [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] .<br /><br /> ![Regarder une vidéo sur les journaux SSRS et Power Query](../media/generic-video-thumbnail.png "regarder une vidéo sur les journaux SSRS et Power Query")|  
  
## <a name="see-also"></a>Voir aussi  
 [Serveur de rapports Reporting Services &#40;mode natif&#41;](reporting-services-report-server-native-mode.md)   
 [Erreurs et événements référence &#40;Reporting Services&#41;](../troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  