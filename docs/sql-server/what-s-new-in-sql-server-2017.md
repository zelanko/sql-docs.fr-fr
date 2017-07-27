---
title: "Nouveautés de SQL Server 2017 | Microsoft Docs"
ms.custom: 
ms.date: 07/12/2017
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
ms.translationtype: HT
ms.sourcegitcommit: 71203bfa7cb4dcd06cc14ad8e49e5bc1113f8605
ms.openlocfilehash: 731d53110d9dc47de5a44dd7f65190e029e120dc
ms.contentlocale: fr-fr
ms.lasthandoff: 07/19/2017

---
# <a name="whats-new-in-sql-server-2017"></a>Nouveautés de SQL Server 2017
SQL Server 2017 représente une étape importante pour faire de SQL Server une plateforme vous offrant des choix en matière de langages de développement, de types de données, d’utilisation locale ou dans le cloud et de systèmes d’exploitation, en apportant la puissance de SQL Server à Linux, aux conteneurs Docker basés sur Linux et à Windows. Cette rubrique récapitule les nouveautés pour des composants spécifiques dans les dernières versions SQL Server 2017 Release Candidate (RC1, juillet 2017) et Community Technical Preview (CTP).

**Faites un essai :** [Téléchargez SQL Server 2017 Release Candidate (RC)](http://go.microsoft.com/fwlink/?LinkID=829477)

>[!TIP]
>**Exécutez SQL Server sur Linux !** Pour plus d’informations, consultez [Documentation de SQL Server sur Linux](https://docs.microsoft.com/sql/linux/) et [Nouveautés de SQL Server 2017 sur Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-whats-new).

## <a name="latest-release-sql-server-2017-release-candidate-rc1-july-2017"></a>Version la plus récente : SQL Server 2017 Release Candidate (RC1, juillet 2017)

### <a name="sql-server-database-engine"></a>Moteur de base de données SQL Server    
- Les assemblys CLR peuvent maintenant être ajoutés à une liste approuvée, comme une solution de contournement pour la fonctionnalité `clr strict security` décrite dans la version CTP 2.0. [sp_add_trusted_assembly](../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md), [sp_drop_trusted_assembly](../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md) et [sys.trusted_asssemblies](../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md) sont ajoutés pour prendre en charge la liste des assemblys approuvés.  

### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
- La nouvelle fonctionnalité **Scale Out** dans SSIS présente les fonctions nouvelles et modifiées suivantes dans la version RC1. Pour plus d’informations, consultez [Nouveautés d’Integration Services dans SQL Server 2017](~/integration-services/what-s-new-in-integration-services-in-sql-server-2017.md).
    -   Scale Out Master prend désormais en charge la haute disponibilité.
    -   La gestion de basculement des journaux d’exécution des Scale Out Workers est améliorée.
    -   Le paramètre *runincluster* de la procédure stockée **[catalog].[create_execution]** est renommé en *runinscaleout* pour des raisons de cohérence et de lisibilité.
    -   Le catalogue SSIS a une nouvelle propriété globale afin de spécifier le mode par défaut pour l’exécution de packages SSIS.

## <a name="sql-server-database-engine"></a>Moteur de base de données SQL Server  
SQL Server 2017 inclut de nombreuses nouvelles fonctionnalités du moteur de base de données, des perfectionnements et des améliorations des performances. 
- La **reconstruction d’index en ligne pouvant être reprise** reprend une opération de reconstruction d’index en ligne là où elle s’est arrêtée après un échec (par exemple, un basculement vers un réplica ou un espace disque insuffisant), ou s’arrête et reprend ultérieurement une opération de reconstruction d’index en ligne. Consultez [ALTER INDEX](../t-sql/statements/alter-index-transact-sql.md) et [instructions pour les opérations d’index en ligne](../relational-databases/indexes/guidelines-for-online-index-operations.md). (CTP 2.0)
- L’option **IDENTITY_CACHE** pour ALTER DATABASE SCOPED CONFIGURATION vous permet d’éviter les écarts dans les valeurs des colonnes d’identité si un serveur redémarre de façon inattendue ou bascule vers un serveur secondaire. Consultez [CONFIGURATION inclus dans l’étendue de base de données ALTER](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md). (CTP 2.0)
- Le **paramétrage de base de données automatique** permet de connaître les éventuels problèmes de performances des requêtes, recommande des solutions et peut corriger automatiquement les problèmes identifiés. Consultez [Paramétrage automatique](../relational-databases/automatic-tuning/automatic-tuning.md). (CTP 2.0)
- Les nouvelles **fonctionnalités de base de données des graphiques** pour la modélisation des relations plusieurs à plusieurs contiennent une nouvelle syntaxe [CREATE TABLE](../t-sql/statements/create-table-sql-graph.md) permettant de créer des tables de nœuds et d’arêtes ainsi que le mot clé [MATCH](../t-sql/queries/match-sql-graph.md) pour les requêtes. Consultez [Traitement des graphiques avec SQL Server 2017](../relational-databases/graphs/sql-graph-overview.md). (CTP 2.0)
- Une option sp_configure appelée `clr strict security` est activée par défaut pour améliorer la sécurité des assemblys CLR. Consultez [Sécurité CLR stricte](../database-engine/configure-windows/clr-strict-security.md). (CTP 2.0)
- Le programme d’installation permet maintenant de spécifier une taille de fichier tempdb initiale pouvant atteindre **256 Go** (262 144 Mo) par fichier, avec un avertissement généré si la taille du fichier a une valeur supérieure à 1 Go sans que l’initialisation IFI ne soit activée. (CTP 2.0)
- La colonne **modified_extent_page_count** dans [sys.dm_db_file_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md) effectue le suivi des modifications différentielles dans chaque fichier de base de données, en activant des solutions Smart Backup qui effectuent une sauvegarde différentielle ou complète basée sur le pourcentage de pages modifiées dans la base de données. (CTP 2.0)
- La syntaxe T-SQL [SELECT INTO](../t-sql/queries/select-into-clause-transact-sql.md) prend désormais en charge le chargement d’une table dans un groupe de fichiers différent de celui par défaut de l’utilisateur à l’aide du mot clé **ON**. (CTP 2.0)
- Les transactions de bases de données croisées sont maintenant prises en charge parmi toutes les bases de données qui font partie d’un **groupe de disponibilité Always On**, dont les bases de données qui font partie de la même instance. Consultez [Transactions : groupes de disponibilité Always On et mise en miroir de bases de données](../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md) (CTP 2.0)
- La nouvelle fonctionnalité **Groupes de disponibilité** comprend la prise en charge sans cluster, le paramètre de groupe de disponibilité à validation de réplica minimale ainsi que les migrations et les tests entre systèmes d’exploitation Windows-Linux. (CTP 1.3)
- Nouvelles vues de gestion dynamique :
    - [sys.dm_db_log_stats](../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md) expose des informations et des attributs de niveau résumé sur les fichiers journaux des transactions, utiles pour surveiller l’intégrité du journal des transactions. (CTP 2.1)
    - [sys.dm_tran_version_store_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-space-usage.md) effectue le suivi de l’utilisation de la banque des versions par base de données, ce qui permet de planifier de manière proactive le dimensionnement de tempdb selon cette utilisation. (CTP 2.0)
    - [sys.dm_db_log_info](../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md) expose les informations du fichier journal virtuel pour surveiller, signaler et éviter les éventuels problèmes liés aux journaux des transactions. (CTP 2.0)
    - [sys.dm_db_stats_histogram](../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) est une nouvelle vue de gestion dynamique pour l’examen des statistiques. (CTP 1.3)
    - **sys.dm_os_host_info** fournit des informations sur les systèmes d’exploitation Windows et Linux. (CTP 1.0)
- L’**Assistant Paramétrage de base de données** présente d’autres options et des performances améliorées. (CTP 1.2)
- Les **améliorations en mémoire** incluent la prise en charge des colonnes calculées dans les tables à mémoire optimisée, la prise en charge complète des fonctions JSON dans les modules compilés en mode natif et l’opérateur CROSS APPLY dans les modules compilés en mode natif. (CTP 1.1)
- Les nouvelles **fonctions de chaîne** sont CONCAT_WS, TRANSLATE et TRIM, et WITHIN GROUP est maintenant pris en charge pour la fonction STRING_AGG. (CTP 1.1)
- Il existe de nouvelles **options d’accès en bloc** (BULK INSERT et OPENROWSET(BULK...)) pour les fichiers CSV et d’objets blob Azure. (CTP 1.1)
- Les **améliorations des objets à mémoire optimisée** incluent sp_spaceused et l’élimination de la limite de 8 index pour les tables à mémoire optimisée, sp_rename pour les tables à mémoire optimisée et les modules T-SQL compilés en mode natif, ainsi que CASE et TOP (N) WITH TIES pour les modules T-SQL compilés en mode natif. Les fichiers de groupes de fichiers à mémoire optimisée peuvent maintenant être stockés, sauvegardés et restaurés sur le stockage Azure. (CTP 1.0)
- **DATABASE SCOPED CREDENTIAL** est une nouvelle classe d’élément sécurisable, prenant en charge les autorisations CONTROL, ALTER, REFERENCES, TAKE OWNERSHIP et VIEW DEFINITION. ADMINISTER DATABASE BULK OPERATIONS est désormais visible dans sys.fn_builtin_permissions. (CTP 1.0)
- Le niveau de compatibilité **COMPATIBILITY_LEVEL 140** de base de données a été ajouté. (CTP 1.0).  

Pour plus d’informations, consultez [Nouveautés du moteur de base de données SQL Server 2017](~/database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md).

## <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
- La nouvelle fonctionnalité **Scale Out** dans SSIS présente les fonctions nouvelles et modifiées suivantes. Pour plus d’informations, consultez [Nouveautés d’Integration Services dans SQL Server 2017](~/integration-services/what-s-new-in-integration-services-in-sql-server-2017.md). (RC1)
    -   Scale Out Master prend désormais en charge la haute disponibilité.
    -   La gestion de basculement des journaux d’exécution des Scale Out Workers est améliorée.
    -   Le paramètre *runincluster* de la procédure stockée **[catalog].[create_execution]** est renommé en *runinscaleout* pour des raisons de cohérence et de lisibilité.
    -   Le catalogue SSIS a une nouvelle propriété globale afin de spécifier le mode par défaut pour l’exécution de packages SSIS.
- Dans la nouvelle fonctionnalité **Scale Out pour SSIS**, vous pouvez maintenant utiliser le paramètre **Use32BitRuntime** quand vous déclenchez l’exécution. (CTP 2.1)
- SQL Server 2017 Integration Services (SSIS) prend désormais en charge **SQL Server sur Linux** et un nouveau package vous permet d’exécuter des packages SSIS sur Linux à partir de la ligne de commande. Pour plus d’informations, consultez le [billet de blog annonçant la prise en charge de SSIS pour Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/). (CTP 2.1)
- La nouvelle fonctionnalité **Scale Out pour SSIS** facilite grandement l’exécution de SSIS sur plusieurs ordinateurs. Consultez [Integration Services Scale Out](~/integration-services/integration-services-ssis-scale-out.md). (CTP 1.0)
- OData Source et le gestionnaire de connexions OData prennent désormais en charge la connexion aux flux OData de Microsoft Dynamics AX Online et Microsoft Dynamics CRM Online. (CTP 1.0)

Pour plus d’informations, consultez [Nouveautés d’Integration Services dans SQL Server 2017](~/integration-services/what-s-new-in-integration-services-in-sql-server-2017.md).

## <a name="sql-server-analysis-services-ssas"></a>SQL Server Analysis Services (SSAS) 
SQL Server Analysis Services 2017 introduit de nombreuses améliorations pour les modèles tabulaires. notamment :
- Mode tabulaire comme option d’installation par défaut pour Analysis Services. (CTP 2.0)
- Sécurité au niveau objet pour sécuriser les métadonnées des modèles tabulaires. (CTP 2.0)
- Relations de dates pour créer facilement des relations basées sur les champs de date. (CTP 2.0)
- Les nouvelles sources de données **Obtenir des données** (Power Query) et sources de données DirectQuery existantes prennent en charge les requêtes M. (CTP 2.0) 
- Éditeur DAX pour SSDT. (CTP 2.0)
- Indications de codage, une fonctionnalité avancée qui permet d’optimiser l’actualisation des données des modèles tabulaires en mémoire volumineux. (CTP 1.3)
- Prise en charge du **niveau de compatibilité 1400** pour les modèles tabulaires. Pour créer des projets de modèles tabulaires ou mettre à niveau des projets de modèles tabulaires existants vers le niveau de compatibilité 1400, téléchargez et installez [SQL Server Data Tools (SSDT) 17.0 RC2](https://go.microsoft.com/fwlink?LinkId=837939). (CTP 1.1)
- Expérience **Obtenir des données** moderne pour les modèles tabulaires au niveau de compatibilité 1400. Consultez le [blog de l’équipe Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2016/12/16/introducing-a-modern-get-data-experience-for-sql-server-2017-on-windows-ctp-1-1-for-analysis-services/). (CTP 1.1)
- Propriété **Masquer des membres** pour masquer les membres vides dans les hiérarchies irrégulières. (CTP 1.1)
- Nouvelle action de l’utilisateur final **Lignes de détails** pour **Afficher les détails** des informations globales. Fonctions [SELECTCOLUMNS](https://msdn.microsoft.com/library/mt761759.aspx) et **DETAILROWS** pour créer des expressions Lignes de détails. (CTP 1.1)
- Opérateur DAX **IN** pour spécifier plusieurs valeurs. (CTP 1.1)

Pour plus d’informations, consultez [Nouveautés de SQL Server Analysis Services 2017](~/analysis-services/what-s-new-in-sql-server-analysis-services-2017.md).

## <a name="sql-server-reporting-services-ssrs"></a>SQL Server Reporting Services (SSRS)
À partir de CTP 2.1, SSRS n’est plus disponible pour une installation via le programme d’installation de SQL Server. Accédez au Centre de téléchargement Microsoft pour [télécharger la préversion de mai 2017 de Power BI Report Server et Power BI Desktop optimisé pour Power BI Report Server](https://www.microsoft.com/download/details.aspx?id=55253). Pour plus d’informations sur le serveur de rapports Power BI, consultez [prise en main avec un serveur de rapports Power BI](https://powerbi.microsoft.com/documentation/reportserver-get-started/).
- Des commentaires sont maintenant disponibles pour les rapports, pour ajouter une perspective et collaborer avec d’autres utilisateurs. Vous pouvez également inclure des pièces jointes avec des commentaires. (CTP 2.1)
- Dans les dernières versions du Générateur de rapports et SQL Server Data Tools, vous pouvez créer des requêtes DAX natives sur des modèles de données tabulaires SQL Server Analysis Services pris en charge en faisant glisser les champs voulus dans les concepteurs de requêtes. Consultez le [blog de Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/2017/03/09/query-designer-support-for-dax-now-available-in-report-builder-and-sql-server-data-tools/).

Pour plus d’informations, consultez [Nouveautés de SQL Server Reporting Services (SSRS)](~/reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md).

## <a name="sql-server-machine-learning-services"></a>Apprentissage des Services de l’ordinateur SQL Server
SQL Server R Services est maintenant renommé **SQL Server Machine Learning Services** afin de refléter la nouvelle prise en charge de Python en plus des langages R. Vous pouvez utiliser Machine Learning Services (en base de données) pour exécuter des scripts R ou Python dans SQL Server, ou installer Microsoft Machine Learning Server (autonome) pour déployer et utiliser des modèles R et Python qui ne nécessitent pas SQL Server. Les deux plateformes incluent les nouveaux algorithmes MicrosoftML pour distribuée d’apprentissage et de la dernière version de Microsoft R (version 9.1.0). (CTP 2.0)
- Machine Learning avec Python inclut le module **revoscalepy**, qui prend en charge un sous-ensemble des algorithmes distribués et des contextes de calcul fournis dans RevoScaleR. 
- Vous pouvez facilement créer plusieurs modèles en parallèle à partir de R à l’aide de la nouvelle fonction **rxExecBy**. Les contextes de calcul pris en charge incluent RxSpark et RxInSQLServer. (CTP 2.0)

Pour plus d’informations, consultez [Nouveautés de SQL Server Machine Learning Services](~/advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).

## <a name="next-steps"></a>Étapes suivantes
- Consultez les [Notes de publication de SQL Server 2017](sql-server-2017-release-notes.md).
- Découvrez les [Nouveautés de SQL Server 2016](what-s-new-in-sql-server-2016.md).

