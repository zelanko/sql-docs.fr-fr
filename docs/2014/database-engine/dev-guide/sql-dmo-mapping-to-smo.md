---
title: Mappage SQL-DMO à SMO | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: 590f5396-98d5-485e-9b41-728c6ed7cb9d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2a6273032f88807291bfc7024f1abcdbd1440073
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62780679"
---
# <a name="sql-dmo-mapping-to-smo"></a>Mappage SQL-DMO vers SMO
  SQL-DMO (SQL Distributed Management Objects) n'est plus inclus dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ; les applications SQL-DMO doivent être converties afin d'utiliser SMO ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects). Le modèle d'objet SMO est similaire à SQL-DMO, aussi la plupart des objets SQL-DMO sont mappés à un objet de même nom dans SMO. Toutefois, certains objets SQL-DMO ont été modifiés ou supprimés lors de la transition vers SMO. Ce tableau indique les actions recommandées pour les objets SQL-DMO non convertis directement en SMO.  
  
|Objet SQL-DMO|Action dans SMO|  
|---------------------|-------------------|  
|Objet View2|Déplacé vers l'espace de noms <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Objet AlertSystem|Déplacé vers l'espace de noms <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Objet Application|Supprimé.|  
|Objets Backup et Backup2|Objets <xref:Microsoft.SqlServer.Management.Smo.Backup> et <xref:Microsoft.SqlServer.Management.Smo.BackupRestoreBase>.|  
|Objet BackupDevice|Objets <xref:Microsoft.SqlServer.Management.Smo.BackupDevice>.|  
|Objets BulkCopy et BulkCopy2|Supprimés et remplacés par l'objet <xref:Microsoft.SqlServer.Management.Smo.Transfer>.|  
|Objet Category|Déplacé vers l'espace de noms <xref:Microsoft.SqlServer.Management.Smo.Agent>. Remplacé par les objets <xref:Microsoft.SqlServer.Management.Smo.Agent.AlertCategory>, <xref:Microsoft.SqlServer.Management.Smo.Agent.OperatorCategory>, <xref:Microsoft.SqlServer.Management.Smo.Agent.JobCategory>.|  
|Objet Check|l'objet <xref:Microsoft.SqlServer.Management.Smo.Check>|  
|Objets Column et Column2|Objet <xref:Microsoft.SqlServer.Management.Smo.Column>.|  
|Objet Configuration|Objets <xref:Microsoft.SqlServer.Management.Smo.Configuration> et <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase>.|  
|Objet ConfigValue|Objet <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty>.|  
|Objets Database et Database2|Objet <xref:Microsoft.SqlServer.Management.Smo.Database>.|  
|Objets DatabaseRole et DatabaseRole2|Objet <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole>.|  
|Objet DBFile|Objet <xref:Microsoft.SqlServer.Management.Smo.DataFile>.|  
|Objets DBOption et DBOption2|Déplacés vers l'objet <xref:Microsoft.SqlServer.Management.Smo.DatabaseOptions>.|  
|Objets Default et Default2|Objet <xref:Microsoft.SqlServer.Management.Smo.Default>.|  
|Objets DistributionArticle et DistributionArticle2|Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objets DistributionDatabase et DistributionDatabase2|Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objets DistributionPublication et DistributionPublication2|Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objets DistributionSubscription et DistributionSubscription2|Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objets Distributor et Distributor2|Déplacés vers l'espace de noms <xref:Microsoft.SqlServer.Replication>.|  
|Objet DRIDefault|Déplacé vers l'objet <xref:Microsoft.SqlServer.Management.Smo.ScriptingOptions>.|  
|Objets FileGroup et FileGroup2|Objet <xref:Microsoft.SqlServer.Management.Smo.FileGroup>.|  
|Objets FullTextCatalog et FullTextCatalog2|Objets <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> et <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex>.|  
|Objets Index et Index2|l'objet <xref:Microsoft.SqlServer.Management.Smo.Index>|  
|Objet IntegratedSecurity|Fonctionnalité déplacée vers l'objet <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dans l'espace de noms <xref:Microsoft.SqlServer.Management.Common>.|  
|Objet Job|Objet <xref:Microsoft.SqlServer.Management.Smo.Agent.Job>. Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> l’espace de noms.|  
|Objet JobFilter|Objet <xref:Microsoft.SqlServer.Management.Smo.Agent.JobFilter>. Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> l’espace de noms.|  
|Objet JobHistoryFilter|Objet <xref:Microsoft.SqlServer.Management.Smo.Agent.JobHistoryFilter>. Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> l’espace de noms.|  
|Objet JobSchedule|Objet <xref:Microsoft.SqlServer.Management.Smo.Agent.JobSchedule>. Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> l’espace de noms.|  
|Objets JobServer et JobServer2|Objet <xref:Microsoft.SqlServer.Management.Smo.Agent.JobServer>. Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> l’espace de noms.|  
|Objet JobStep|Objet <xref:Microsoft.SqlServer.Management.Smo.Agent.JobStep>. Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> l’espace de noms.|  
|Objet Key|Objets <xref:Microsoft.SqlServer.Management.Smo.ForeignKey> et <xref:Microsoft.SqlServer.Management.Smo.Index>.|  
|Objets LinkedServer et LinkedServer2|Objet <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>.|  
|Objet LinkedServerLogin|Objet <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin>.|  
|Objet LogFile|Objet <xref:Microsoft.SqlServer.Management.Smo.LogFile>.|  
|Objets Login et Login2|Objet <xref:Microsoft.SqlServer.Management.Smo.Login>.|  
|Objets MergeArticle et MergeArticle2|Objet <xref:Microsoft.SqlServer.Replication.MergeArticle>. Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objet MergeDynamicSnapshotJob|Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objets MergePublication et MergePublication2|Objet <xref:Microsoft.SqlServer.Replication.MergePublication>. Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objets MergePullSubscription et MergePullSubscription2|Objet <xref:Microsoft.SqlServer.Replication.MergePullSubscription>. Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objet MergeSubscription|Objet <xref:Microsoft.SqlServer.Replication.MergeSubscription>. Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objet MergeSubsetFilter|Déplacé vers `N:Microsoft.SqlServer.Replication` l’espace de noms.|  
|Objet NameList|Supprimé. Fonctionnalités autres dans l'objet <xref:Microsoft.SqlServer.Management.Smo.Scripter>.|  
|Objet Operator|Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> l’espace de noms.|  
|Objets Permission et Permission2|Objets <xref:Microsoft.SqlServer.Management.Smo.ServerPermission>, <xref:Microsoft.SqlServer.Management.Smo.DatabasePermission>, <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole> et <xref:Microsoft.SqlServer.Management.Smo.ObjectPermission>.|  
|Objet Property|Objet `Property`.|  
|Objets Publisher et Publisher2|Objet <xref:Microsoft.SqlServer.Replication.ReplicationServer>. Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objets QueryResults et QueryResults2|Remplacés par l'objet système <xref:System.Data.DataTable> ou <xref:System.Data.DataSet>.|  
|Objet RegisteredServer|Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objet RegisteredSubscriber|Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objets Registry et Registry2|Supprimé.|  
|Objet RemoteLogin|Objet <xref:Microsoft.SqlServer.Management.Common.ServerConnection>. Déplacé vers l'espace de noms Common.|  
|Objets RemoteServer et RemoteServer2|Objet <xref:Microsoft.SqlServer.Management.Common.ServerConnection>. Déplacé vers <xref:Microsoft.SqlServer.Management.Common> l’espace de noms.|  
|Objet Replication|Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objets ReplicationDatabase et ReplicationDatabase2|Objet <xref:Microsoft.SqlServer.Replication.ReplicationDatabase>. Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objet ReplicationSecurity|Objet <xref:Microsoft.SqlServer.Management.Common.ServerConnection>. Déplacé vers <xref:Microsoft.SqlServer.Management.Common> l’espace de noms.|  
|Objets ReplicationStoredProcedure et ReplicationStoredProcedure2|Objet <xref:Microsoft.SqlServer.Replication.ReplicationStoredProcedure>. Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objets ReplicationTable et ReplicationTable2|Objet <xref:Microsoft.SqlServer.Replication.ReplicationTable>. Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objets Restore et Restore2|Objets <xref:Microsoft.SqlServer.Management.Smo.Restore> et <xref:Microsoft.SqlServer.Management.Smo.BackupRestoreBase>.|  
|Objets Rule et Rule2|l'objet <xref:Microsoft.SqlServer.Management.Smo.Rule>|  
|Objet Schedule|Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objet ServerGroup|Supprimé.|  
|Objet ServerRole|Objet <xref:Microsoft.SqlServer.Management.Smo.ServerRole>.|  
|Objet SQLObjectList|Tableau<xref:Microsoft.SqlServer.Management.Smo.SqlSmoObject> .|  
|Objets SQLServer et SQLServer2|Objet <xref:Microsoft.SqlServer.Management.Smo.Server>.|  
|Objets StoredProcedure et StoredProcedure2|<xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>objets <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> et|  
|Objets Subscriber et Subscriber2|Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objets SystemDatatype et SystemDataType2|Objet <xref:Microsoft.SqlServer.Management.Smo.DataType>.|  
|Objets Table et Table2|Objet <xref:Microsoft.SqlServer.Management.Smo.Table>.|  
|Objet TargetServer|Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> l’espace de noms.|  
|Objet TargetServerGroup|Déplacé vers <xref:Microsoft.SqlServer.Management.Smo.Agent> l’espace de noms.|  
|Objet TransactionLog|Fonctionnalité déplacée vers l'objet <xref:Microsoft.SqlServer.Management.Smo.Database>.|  
|Objets TransArticle et TransArticle2|Objet <xref:Microsoft.SqlServer.Replication.TransArticle>. Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Méthode Transfer et Objet Transfer2|Objet <xref:Microsoft.SqlServer.Management.Smo.Transfer>.|  
|Objets TransPublication et TransPublication2|Objet <xref:Microsoft.SqlServer.Replication.TransPublication>. Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objets TransPullSubscription et TransPullSubscription2|Objet <xref:Microsoft.SqlServer.Replication.TransPullSubscription>. Déplacé vers <xref:Microsoft.SqlServer.Replication> l’espace de noms.|  
|Objets Trigger et Trigger2|Objet <xref:Microsoft.SqlServer.Management.Smo.Trigger>.|  
|Objets User et User2|Objet <xref:Microsoft.SqlServer.Management.Smo.User>.|  
|Objets UserDefinedDatatype et UserDefinedDataType2|Objet <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>.|  
|Objet UserDefinedFunction|Objets <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> et <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>.|  
|Objets View et View2|Objet <xref:Microsoft.SqlServer.Management.Smo.View>.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation SQL Server Management Objects &#40;SMO&#41;](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  
