---
title: Mappage SQL-DMO vers SMO | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 590f5396-98d5-485e-9b41-728c6ed7cb9d
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d99a665366fc9b5df9ff975d47cfa60dccaf4b4e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038880"
---
# <a name="sql-dmo-mapping-to-smo"></a>Mappage SQL-DMO vers SMO
  SQL-DMO (SQL Distributed Management Objects) n'est plus inclus dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ; les applications SQL-DMO doivent être converties afin d'utiliser SMO ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects). Le modèle d'objet SMO est similaire à SQL-DMO, aussi la plupart des objets SQL-DMO sont mappés à un objet de même nom dans SMO. Toutefois, certains objets SQL-DMO ont été modifiés ou supprimés lors de la transition vers SMO. Ce tableau indique les actions recommandées pour les objets SQL-DMO non convertis directement en SMO.  
  
|Objet SQL-DMO|Action dans SMO|  
|---------------------|-------------------|  
|Objet View2|Déplacé vers l'espace de noms <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Objet AlertSystem|Déplacé vers l'espace de noms <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Objet Application|Supprimé.|  
|Objets Backup et Backup2|Objets <xref:Microsoft.SqlServer.Management.Smo.Backup> et <xref:Microsoft.SqlServer.Management.Smo.BackupRestoreBase>.|  
|Objet BackupDevice|<xref:Microsoft.SqlServer.Management.Smo.BackupDevice> Objets|  
|Objets BulkCopy et BulkCopy2|Supprimés et remplacés par l'objet <xref:Microsoft.SqlServer.Management.Smo.Transfer>.|  
|Objet Category|Déplacé vers l'espace de noms <xref:Microsoft.SqlServer.Management.Smo.Agent>. Remplacé par les objets <xref:Microsoft.SqlServer.Management.Smo.Agent.AlertCategory>, <xref:Microsoft.SqlServer.Management.Smo.Agent.OperatorCategory>, <xref:Microsoft.SqlServer.Management.Smo.Agent.JobCategory>.|  
|Objet Check|<xref:Microsoft.SqlServer.Management.Smo.Check> objet|  
|Objets Column et Column2|<xref:Microsoft.SqlServer.Management.Smo.Column> objet.|  
|Objet Configuration|Objets <xref:Microsoft.SqlServer.Management.Smo.Configuration> et <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase>.|  
|Objet ConfigValue|<xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> objet.|  
|Objets Database et Database2|<xref:Microsoft.SqlServer.Management.Smo.Database> objet.|  
|Objets DatabaseRole et DatabaseRole2|<xref:Microsoft.SqlServer.Management.Smo.DatabaseRole> objet.|  
|Objet DBFile|<xref:Microsoft.SqlServer.Management.Smo.DataFile> objet.|  
|Objets DBOption et DBOption2|Déplacés vers l'objet <xref:Microsoft.SqlServer.Management.Smo.DatabaseOptions>.|  
|Objets Default et Default2|<xref:Microsoft.SqlServer.Management.Smo.Default> objet.|  
|Objets DistributionArticle et DistributionArticle2|Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objets DistributionDatabase et DistributionDatabase2|Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objets DistributionPublication et DistributionPublication2|Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objets DistributionSubscription et DistributionSubscription2|Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objets Distributor et Distributor2|Déplacés vers l'espace de noms <xref:Microsoft.SqlServer.Replication>.|  
|Objet DRIDefault|Déplacé vers l'objet <xref:Microsoft.SqlServer.Management.Smo.ScriptingOptions>.|  
|Objets FileGroup et FileGroup2|<xref:Microsoft.SqlServer.Management.Smo.FileGroup> objet.|  
|Objets FullTextCatalog et FullTextCatalog2|Objets <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> et <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex>.|  
|Objets Index et Index2|<xref:Microsoft.SqlServer.Management.Smo.Index> objet|  
|Objet IntegratedSecurity|Fonctionnalité déplacée vers l'objet <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dans l'espace de noms <xref:Microsoft.SqlServer.Management.Common>.|  
|Objet Job|<xref:Microsoft.SqlServer.Management.Smo.Agent.Job> objet. Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> espace de noms.|  
|Objet JobFilter|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobFilter> objet. Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> espace de noms.|  
|Objet JobHistoryFilter|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobHistoryFilter> objet. Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> espace de noms.|  
|Objet JobSchedule|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobSchedule> objet. Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> espace de noms.|  
|Objets JobServer et JobServer2|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobServer> objet. Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> espace de noms.|  
|Objet JobStep|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobStep> objet. Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> espace de noms.|  
|Objet Key|Objets <xref:Microsoft.SqlServer.Management.Smo.ForeignKey> et <xref:Microsoft.SqlServer.Management.Smo.Index>.|  
|Objets LinkedServer et LinkedServer2|<xref:Microsoft.SqlServer.Management.Smo.LinkedServer> objet.|  
|Objet LinkedServerLogin|<xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin> objet.|  
|Objet LogFile|<xref:Microsoft.SqlServer.Management.Smo.LogFile> objet.|  
|Objets Login et Login2|<xref:Microsoft.SqlServer.Management.Smo.Login> objet.|  
|Objets MergeArticle et MergeArticle2|<xref:Microsoft.SqlServer.Replication.MergeArticle> objet. Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objet MergeDynamicSnapshotJob|Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objets MergePublication et MergePublication2|<xref:Microsoft.SqlServer.Replication.MergePublication> objet. Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objets MergePullSubscription et MergePullSubscription2|<xref:Microsoft.SqlServer.Replication.MergePullSubscription> objet. Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objet MergeSubscription|<xref:Microsoft.SqlServer.Replication.MergeSubscription> objet. Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objet MergeSubsetFilter|Déplacé vers `N:Microsoft.SqlServer.Replication` espace de noms.|  
|Objet NameList|Supprimé. Fonctionnalités autres dans l'objet <xref:Microsoft.SqlServer.Management.Smo.Scripter>.|  
|Objet Operator|Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> espace de noms.|  
|Objets Permission et Permission2|Objets <xref:Microsoft.SqlServer.Management.Smo.ServerPermission>, <xref:Microsoft.SqlServer.Management.Smo.DatabasePermission>, <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole> et <xref:Microsoft.SqlServer.Management.Smo.ObjectPermission>.|  
|Objet Property|`Property` objet.|  
|Objets Publisher et Publisher2|<xref:Microsoft.SqlServer.Replication.ReplicationServer> objet. Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objets QueryResults et QueryResults2|Remplacés par l'objet système <xref:System.Data.DataTable> ou <xref:System.Data.DataSet>.|  
|Objet RegisteredServer|Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objet RegisteredSubscriber|Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objets Registry et Registry2|Supprimé.|  
|Objet RemoteLogin|<xref:Microsoft.SqlServer.Management.Common.ServerConnection> objet. Déplacé vers l'espace de noms Common.|  
|Objets RemoteServer et RemoteServer2|<xref:Microsoft.SqlServer.Management.Common.ServerConnection> objet. Déplacé vers <xref:Microsoft.SqlServer.Management.Common> espace de noms.|  
|Objet Replication|Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objets ReplicationDatabase et ReplicationDatabase2|<xref:Microsoft.SqlServer.Replication.ReplicationDatabase> objet. Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objet ReplicationSecurity|<xref:Microsoft.SqlServer.Management.Common.ServerConnection> objet. Déplacé vers <xref:Microsoft.SqlServer.Management.Common> espace de noms.|  
|Objets ReplicationStoredProcedure et ReplicationStoredProcedure2|<xref:Microsoft.SqlServer.Replication.ReplicationStoredProcedure> objet. Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objets ReplicationTable et ReplicationTable2|<xref:Microsoft.SqlServer.Replication.ReplicationTable> objet. Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objets Restore et Restore2|Objets <xref:Microsoft.SqlServer.Management.Smo.Restore> et <xref:Microsoft.SqlServer.Management.Smo.BackupRestoreBase>.|  
|Objets Rule et Rule2|<xref:Microsoft.SqlServer.Management.Smo.Rule> objet|  
|Objet Schedule|Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objet ServerGroup|Supprimé.|  
|Objet ServerRole|<xref:Microsoft.SqlServer.Management.Smo.ServerRole> objet.|  
|Objet SQLObjectList|<xref:Microsoft.SqlServer.Management.Smo.SqlSmoObject> tableau.|  
|Objets SQLServer et SQLServer2|<xref:Microsoft.SqlServer.Management.Smo.Server> objet.|  
|Objets StoredProcedure et StoredProcedure2|<xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> et <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> objets|  
|Objets Subscriber et Subscriber2|Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objets SystemDatatype et SystemDataType2|<xref:Microsoft.SqlServer.Management.Smo.DataType> objet.|  
|Objets Table et Table2|<xref:Microsoft.SqlServer.Management.Smo.Table> objet.|  
|Objet TargetServer|Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> espace de noms.|  
|Objet TargetServerGroup|Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> espace de noms.|  
|Objet TransactionLog|Fonctionnalité déplacée vers l'objet <xref:Microsoft.SqlServer.Management.Smo.Database>.|  
|Objets TransArticle et TransArticle2|<xref:Microsoft.SqlServer.Replication.TransArticle> objet. Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Méthode Transfer et Objet Transfer2|<xref:Microsoft.SqlServer.Management.Smo.Transfer> objet.|  
|Objets TransPublication et TransPublication2|<xref:Microsoft.SqlServer.Replication.TransPublication> objet. Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objets TransPullSubscription et TransPullSubscription2|<xref:Microsoft.SqlServer.Replication.TransPullSubscription> objet. Déplacé vers <xref:Microsoft.SqlServer.Replication> espace de noms.|  
|Objets Trigger et Trigger2|<xref:Microsoft.SqlServer.Management.Smo.Trigger> objet.|  
|Objets User et User2|<xref:Microsoft.SqlServer.Management.Smo.User> objet.|  
|Objets UserDefinedDatatype et UserDefinedDataType2|<xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> objet.|  
|Objet UserDefinedFunction|Objets <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> et <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>.|  
|Objets View et View2|<xref:Microsoft.SqlServer.Management.Smo.View> objet.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation SQL Server Management Objects &#40;SMO&#41;](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  