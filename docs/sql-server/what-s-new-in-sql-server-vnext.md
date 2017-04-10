---
title: "Nouveaut&#233;s de SQL Server vNext | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b57f375-9242-4bb2-9d4b-c560d5a93524
caps.latest.revision: 71
author: "craigg-msft"
ms.author: "craigg"
manager: "jhubbard"
caps.handback.revision: 65
---
# Nouveaut&#233;s de SQL Server vNext
SQL Server vNext représente une étape importante qui vise à faire de SQL Server une plateforme vous offrant des choix en matière de langages de développement, de types de données, d’utilisation locale ou dans le cloud, et de systèmes d’exploitation, en apportant la puissance de SQL Server à Linux, aux conteneurs Docker basés sur Linux et à Windows.

Cette rubrique présente un résumé des nouveautés de la dernière version préliminaire CTP (Community Technical Preview), ainsi que des liens vers des informations détaillées sur les nouveautés pour des domaines de fonctionnalités spécifiques.

![info_tip](../sql-server/media/info-tip.png) Exécutez SQL Server sur Linux ! Pour plus d'informations, consultez :
-  [Nouveautés de SQL Server vNext sur Linux](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-whats-new)
-  [Documentation de SQL Server sur Linux](https://docs.microsoft.com/en-us/sql/linux/)


**Essayez-le :**    
   -   [![Télécharger à partir du Centre d’évaluation](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477) **[Télécharger SQL Server vNext Community Technology Preview](http://go.microsoft.com/fwlink/?LinkID=829477)**


## <a name="whats-new-in-sql-server-vnext-ctp-13-february-2017"></a>Nouveautés de SQL Server vNext CTP 1.3 (février 2017)
### <a name="sql-server-database-engine"></a>Moteur de base de données SQL Server
- Améliorations des performances des points de contrôle indirects.
- Ajout de la prise en charge des groupes de disponibilité sans cluster.
- Ajout du paramètre des groupes de disponibilité à validation de réplica minimale.
- Les groupes de disponibilité peuvent désormais fonctionner sur Windows-Linux pour activer les migrations entre systèmes d’exploitation et les tests.
- Ajout de la prise en charge de la stratégie de rétention des tables temporelles
- Nouvel élément DMV SYS.DM_DB_STATS_HISTOGRAM.
- Ajout de la prise en charge de la génération et de la régénération d’index columnstore non cluster en ligne.
- Ajout de&5; nouvelles vues de gestion dynamique pour retourner des informations sur le processus Linux. Pour plus d’informations, consultez l’article [Vues de gestion dynamique de processus Linux (Transact-SQL)](../relational-databases/system-dynamic-management-views/linux-process-dynamic-management-views-transact-sql.md).   
- Le paramètre [Sys.dm_db_stats_histogram (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) est ajouté pour l’examen des statistiques.

### <a name="sql-server-analysis-services-ssas-ctp-13"></a>SQL Server Analysis Services (SSAS) (CTP 1.3)
- La fonctionnalité avancée d’indicateurs d’encodage permet d’optimiser le traitement (actualisation des données) des modèles tabulaires en mémoire volumineux. Pour en savoir plus, consultez l’article [Nouveautés dans SQL Server Analysis Services vNext](../analysis-services/what-s-new-in-sql-server-analysis-services-vnext.md). 

## <a name="whats-new-in-sql-server-vnext-ctp-12-january-2017"></a>Nouveautés de SQL Server vNext CTP 1.2 (janvier 2017)
### <a name="sql-server-database-engine"></a>Moteur de base de données SQL Server
- Prise en charge de la génération et de la régénération d’index en ligne pour les index columnstore non cluster.
- Cette version CTP contient également des correctifs de bogues pour le moteur de base de données.
- Pour obtenir la liste détaillée des améliorations apportées à vNext CTP, consultez l’article [Nouveautés de SQL Server vNext (moteur de base de données)](../database-engine/configure-windows/what-s-new-in-sql-server-vnext-database-engine.md).

### <a name="sql-server-r-services"></a>SQL Server R Services
- Il n’y a pas de nouvelles fonctionnalités R Services dans cette version CTP.
- Pour des informations plus détaillées sur les nouveautés R Services, notamment des détails sur les versions CTP précédentes, consultez [Nouveautés de SQL Server R Services](../advanced-analytics/r-services/what-s-new-in-sql-server-r-services.md).  

### <a name="sql-server-reporting-services-ssrs"></a>SQL Server Reporting Services (SSRS)
- Il n’y a pas de nouvelles fonctionnalités SSRS dans cette version CTP.
- Pour des informations plus détaillées sur les nouveautés de SSRS et sur les versions précédentes, consultez l’article [Nouveautés de Reporting Services (SSRS)](../reporting-services/nouveautés-de-sql-server-reporting-services-ssrs.md). 

### <a name="sql-server-analysis-services-ssas"></a>SQL Server Analysis Services (SSAS)
- Cette version CTP ne contient pas de nouvelles fonctionnalités SSAS.  
- Pour plus d'informations, consultez [Nouveautés d’Analysis Services](../analysis-services/what-s-new-in-sql-server-analysis-services-vnext.md).  

### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
- Il n’y a pas de nouvelles fonctionnalités SSIS dans cette version CTP.
- Pour des informations plus détaillées sur les nouveautés SSIS, consultez [Nouveautés d’Integration Services vNext](../integration-services/what-s-new-in-integration-services-in-sql-server-vnext.md).  

### <a name="master-data-services-mds"></a>Master Data Services (MDS)
- Il n’y a pas de nouvelles fonctionnalités Master Data Services dans cette version CTP.

##  <a name="infotipimageshiproominfotippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Contacter l’équipe d’ingénierie de SQL Server 
- [Stack Overflow (tag sql-server)](http://stackoverflow.com/questions/tagged/sql-server)
- [Forums MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect : signaler des bogues et demander des fonctionnalités](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit : discussion générale sur R](https://www.reddit.com/r/SQLServer/)

## <a name="see-also"></a>Voir aussi    
 + [![Notes de publication](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png)](SQL%20Server%20vNext%20Release%20Notes.md) [Notes de publication de SQL Server VNext](../sql-server/sql-server-vnext-release-notes.md). 
+ [Fonctionnalités prises en charge par l’édition](https://msdn.microsoft.com/library/cc645993.aspx)
 + [[Installation des configurations matérielle et logicielle requises](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)](Hardware%20and%20Software%20Requirements%20for%20Installing%20SQL%20Server%202016.md)
 + [Assistant Installation](../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md)
 
 + [Configuration et installation de maintenance](Setup%20and%20Servicing%20Installation.md)
 
 ![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)