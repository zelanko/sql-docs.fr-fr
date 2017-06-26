---
title: "Quelles sont les nouveautés dans SQL Server 2017 | Documents Microsoft"
ms.custom: 
ms.date: 06/19/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b57f375-9242-4bb2-9d4b-c560d5a93524
caps.latest.revision: 71
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: aa08b5e7de9bb317fd781a98ee5d829431b92df6
ms.openlocfilehash: 66c9bc4f2cba20076c357d27fdfacbc767a94c5c
ms.contentlocale: fr-fr
ms.lasthandoff: 06/23/2017

---
# <a name="what39s-new-in-sql-server-2017"></a>Quelles sont les nouveautés dans SQL Server 2017
SQL Server 2017 représente une étape importante sur la réalisation de SQL Server une plateforme qui vous donne le choix de langages de développement, les types de données, localement et dans le cloud et entre les systèmes d’exploitation en apportant la puissance de SQL Server pour Linux, conteneurs Docker de basés sur Linux et Windows.

Cette rubrique est un résumé des nouveautés de la mise en production Community Technical Preview (CTP) et des liens vers plus d’informations pour les zones de fonctionnalité spécifique sur les nouveautés les plus récentes.

![info_tip](../sql-server/media/info-tip.png) Exécutez SQL Server sur Linux ! Pour plus d'informations, consultez :
-  [Nouveautés de 2017 du serveur SQL sur Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-whats-new)
-  [Documentation de SQL Server sur Linux](https://docs.microsoft.com/sql/linux/)


**Essayez-le :**    
   -   [![Télécharger à partir du centre d’évaluation](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477)  **[télécharger le Kit de développement SQL Server 2017 Community Technology Preview](http://go.microsoft.com/fwlink/?LinkID=829477)**

## <a name="whats-new-in-sql-server-2017-ctp-21-may-2017"></a>Nouveautés de SQL Server CTP 2017 2.1 (mai 2017)
### <a name="sql-server-database-engine"></a>Moteur de base de données SQL Server  
- Un nouveau DMF, [sys.dm_db_log_stats](../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md), est introduit pour exposer les attributs de niveau résumés et plus d’informations sur les fichiers journaux des transactions ; utile pour surveiller l’intégrité du journal des transactions.  
- Cette version CTP contient des correctifs de bogues et améliorations des performances pour le moteur de base de données.
- Pour une liste détaillée des 2017 améliorations CTP dans les précédentes versions CTP, consultez [Nouveautés de SQL Server 2017 (moteur de base de données)](../database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md).

### <a name="sql-server-reporting-services-ssrs"></a>SQL Server Reporting Services (SSRS)
- SQL Server Reporting Services n’est plus disponible pour installer via le programme d’installation de SQL Server à partir de CTP 2.1.
- Commentaires sont maintenant disponibles pour les rapports. Commentaires permettent d’ajouter une perspective à ce qui est dans un rapport et de collaborer avec d’autres personnes de votre organisation. Vous pouvez également inclure des pièces jointes avec votre commentaire.
- Pour des informations plus détaillées sur les nouveautés de SSRS et sur les versions précédentes, consultez l’article [Nouveautés de Reporting Services (SSRS)](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md). 
- Pour plus d’informations sur le serveur de rapports Power BI, consultez [prise en main avec un serveur de rapports Power BI](https://powerbi.microsoft.com/documentation/reportserver-get-started/).

### <a name="sql-server-machine-learning-services"></a>Apprentissage des Services de l’ordinateur SQL Server
- Il n’y a aucune nouvelle fonctionnalité de Machine Learning Services dans cette version CTP.
- Pour plus Machine Learning Services que nouvelles informations, y compris les informations à partir des précédentes versions de CTP, consultez [Nouveautés de SQL Server Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).  

### <a name="sql-server-analysis-services-ssas"></a>SQL Server Analysis Services (SSAS)
- Cette version CTP ne contient pas de nouvelles fonctionnalités SSAS.  
- Pour plus d’informations sur les améliorations et correctifs de bogues dans cette version, consultez [Nouveautés de SQL Server 2017 Analysis Services](../analysis-services/what-s-new-in-sql-server-analysis-services-2017.md).  

### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
-   Vous pouvez maintenant utiliser le **Use32BitRuntime** paramètre.
-   Les performances de journalisation a été améliorée.
- Pour plus SSIS que nouvelles informations, y compris les informations à partir des précédentes versions de CTP, consultez [Nouveautés de SQL Server 2017 Integration Services](../integration-services/what-s-new-in-integration-services-in-sql-server-2017.md).  

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="whats-new-in-sql-server-2017-ctp-20-april-2017"></a>Nouveautés de SQL Server 2017 CTP 2.0 (avril 2017)
### <a name="sql-server-database-engine"></a>Moteur de base de données SQL Server
- **Reconstruction d’index en ligne peut être repris**. Reconstruction d’index en ligne peut être repris vous permet de reprendre une opération de reconstruction d’index en ligne où il a été arrêtée après une défaillance. Par exemple, un basculement vers un réplica ou d’une situation d’espace disque insuffisant. Vous pouvez également interrompre et reprendre ultérieurement une opération de reconstruction d’index en ligne. Par exemple, vous devrez peut-être temporairement libérer des ressources de systèmes afin d’exécuter une tâche de priorité élevée ou de terminer la reconstruction d’index dans une autre fenêtre miniatous si les fenêtres de maintenance disponible est trop courte pour une table de grande taille. Enfin, reconstruction d’index en ligne peut être repris ne nécessite pas d’espace journal significative, ce qui vous permet d’effectuer la troncation du journal pendant l’exécution de l’opération de reconstruction peut être repris. Consultez [ALTER INDEX](../t-sql/statements/alter-index-transact-sql.md) et [instructions pour les opérations d’index en ligne](../relational-databases/indexes/guidelines-for-online-index-operations.md).
- **Option IDENTITY_CACHE pour ALTER DATABASE SCOPED CONFIGURATION**. Une nouvelle option IDENTITY_CACHE a été ajoutée à l’instruction ALTER DATABASE portée CONFIGURATION T-SQL. Lorsque cette option est définie sur OFF, écarts peuvent être évités dans les valeurs des colonnes d’identité au cas où un serveur redémarre de façon inattendue ou bascule vers un serveur secondaire. Consultez [CONFIGURATION inclus dans l’étendue de base de données ALTER](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).  
- CLR utilise la sécurité d’accès de Code (CAS) dans le .NET Framework, qui n’est plus pris en charge comme une limite de sécurité. Un assembly CLR créé avec `PERMISSION_SET = SAFE` peuvent être en mesure d’accéder à des ressources système externes, appeler du code non managé et acquérir des privilèges sysadmin. À partir de [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)], un `sp_configure` option appelée `clr strict security` est introduit pour améliorer la sécurité des assemblys CLR. `clr strict security`est activé par défaut et traite `SAFE` et `EXTERNAL_ACCESS` assemblys comme si elles ont été marquées `UNSAFE`. Le `clr strict security` option peut être désactivée pour la compatibilité descendante, mais n’est ne pas recommandée. Microsoft recommande que tous les assemblys être signés par un certificat ou une clé asymétrique avec une connexion correspondante qui a été accordée `UNSAFE ASSEMBLY` autorisation dans la base de données master. Pour plus d’informations, consultez [stricte de sécurité CLR](../database-engine/configure-windows/clr-strict-security.md).  
- Fonctionnalités de base de données de graphique pour modéliser des relations plusieurs-à-plusieurs. Cela inclut de nouveaux [CREATE TABLE](../t-sql/statements/create-table-sql-graph.md) syntaxe permettant de créer le nœud et les tableaux de bord et le mot clé [correspondance](../t-sql/queries/match-sql-graph.md) pour les requêtes. Pour plus d’informations, consultez [de traitement graphique avec SQL Server 2017](../relational-databases/graphs/sql-graph-overview.md).   
- Le paramétrage automatique est une fonctionnalité de base de données qui fournit un aperçu de requête potentiel des problèmes de performances, il peut recommander des solutions et corriger automatiquement les problèmes identifiés. Le paramétrage automatique [!INCLUDE[ssnoversion](../includes/ssnoversion.md)], vous avertit chaque fois qu’un problème de performance potentiel est détecté et vous permet d’appliquer des actions correctives, ou vous permet du [!INCLUDE[ssde](../includes/ssde-md.md)] résoudre automatiquement les problèmes de performances. Pour plus d’informations, consultez [le paramétrage automatique](../relational-databases/automatic-tuning/automatic-tuning.md).  
-   Lot Mode Adaptive joindre à améliorer la qualité du plan (sous compatibilité db 140).
-   Exécution entrelacée de T-SQL multi-instruction améliorer la qualité du plan (sous compatibilité 140 de base de données).
- Magasin de requêtes maintenant suit également les informations de résumé de statistiques attente. Catégories de statistiques d’attente par la requête dans le magasin de requêtes de suivi permet le niveau de performances expérience de résolution des problèmes, en fournissant, voire plus, son les goulots d’étranglement tout en conservant les avantages clés de magasin de requêtes et les performances de la charge de travail suivant.
- Prise en charge DTC pour les groupes de disponibilité AlwaysOn pour toutes les transactions de base de données croisées entre les bases de données qui font partie du groupe de disponibilité, y compris les bases de données qui font partie de la même instance. Pour plus d’informations, consultez [Transactions - mise en miroir de base de données et les groupes de disponibilité AlwaysOn](../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)
- Une nouvelle colonne **modified_extent_page_count** a été introduit dans [sys.dm_db_file_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md) pour effectuer le suivi des modifications différentielles dans chaque fichier de base de données de la base de données.
- [SELECT INTO](../t-sql/queries/select-into-clause-transact-sql.md) prend désormais en charge le chargement d’une table dans un groupe de fichiers autres que d’un groupe de fichiers par défaut de l’utilisateur à l’aide du **ON** (mot clé).
- Le programme d’installation de SQL Server prend en charge la spécification de taille de fichier tempdb initial jusqu'à **256 Go (262 144 Mo)** par fichier avec un avertissement si la taille du fichier est définie à une valeur supérieure à **1 Go** et si IFI n’est pas activé.
- Une vue de gestion dynamique nouvelles (DMV) [sys.dm_tran_version_store_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-space-usage.md) est introduit pour suivre l’utilisation du magasin de version par base de données.
- Une vue de gestion dynamique [sys.dm_db_log_info](../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md) est introduit pour exposer les informations de fichier journal virtuel similaires à DBCC LOGINFO.
- Tables temporelles avec version système prennent désormais en charge la mise à jour en CASCADE et suppression en CASCADE.
- Cette version CTP contient des correctifs de bogues pour le moteur de base de données.
- Pour une liste détaillée des 2017 améliorations CTP dans les précédentes versions CTP, consultez [Nouveautés de SQL Server 2017 (moteur de base de données)](../database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md).   

### <a name="sql-server-machine-learning-services"></a>Apprentissage des Services de l’ordinateur SQL Server
- SQL Server R Services a un nouveau nom, afin de refléter la prise en charge pour le langage Python dans CTP 2.0. Vous pouvez désormais utiliser SQL Server Machine Learning Services (de-de base de données) pour exécuter des scripts R ou Python dans SQL Server. Ou bien, installez Microsoft Machine Learning Server (autonome) pour déployer et utiliser des modèles R et Python, qui ne nécessitent pas SQL Server. 
- Les deux plateformes incluent les nouveaux algorithmes MicrosoftML pour distribuée d’apprentissage et de la dernière version de Microsoft R (version 9.1.0).
- Pour plus d’informations, consultez [Nouveautés pour l’apprentissage](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="whats-new-in-sql-server-2017-ctp-14-march-2017"></a>Nouveautés de SQL Server 2017 CTP 1.4 (mars 2017)
### <a name="sql-server-database-engine"></a>Moteur de base de données SQL Server
- Il n’y a pas de nouvelles fonctionnalités de moteur de base de données dans cette version CTP.
- Cette version CTP contient des correctifs de bogues pour le moteur de base de données.
- Pour une liste détaillée des 2017 améliorations CTP dans les précédentes versions CTP, consultez [Nouveautés de SQL Server 2017 (moteur de base de données)](../database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md).

### <a name="sql-server-r-services"></a>SQL Server R Services
- Il n’y a pas de nouvelles fonctionnalités R Services dans cette version CTP.
- Pour des informations plus détaillées sur les nouveautés R Services, notamment des détails sur les versions CTP précédentes, consultez [Nouveautés de SQL Server R Services](../advanced-analytics/r-services/what-s-new-in-sql-server-r-services.md).  

### <a name="sql-server-reporting-services-ssrs"></a>SQL Server Reporting Services (SSRS)
- Il n’y a pas de nouvelles fonctionnalités SSRS dans cette version CTP.
- Pour des informations plus détaillées sur les nouveautés de SSRS et sur les versions précédentes, consultez l’article [Nouveautés de Reporting Services (SSRS)](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md). 

### <a name="sql-server-analysis-services-ssas"></a>SQL Server Analysis Services (SSAS)
- Cette version CTP ne contient pas de nouvelles fonctionnalités SSAS.  
- Pour plus d’informations, notamment les nouveautés dans les dernières versions preview de SSDT et SSMS, pour Analysis Services, consultez [Nouveautés dans Analysis Services 2017](../analysis-services/what-s-new-in-sql-server-analysis-services-2017.md).  

### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
- Il n’y a pas de nouvelles fonctionnalités SSIS dans cette version CTP.
- Pour plus SSIS que nouvelles informations, y compris les informations à partir des précédentes versions de CTP, consultez [Nouveautés Integration Services 2017](../integration-services/what-s-new-in-integration-services-in-sql-server-2017.md).  

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="whats-new-in-sql-server-2017-ctp-13-february-2017"></a>Nouveautés de SQL Server CTP 2017 1.3 (février 2017)
### <a name="sql-server-database-engine"></a>Moteur de base de données SQL Server
- Améliorations des performances des points de contrôle indirects.
- Ajout de la prise en charge des groupes de disponibilité sans cluster.
- Ajout du paramètre des groupes de disponibilité à validation de réplica minimale.
- Les groupes de disponibilité peuvent désormais fonctionner sur Windows-Linux pour activer les migrations entre systèmes d’exploitation et les tests.
- Stratégie de rétention de Tables prise en charge temporelle ajouté. Pour plus d’informations, consultez [gérer rétention des données d’historique dans les Tables temporelles avec version système](../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md#using-temporal-history-retention-policy-approach).
- Nouvel élément DMV SYS.DM_DB_STATS_HISTOGRAM.
- En ligne columnstore non cluster génération d’index et reconstruire prend désormais en charge
- Ajout de&5; nouvelles vues de gestion dynamique pour retourner des informations sur le processus Linux. Pour plus d’informations, consultez l’article [Vues de gestion dynamique de processus Linux (Transact-SQL)](../relational-databases/system-dynamic-management-views/linux-process-dynamic-management-views-transact-sql.md).   
- Le paramètre[Sys.dm_db_stats_histogram (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) est ajouté pour l’examen des statistiques.

### <a name="sql-server-analysis-services-ssas-ctp-13"></a>SQL Server Analysis Services (SSAS) (CTP 1.3)
- La fonctionnalité avancée d’indicateurs d’encodage permet d’optimiser le traitement (actualisation des données) des modèles tabulaires en mémoire volumineux. Pour plus d’informations, consultez [Nouveautés dans Analysis Services 2017](../analysis-services/what-s-new-in-sql-server-analysis-services-2017.md). 


![horizontal_bar](../sql-server/media/horizontal-bar.png)

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Contacter l’équipe d’ingénierie de SQL Server 
- [Stack Overflow (tag sql-server)](http://stackoverflow.com/questions/tagged/sql-server)
- [Forums MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect : signaler des bogues et demander des fonctionnalités](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit : discussion générale sur R](https://www.reddit.com/r/SQLServer/)

## <a name="see-also"></a>Voir aussi    
- ![Notes de publication](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png) [notes de mise à jour de SQL Server 2017](../sql-server/sql-server-2017-release-notes.md). 
- [Fonctionnalités prises en charge par l’édition](https://msdn.microsoft.com/library/cc645993.aspx)
- [Installation des configurations matérielle et logicielle requises](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)
- [Assistant Installation de SQL Server](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)
- [Installer les mises à jour de maintenance de SQL Server](http://msdn.microsoft.com/library/6df72a78-6b36-4bc1-948e-04b4ebe46094)
 
 ![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)

