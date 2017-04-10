---
title: "Surveiller la r&#233;plication par programme | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "sp_replmonitorhelppublisher"
  - "sp_replmonitorhelpmergesessiondetail"
  - "monitoring performance [SQL Server replication], publication status"
  - "sp_replmonitorhelpmergesession"
  - "sp_replmonitorhelppublicationthresholds"
  - "monitoring performance [SQL Server replication], subscription status"
  - "monitoring performance [SQL Server replication], Transact-SQL programming"
  - "sp_replmonitorsubscriptionpendingcmds"
  - "sp_replmonitorchangepublicationthreshold"
  - "transactional replication, monitoring"
  - "sp_replmonitorhelppublication"
  - "sp_replmonitorhelpsubscription"
  - "monitoring performance [SQL Server replication], thresholds and warnings"
  - "merge replication monitoring [SQL Server replication]"
  - "réplication de capture instantanée [SQL Server], analyse"
ms.assetid: e8bf8850-8da5-4a4f-a399-64232b4e476d
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# Surveiller la r&#233;plication par programme
  Le moniteur de réplication est un outil graphique permettant d'analyser une topologie de réplication. Vous pouvez accéder par programmation aux mêmes données d'analyse en utilisant les procédures stockées de réplication [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou les objets RMO (Replication Management Objects). Ces objets permettent de programmer les tâches suivantes :  
  
-   Analyser l'état des serveurs de publication, des publications et des abonnements.  
  
-   Analyser les sessions de l'Agent de fusion sur un ou plusieurs Abonnés.  
  
-   Analyser les commandes transactionnelles en attente d'application sur un ou plusieurs Abonnés.  
  
-   Définir la métrique de seuil qui détermine quand une publication nécessite une intervention.  
  
-   Analyser l'état des jetons de suivi.  
  
 **Dans cette rubrique :**  
  
 [Transact-SQL](#Tsql)  
  
 [Objets RMO (Replication Management Objects)](#RMO)  
  
##  <a name="Tsql"></a> Transact-SQL  
  
#### Analyser les serveurs de publication, les publications et les abonnements du serveur de distribution.  
  
1.  Sur le serveur de distribution sur la base de données de distribution, exécutez [sp_replmonitorhelppublisher](../../../relational-databases/system-stored-procedures/sp-replmonitorhelppublisher-transact-sql.md). Les informations d'analyse pour tous les serveurs de publication utilisant ce serveur de distribution sont ainsi retournées. Pour limiter le jeu de résultats à un seul serveur de publication, spécifiez **@publisher**.  
  
2.  Sur le serveur de distribution sur la base de données de distribution, exécutez [sp_replmonitorhelppublication](../../../relational-databases/system-stored-procedures/sp-replmonitorhelppublication-transact-sql.md). Les informations d'analyse pour tous les serveurs de publication utilisant ce serveur de distribution sont ainsi retournées. Pour limiter le jeu de résultats à un serveur de publication, la publication ou la base de données publiée, spécifiez **@publisher**, **@publication**, ou **@publisher_db**, respectivement.  
  
3.  Sur le serveur de distribution sur la base de données de distribution, exécutez [sp_replmonitorhelpsubscription](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpsubscription-transact-sql.md). Les informations d'analyse pour tous les abonnements utilisant ce serveur de distribution sont ainsi retournées. Pour limiter les résultats aux abonnements appartenant à un serveur de publication, publication ou une base de données publiée, spécifiez **@publisher**, **@publication**, ou **@publisher_db**, respectivement.  
  
#### Pour analyser les commandes transactionnelles en attente d'application sur l'Abonné  
  
1.  Sur le serveur de distribution sur la base de données de distribution, exécutez [sp_replmonitorsubscriptionpendingcmds](../../../relational-databases/system-stored-procedures/sp-replmonitorsubscriptionpendingcmds-transact-sql.md). Les informations d'analyse pour toutes les commandes en attente de tous les abonnements utilisant ce serveur de distribution sont ainsi retournées. Pour limiter le jeu de résultats aux commandes en attente pour les abonnements appartenant à un serveur de publication, abonnés, de publication ou de base de données publiée, spécifiez **@publisher**, **@subscriber**, **@publication**, ou **@publisher_db**, respectivement.  
  
#### Pour analyser les modifications de fusion en attente de chargement ou de téléchargement  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_showpendingchanges](../../../relational-databases/system-stored-procedures/sp-showpendingchanges-transact-sql.md). Retourne un jeu de résultats affichant des informations sur les modifications en attente de réplication sur les Abonnés. Pour limiter le jeu de résultats aux modifications qui appartiennent à une publication ou un article unique, spécifiez respectivement **@publication** ou **@article**.  
  
2.  Un abonné sur la base de données d’abonnement, exécutez [sp_showpendingchanges](../../../relational-databases/system-stored-procedures/sp-showpendingchanges-transact-sql.md). Retourne un jeu de résultats affichant des informations sur les modifications en attente de réplication sur le serveur de publication. Pour limiter le jeu de résultats aux modifications qui appartiennent à une publication ou un article unique, spécifiez respectivement **@publication** ou **@article**.  
  
#### Pour analyser les sessions de l'Agent de fusion  
  
1.  Sur le serveur de distribution sur la base de données de distribution, exécutez [sp_replmonitorhelpmergesession](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesession-transact-sql.md). Cela renvoie des informations d’analyse, y compris **Session_id**, sur toutes les sessions de l’Agent de fusion pour tous les abonnements à l’aide de ce serveur de distribution. Vous pouvez également obtenir **Session_id** en interrogeant le [MSmerge_sessions](../../../relational-databases/system-tables/msmerge-sessions-transact-sql.md) (table système).  
  
2.  Sur le serveur de distribution sur la base de données de distribution, exécutez [sp_replmonitorhelpmergesessiondetail](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesessiondetail-transact-sql.md). Spécifiez un **Session_id** valeur à l’étape 1 pour **@session_id**. Les informations d'analyse détaillées sur la session sont ainsi affichées.  
  
3.  Répétez l'étape 2 pour chaque session digne d'intérêt.  
  
#### Pour analyser les sessions de l'Agent de fusion pour les abonnements par extraction de l'Abonné  
  
1.  Sur la base de données d’abonnement de l’abonné, exécutez [sp_replmonitorhelpmergesession](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesession-transact-sql.md). Pour un abonnement donné, spécifiez **@publisher**, **@publication**, et le nom de la base de données de publication pour **@publisher_db**. Cela retourne des informations d'analyse sur les cinq dernières sessions de l'Agent de fusion pour cet abonnement. Notez la valeur de **Session_id** pour les sessions dignes d’intérêt dans le résultat défini.  
  
2.  Sur la base de données d’abonnement de l’abonné, exécutez [sp_replmonitorhelpmergesessiondetail](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesessiondetail-transact-sql.md). Spécifiez un **Session_id** valeur à l’étape 1 pour **@session_id**. Les informations d'analyse détaillées sur la session sont ainsi affichées.  
  
3.  Répétez l'étape 2 pour chaque session digne d'intérêt.  
  
#### Pour afficher et modifier la métrique du seuil d'analyse pour une publication  
  
1.  Sur le serveur de distribution sur la base de données de distribution, exécutez [sp_replmonitorhelppublicationthresholds](../../../relational-databases/system-stored-procedures/sp-replmonitorhelppublicationthresholds-transact-sql.md). Les seuils d'analyse définis pour toutes les publications utilisant ce serveur de distribution sont ainsi retournées. Pour limiter le jeu de résultats à surveiller les seuils pour les publications appartenant à un seul éditeur ou d’une base de données publiée ou à une seule publication, spécifiez **@publisher**, **@publisher_db**, ou **@publication**, respectivement. Notez la valeur de **Metric_id** pour les seuils qui doivent être modifiés. Pour plus d’informations, consultez [définition des seuils et des avertissements dans le moniteur de réplication](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
2.  Sur le serveur de distribution sur la base de données de distribution, exécutez [sp_replmonitorchangepublicationthreshold](../../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md). Spécifiez les éléments suivants si nécessaire :  
  
    -   Le **Metric_id** valeur obtenue à l’étape 1 pour **@metric_id**.  
  
    -   Une nouvelle valeur pour le métrique du seuil d'analyse pour **@value**.  
  
    -   Une valeur de **1** pour **@shouldalert** pour une alerte à enregistrer lorsque ce seuil est atteint, ou une valeur de **0** si une alerte n'est pas nécessaire.  
  
    -   Valeur de **1** pour **@mode** afin d'activer la métrique du seuil d'analyse ou valeur de **2** pour la désactiver.  
  
##  <a name="RMO"></a> Objets RMO (Replication Management Objects)  
  
#### Pour surveiller un abonnement à une publication de fusion sur l'Abonné  
  
1.  Créer une connexion à l’abonné à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créer une instance de la <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor> puis définissez la <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.Publisher%2A>, <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.Publication%2A>, <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.PublisherDB%2A>, <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.SubscriberDB%2A> Propriétés de l’abonnement et définissez la <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> créé à l’étape 1.  
  
3.  Appelez l'une des méthodes suivantes pour retourner les informations sur les sessions de l'Agent de fusion de cet abonnement :  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummary%2A> -Retourne un tableau de <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> objets avec des informations sur les cinq dernières sessions de l’Agent de fusion. Remarque la <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> valeur pour toutes les sessions dignes d’intérêt.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummary%2A> -Retourne un tableau de <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> objets contenant des informations sur les sessions de l’Agent de fusion qui se sont produites pendant le nombre d’heures transmis comme passé le *heures* paramètre (jusqu’aux cinq dernières sessions). Remarque la <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> valeur pour toutes les sessions dignes d’intérêt.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetLastSessionSummary%2A> -retourne un <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> objet contenant des informations sur la dernière session de l’Agent de fusion. Remarque la <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> valeur pour cette session.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummaryDataSet%2A> -retourne un <xref:System.Data.DataSet> objet avec des informations sur les cinq dernières sessions de l’Agent de fusion, un par ligne. Notez la valeur de la **Session_id** colonne pour toutes les sessions dignes d’intérêt.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetLastSessionSummaryDataRow%2A> -retourne un <xref:System.Data.DataRow> objet contenant des informations sur la dernière session de l’Agent de fusion. Notez la valeur de la **Session_id** colonne pour cette session.  
  
4.  (Facultatif) Appelez <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.RefreshSessionSummary%2A> Pour actualiser les données de la <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> objet passé en tant que *mss,* ou appelez <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.RefreshSessionSummary%2A> pour actualiser les données dans le <xref:System.Data.DataRow> objet passé en tant que *drRefresh*.  
  
5.  À l'aide de l'ID de session obtenu à l'étape 3, appelez l'une des méthodes suivantes pour retourner les informations sur les détails d'une session particulière :  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionDetails%2A> -retourne un tableau de <xref:Microsoft.SqlServer.Replication.MergeSessionDetail> objets fourni *SessionId*.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionDetailsDataSet%2A> -retourne un <xref:System.Data.DataSet> objet contenant des informations pour l’objet *SessionId*.  
  
#### Pour surveiller les propriétés de réplication de toutes les publications sur un serveur de distribution  
  
1.  Créer une connexion au serveur de distribution à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.ReplicationMonitor> (classe).  
  
3.  Définir le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété du <xref:Microsoft.SqlServer.Management.Common.ServerConnection> créé à l’étape 1.  
  
4.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet.  
  
5.  Exécutez une ou plusieurs des méthodes suivantes pour retourner les informations de réplication de tous les serveurs de publication qui utilisent ce serveur de distribution.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumDistributionAgents%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations sur tous les Agents de Distribution sur ce serveur de distribution.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumErrorRecords%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations sur les erreurs stockées sur le serveur de distribution.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumLogReaderAgents%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations sur tous les Agents de lecture du journal sur le serveur de distribution.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumMergeAgents%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations sur tous les Agents de fusion sur le distributeur.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumMiscellaneousAgents%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations sur tous les autres agents de réplication sur le serveur de distribution.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumPublishers%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations sur tous les serveurs de publication sur ce serveur de distribution.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumPublishers2%2A> -retourne un <xref:System.Data.DataSet> objet par les serveurs de publication qui utilisent ce serveur de distribution.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgents%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations sur tous les Agents de lecture de file d’attente sur le serveur de distribution.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgentSessionDetails%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des détails sur l’Agent de lecture de file d’attente et la session spécifiée.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgentSessions%2A> -retourne un <xref:System.Data.DataSet> objet qui contient les informations de session de l’Agent de lecture de file d’attente spécifié.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumSnapshotAgents%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations sur tous les Agents de capture instantanée sur le distributeur.  
  
#### Pour analyser les propriétés de publication d'un serveur de publication spécifique d'un serveur de distribution  
  
1.  Créer une connexion au serveur de distribution à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Obtenir un <xref:Microsoft.SqlServer.Replication.PublisherMonitor> objet dans une des manières suivantes.  
  
    -   Créez une instance de la <xref:Microsoft.SqlServer.Replication.PublisherMonitor> (classe). Définir le <xref:Microsoft.SqlServer.Replication.PublisherMonitor.Name%2A> propriété pour le serveur de publication et définissez la <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> créé à l’étape 1. Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet. Si cette méthode retourne **false**, soit le nom du serveur de publication a été défini de manière incorrecte, soit la publication n’existe pas.  
  
    -   À partir de la <xref:Microsoft.SqlServer.Replication.PublisherMonitorCollection> accessible au moyen de la <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.PublisherMonitors%2A> Propriétés d’un <xref:Microsoft.SqlServer.Replication.ReplicationMonitor> objet.  
  
3.  Exécutez une ou plusieurs des méthodes suivantes pour retourner les informations de réplication de toutes les publications qui appartiennent à ce serveur de publication.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumDistributionAgentSessionDetails%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des détails sur l’Agent de Distribution et la session spécifiée.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumDistributionAgentSessions%2A> -retourne un <xref:System.Data.DataSet> objet qui contient les informations de session de l’Agent de Distribution spécifié.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumErrorRecords%2A> -retourne un <xref:System.Data.DataSet> objet qui contient l’erreur consigner des informations sur l’erreur spécifiée.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumLogReaderAgentSessionDetails%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des détails sur l’Agent de lecture du journal et la session spécifiée.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumLogReaderAgentSessions%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations de session pour l’Agent de lecture du journal spécifié.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessionDetails%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des détails sur l’Agent de fusion et la session spécifiée.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessionDetails2%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des détails supplémentaires sur l’Agent de fusion et la session spécifiée.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessions%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations de session pour l’Agent de fusion spécifiée.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessions2%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations de session supplémentaires pour l’Agent de fusion spécifiée.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumPublications%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations sur toutes les publications sur ce serveur de distribution.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumPublications2%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations supplémentaires sur toutes les publications sur ce serveur de distribution.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSnapshotAgentSessionDetails%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des détails sur l’Agent de capture instantanée et la session spécifiée.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSnapshotAgentSessions%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations de session de l’Agent de capture instantanée spécifié.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSubscriptions%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations sur tous les abonnements aux publications sur ce serveur de distribution.  
  
#### Pour analyser les propriétés d'une publication spécifique du serveur de distribution  
  
1.  Créer une connexion au serveur de distribution à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Obtenir un <xref:Microsoft.SqlServer.Replication.PublicationMonitor> objet dans une des manières suivantes.  
  
    -   Créez une instance de la <xref:Microsoft.SqlServer.Replication.PublicationMonitor> (classe). Définir le <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>, et <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> Propriétés de la publication et définissez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété du <xref:Microsoft.SqlServer.Management.Common.ServerConnection> créé à l’étape 1. Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet. Si cette méthode retourne **false**, soit les propriétés de la publication ont été définies de manière incorrecte, soit la publication n’existe pas.  
  
    -   À partir de la <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> accessible au moyen de la <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> Propriétés d’un <xref:Microsoft.SqlServer.Replication.PublisherMonitor> objet.  
  
3.  Exécutez une ou plusieurs des méthodes suivantes pour retourner des informations sur cette publication.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumErrorRecords%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des enregistrements d’erreur sur l’erreur spécifiée.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumLogReaderAgent%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations sur l’Agent de lecture du journal pour cette publication.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumMonitorThresholds%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations sur les seuils d’avertissement analyse défini pour cette publication.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumQueueReaderAgent%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations sur l’Agent de lecture de file d’attente utilisée par cette publication.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumSnapshotAgent%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations sur l’Agent de capture instantanée pour cette publication.  
  
    -   <xref:Microsoft.SqlServer.Replication.Publication.EnumSubscriptions%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations sur les abonnements à cette publication.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumSubscriptions2%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations supplémentaires sur les abonnements à cette publication selon fourni <xref:Microsoft.SqlServer.Replication.SubscriptionResultOption>.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations de latence pour le jeton de suivi spécifié.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> -retourne un <xref:System.Data.DataSet> objet qui contient des informations sur tous les jetons de suivi insérés dans cette publication.  
  
#### Pour analyser les commandes transactionnelles en attente d'application sur l'Abonné  
  
1.  Créer une connexion au serveur de distribution à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Obtenir un <xref:Microsoft.SqlServer.Replication.PublicationMonitor> objet dans une des manières suivantes.  
  
    -   Créez une instance de la <xref:Microsoft.SqlServer.Replication.PublicationMonitor> (classe). Définir le <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>, et <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> Propriétés de la publication et définissez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété du <xref:Microsoft.SqlServer.Management.Common.ServerConnection> créé à l’étape 1. Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet. Si cette méthode retourne **false**, soit les propriétés de la publication ont été définies de manière incorrecte, soit la publication n’existe pas.  
  
    -   À partir de la <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> accessible au moyen de la <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> Propriétés d’un <xref:Microsoft.SqlServer.Replication.PublisherMonitor> objet.  
  
3.  Exécuter la <xref:Microsoft.SqlServer.Replication.PublicationMonitor.TransPendingCommandInfo%2A> méthode qui retourne un <xref:Microsoft.SqlServer.Replication.PendingCommandInfo> objet.  
  
4.  Utilisez les propriétés de ce <xref:Microsoft.SqlServer.Replication.PendingCommandInfo> objet afin de déterminer le nombre estimé de commandes en attente et la durée nécessaire à la livraison de ces commandes.  
  
#### Pour définir les seuils d'avertissement du moniteur pour une publication  
  
1.  Créer une connexion au serveur de distribution à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Obtenir un <xref:Microsoft.SqlServer.Replication.PublicationMonitor> objet dans une des manières suivantes.  
  
    -   Créez une instance de la <xref:Microsoft.SqlServer.Replication.PublicationMonitor> (classe). Définir le <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>, et <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> Propriétés de la publication et définissez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété du <xref:Microsoft.SqlServer.Management.Common.ServerConnection> créé à l’étape 1. Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet. Si cette méthode retourne **false**, soit les propriétés de la publication ont été définies de manière incorrecte, soit la publication n’existe pas.  
  
    -   À partir de la <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> accessible au moyen de la <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> Propriétés d’un <xref:Microsoft.SqlServer.Replication.PublisherMonitor> objet.  
  
3.  Exécuter la <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumMonitorThresholds%2A> (méthode). Notez les paramètres de seuil actuel dans le code <xref:System.Collections.ArrayList> de <xref:Microsoft.SqlServer.Replication.MonitorThreshold> objets.  
  
4.  Exécuter la <xref:Microsoft.SqlServer.Replication.PublicationMonitor.ChangeMonitorThreshold%2A> (méthode). Transmettez les paramètres suivants :  
  
    -   *metricID* : <xref:System.Int32> valeur qui représente le seuil d’analyse métrique de la table suivante :  
  
        |Valeur|Description|  
        |-----------|-----------------|  
        |1|**expiration** -moniteurs d’expiration imminente des abonnements aux publications transactionnelles.|  
        |2|**latence** -contrôle les performances des abonnements aux publications transactionnelles.|  
        |4|**mergeexpiration** -contrôle l’expiration imminente des abonnements aux publications de fusion.|  
        |5|**mergeslowrunduration** -contrôle la durée des synchronisations de fusion sur les connexions lentes (accès à distance).|  
        |6|**mergefastrunduration** -contrôle la durée des synchronisations de fusion sur une connexion haut débit (LAN).|  
        |7|**mergefastrunspeed** -contrôle la vitesse de synchronisation des synchronisations de fusion sur une connexion haut débit (LAN).|  
        |8|**mergeslowrunspeed** -contrôle la vitesse de synchronisation de fusion sur les connexions lentes (accès à distance).|  
  
    -   *activer* - <xref:System.Boolean> valeur qui indique si la mesure est activée pour la publication.  
  
    -   *thresholdValue* -valeur entière qui définit le seuil.  
  
    -   *shouldAlert* -entier qui indique si ce seuil doit générer une alerte.  
  
  