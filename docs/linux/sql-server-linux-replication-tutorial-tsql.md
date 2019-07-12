---
title: Configurer la réplication de SQL Server sur Linux
description: Ce didacticiel montre comment configurer la réplication de capture instantanée de SQL Server sur Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
manager: jroth
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: cd0c2f2463abdc124f32d88fa9bd877c47a2fb76
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67834753"
---
# <a name="configure-replication-with-t-sql"></a>Configurer la réplication avec T-SQL

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)] 

Dans ce didacticiel, vous allez configurer la réplication d’instantané SQL Server sur Linux avec deux instances de SQL Server à l’aide de Transact-SQL. Le serveur de publication et le serveur de distribution sera la même instance, et l’abonné ne sera sur une instance distincte.

> [!div class="checklist"]
> * Activer les agents de réplication SQL Server sur Linux
> * Créer un exemple de base de données
> * Configurer le dossier d’instantanés pour l’accès des agents SQL Server
> * Configurer le serveur de distribution
> * Configurer le serveur de publication
> * Configurer la publication et les articles
> * Configurer l’abonné 
> * Exécuter les travaux de réplication

Toutes les configurations de réplication peuvent être configurées avec [procédures stockées de réplication](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

## <a name="prerequisites"></a>Prérequis  
Pour suivre ce didacticiel, vous devez :

- Deux instances de SQL Server avec la dernière version de SQL Server sur Linux
- Un outil pour émettre T-SQL des requêtes pour configurer la réplication telles que SQLCMD ou SSMS

  Consultez [utiliser SSMS pour gérer SQL Server sur Linux](./sql-server-linux-manage-ssms.md).

## <a name="detailed-steps"></a>Étapes détaillées

1. Activer les Agents de réplication SQL Server sur Linux activer l’Agent SQL Server à utiliser des Agents de réplication. Sur les deux ordinateurs hôtes, exécutez les commandes suivantes dans le terminal. 

  ```bash
  sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
  sudo systemctl restart mssql-server
  ```

1. Créer une base de données exemple et Table sur votre serveur de publication créer une base de données exemple et une table qui agira en tant que les articles pour une publication.

  ```sql
  CREATE DATABASE Sales
  GO
  USE [SALES]
  GO 
  CREATE TABLE CUSTOMER([CustomerID] [int] NOT NULL, [SalesAmount] [decimal] NOT NULL)
  GO 
  INSERT INTO CUSTOMER (CustomerID, SalesAmount) VALUES (1,100),(2,200),(3,300)
  ```

  Sur l’autre instance de SQL Server, l’abonné, créez la base de données pour recevoir les articles.

  ```sql
  CREATE DATABASE Sales
  GO
  ```

1. Créer le dossier d’instantanés pour les Agents SQL Server en lecture/écriture sur le serveur de distribution, créez le dossier d’instantanés et accorder l’accès à l’utilisateur « mssql » 

  ```bash
  sudo mkdir /var/opt/mssql/data/ReplData/
  sudo chown mssql /var/opt/mssql/data/ReplData/
  sudo chgrp mssql /var/opt/mssql/data/ReplData/
  ```

1. Configurer le serveur de distribution dans cet exemple, le serveur de publication est également le serveur de distribution. Exécutez les commandes suivantes sur le serveur de publication pour configurer l’instance pour la distribution également.

  ```sql
  DECLARE @distributor AS sysname
  DECLARE @distributorlogin AS sysname
  DECLARE @distributorpassword AS sysname
  -- Specify the distributor name. Use 'hostname' command on in terminal to find the hostname
  SET @distributor = N'<distributor instance name>'--in this example, it will be the name of the publisher
  SET @distributorlogin = N'<distributor login>'
  SET @distributorpassword = N'<distributor password>'
  -- Specify the distribution database. 
  
  use master
  exec sp_adddistributor @distributor = @distributor -- this should be the hostname

  -- Log into distributor and create Distribution Database. In this example, our publisher and distributor is on the same host
  exec sp_adddistributiondb @database = N'distribution', @log_file_size = 2, @deletebatchsize_xact = 5000, @deletebatchsize_cmd = 2000, @security_mode = 0, @login = @distributorlogin, @password = @distributorpassword
  GO

  DECLARE @snapshotdirectory AS nvarchar(500)
  SET @snapshotdirectory = N'/var/opt/mssql/data/ReplData/'

  -- Log into distributor and create Distribution Database. In this example, our publisher and distributor is on the same host
  use [distribution] 
  if (not exists (select * from sysobjects where name = 'UIProperties' and type = 'U ')) 
         create table UIProperties(id int) 
  if (exists (select * from ::fn_listextendedproperty('SnapshotFolder', 'user', 'dbo', 'table', 'UIProperties', null, null))) 
         EXEC sp_updateextendedproperty N'SnapshotFolder', @snapshotdirectory, 'user', dbo, 'table', 'UIProperties' 
  else 
         EXEC sp_addextendedproperty N'SnapshotFolder', @snapshotdirectory, 'user', dbo, 'table', 'UIProperties'
  GO
  ```

1. Configurer la publication, exécutez les commandes TSQL suivantes sur le serveur de publication.

  ```sql
  DECLARE @publisher AS sysname
  DECLARE @distributorlogin AS sysname
  DECLARE @distributorpassword AS sysname
  -- Specify the distributor name. Use 'hostname' command on in terminal to find the hostname
  SET @publisher = N'<instance name>' 
  SET @distributorlogin = N'<distributor login>'
  SET @distributorpassword = N'<distributor password>'
  -- Specify the distribution database. 

  -- Adding the distribution publishers
  exec sp_adddistpublisher @publisher = @publisher, 
  @distribution_db = N'distribution', 
  @security_mode = 0, 
  @login = @distributorlogin, 
  @password = @distributorpassword, 
  @working_directory = N'/var/opt/mssql/data/ReplData', 
  @trusted = N'false', 
  @thirdparty_flag = 0, 
  @publisher_type = N'MSSQLSERVER'
  GO
  ```

1. Configurer des commandes TSQL suivantes publication travail exécuté sur le serveur de publication.

  ```sql
  DECLARE @replicationdb AS sysname
  DECLARE @publisherlogin AS sysname
  DECLARE @publisherpassword AS sysname
  SET @replicationdb = N'Sales'
  SET @publisherlogin = N'<Publisher login>'
  SET @publisherpassword = N'<Publisher Password>'

  use [Sales]
  exec sp_replicationdboption @dbname = N'Sales', @optname = N'publish', @value = N'true'
  
  -- Add the snapshot publication
  exec sp_addpublication 
  @publication = N'SnapshotRepl', 
  @description = N'Snapshot publication of database ''Sales'' from Publisher ''<PUBLISHER HOSTNAME>''.',
  @retention = 0, 
  @allow_push = N'true', 
  @repl_freq = N'snapshot', 
  @status = N'active', 
  @independent_agent = N'true'

  exec sp_addpublication_snapshot @publication = N'SnapshotRepl', 
  @frequency_type = 1, 
  @frequency_interval = 1, 
  @frequency_relative_interval = 1, 
  @frequency_recurrence_factor = 0, 
  @frequency_subday = 8, 
  @frequency_subday_interval = 1, 
  @active_start_time_of_day = 0,
  @active_end_time_of_day = 235959, 
  @active_start_date = 0, 
  @active_end_date = 0, 
  @publisher_security_mode = 0, 
  @publisher_login = @publisherlogin, 
  @publisher_password = @publisherpassword
  ```

1. Créer des articles d’à partir de la table sales, exécutez les commandes TSQL suivantes sur le serveur de publication.

  ```sql
  use [Sales]
  exec sp_addarticle 
  @publication = N'SnapshotRepl', 
  @article = N'customer', 
  @source_owner = N'dbo', 
  @source_object = N'customer', 
  @type = N'logbased', 
  @description = null, 
  @creation_script = null, 
  @pre_creation_cmd = N'drop', 
  @schema_option = 0x000000000803509D,
  @identityrangemanagementoption = N'manual', 
  @destination_table = N'customer', 
  @destination_owner = N'dbo', 
  @vertical_partition = N'false'
  ```

1. Configurer un abonnement exécuter les commandes TSQL suivantes sur le serveur de publication.

  ```sql
  DECLARE @subscriber AS sysname
  DECLARE @subscriber_db AS sysname
  DECLARE @subscriberLogin AS sysname
  DECLARE @subscriberPassword AS sysname
  SET @subscriber = N'<Instance Name>' -- for example, MSSQLSERVER
  SET @subscriber_db = N'Sales'
  SET @subscriberLogin = N'<Subscriber Login>'
  SET @subscriberPassword = N'<Subscriber Password>'

  use [Sales]
  exec sp_addsubscription 
  @publication = N'SnapshotRepl', 
  @subscriber = @subscriber,
  @destination_db = @subscriber_db, 
  @subscription_type = N'Push', 
  @sync_type = N'automatic', 
  @article = N'all', 
  @update_mode = N'read only', 
  @subscriber_type = 0

  exec sp_addpushsubscription_agent 
  @publication = N'SnapshotRepl', 
  @subscriber = @subscriber,
  @subscriber_db = @subscriber_db, 
  @subscriber_security_mode = 0, 
  @subscriber_login =  @subscriberLogin,
  @subscriber_password =  @subscriberPassword,
  @frequency_type = 1,
  @frequency_interval = 0, 
  @frequency_relative_interval = 0, 
  @frequency_recurrence_factor = 0, 
  @frequency_subday = 0, 
  @frequency_subday_interval = 0, 
  @active_start_time_of_day = 0, 
  @active_end_time_of_day = 0, 
  @active_start_date = 0, 
  @active_end_date = 19950101
  GO
  ```

1. Exécuter des travaux de l’Agent de réplication

  Exécutez la requête suivante pour obtenir une liste des tâches :

  ```sql
  SELECT name, date_modified FROM msdb.dbo.sysjobs order by date_modified desc
  ```

  Exécutez le travail de réplication d’instantané pour générer l’instantané :

  ```sql
  USE msdb;  
  --generate snapshot of publications, for example
  EXEC dbo.sp_start_job N'PUBLISHER-PUBLICATION-SnapshotRepl-1'
  GO
  ```

  Exécutez le travail de réplication d’instantané pour générer l’instantané :

  ```sql
  USE msdb;  
  --distribute the publication to subscriber, for example
  EXEC dbo.sp_start_job N'DISTRIBUTOR-PUBLICATION-SnapshotRepl-SUBSCRIBER'
  GO
  ```

1. Se connecter abonné et interroger des données répliquées 

  Sur l’abonné, vérifiez que la réplication fonctionne en exécutant la requête suivante :

  ```sql
  SELECT * from [Sales].[dbo].[CUSTOMER]
  ```

Dans ce didacticiel, vous avez configuré la réplication d’instantané SQL Server sur Linux avec deux instances de SQL Server à l’aide de Transact-SQL.

> [!div class="checklist"]
> * Activer les agents de réplication SQL Server sur Linux
> * Créer un exemple de base de données
> * Configurer le dossier d’instantanés pour l’accès des agents SQL Server
> * Configurer le serveur de distribution
> * Configurer le serveur de publication
> * Configurer la publication et les articles
> * Configurer l’abonné 
> * Exécuter les travaux de réplication

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur la réplication, consultez [documentation de réplication SQL Server](../relational-databases/replication/sql-server-replication.md).

## <a name="next-steps"></a>Étapes suivantes

[Concepts : Réplication SQL Server sur Linux](sql-server-linux-replication.md)

[Procédures stockées de réplication](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).
