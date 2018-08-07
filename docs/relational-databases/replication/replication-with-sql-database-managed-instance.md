---
title: Réplication avec SQL Database Managed Instance | Microsoft Docs
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Database replication
- replication, SQL Database
ms.assetid: e8484da7-495f-4dac-b38e-bcdc4691f9fa
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: d55aea5d50d9ea434aabb392d0c6b53573c0199e
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39559569"
---
# <a name="replication-with-sql-database-managed-instance"></a>Réplication avec SQL Database Managed Instance

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

Azure SQL Database Managed Instance (préversion) prend en charge la réplication transactionnelle. Managed Instance peut héberger les bases de données du serveur de publication, du serveur de distribution et de l'abonné.

## <a name="common-configurations"></a>Configurations courantes

En règle générale, le serveur de publication et le serveur de distribution doivent être dans le cloud ou bien locaux. Les configurations prises en charge sont les suivantes :

- **Serveur de publication avec serveur de distribution local sur l’instance managée**

   ![Replication-with-azure-sql-db-single-managed-instance-publisher-distributor](./media/replication-with-sql-database-managed-instance/01-single-instance-asdbmi-pubdist.png)

   Les bases de données du serveur de publication et du serveur de distribution sont configurées sur une même instance gérée.

- **Serveur de publication avec serveur de distribution distant sur l’instance managée**

   ![Replication-with-azure-sql-db-separate-managed-instances-publisher-distributor](./media/replication-with-sql-database-managed-instance/02-separate-instances-asdbmi-pubdist.png)

   Le serveur de publication et le serveur de distribution sont configurés sur deux instances gérées. Dans cette configuration :

  - Les deux instances gérées se trouvent dans le même réseau virtuel.

  - Les deux instances gérées se trouvent au même endroit.

- **Serveur de publication et serveur de distribution locaux avec abonné sur l’instance managée**

   ![Replication-from-on-premises-to-azure-sql-db-subscriber](./media/replication-with-sql-database-managed-instance/03-azure-sql-db-subscriber.png)

   Dans cette configuration, Azure SQL Database est un abonné. Cette configuration prend en charge la migration du système local vers Azure. Dans le rôle de l’abonné, SQL Database n’a pas besoin d’instance gérée ; il reste possible d’en utiliser une dans le cadre de la migration du système local vers Azure. Pour plus d’informations sur les abonnés Azure SQL Database, voir [Réplication sur SQL Database](replication-to-sql-database.md).

## <a name="requirements"></a>Spécifications

Le serveur de publication et le serveur de distribution sur Azure SQL Database exigent les éléments suivants :

- Azure SQL Database Managed Instance.

   >[!NOTE]
   >Les bases de données Azure SQL Database qui ne sont pas configurées avec Managed Instance ne peuvent être que des abonnés.

- Toutes les instances de SQL Server doivent se trouver sur le même réseau virtuel.

- La connectivité utilise l’authentification SQL entre les participants à la réplication.

- Un partage de compte de Stockage Azure pour le répertoire de travail de la réplication.

## <a name="features"></a>Fonctionnalités

Prend en charge :

- Une combinaison entre la réplication transactionnelle et la réplication de capture instantanée d’instances Azure SQL Database Managed Instance et locales.

- Les abonnés peuvent être sur site, dans Azure SQL Database ou dans des pools élastiques.

- Réplication unidirectionnelle ou bidirectionnelle

## <a name="configure-publishing-and-distribution-example"></a>Exemple de configuration de la publication et de la distribution

1. [Créez une instance Azure SQL Database Managed Instance](http://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-create-tutorial-portal) sur le portail.

1. [Créez un compte de stockage Azure](http://docs.microsoft.com/azure/storage/common/storage-create-storage-account#create-a-storage-account) pour le répertoire de travail. Veillez à copier les clés de stockage. Voir [Afficher et copier les clés d’accès de stockage](http://docs.microsoft.com/azure/storage/common/storage-create-storage-account#manage-your-storage-access-keys).

1. Créez une base de données pour le serveur de publication.

   Dans les exemples de scripts ci-dessous, remplacez `<Publishing_DB>` par le nom de cette base de données.

1. Créez un utilisateur de base de données avec l’authentification SQL pour le serveur de distribution. Voir [Créer des utilisateurs de base de données](http://docs.microsoft.com/azure/sql-database/sql-database-security-tutorial#creating-database-users). Utilisez un mot de passe sécurisé.

   Dans les exemples de scripts ci-dessous, utilisez `<SQL_USER>` et `<PASSWORD>` avec cet utilisateur de base de données de compte SQL Server et ce mot de passe.

1. [Connectez-vous à Azure SQL Database Managed Instance](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-ssms).

1. Exécutez la requête suivante pour ajouter le serveur de distribution et la base de données de distribution.

   ```sql
   USE [master]
   GO
   EXEC sp_adddistributor @distributor = @@ServerName;
   EXEC sp_adddistributiondb @database = N'distribution';
   ```

1. Pour configurer un serveur de publication de façon à ce qu’il utilise une base de données de distribution spécifiée, modifiez et exécutez la requête suivante.

   Remplacez `<SQL_USER>` et `<PASSWORD>` par le compte SQL Server et le mot de passe.

   Remplacez `\\<STORAGE_ACCOUNT>.file.core.windows.net\<SHARE>` par la valeur de votre compte de stockage. 

   Remplacez `<STORAGE_CONNECTION_STRING>` par la valeur de vos clés d’accès.

   Dès que vous avez modifié la requête suivante, exécutez-la. 

   ```sql
   USE [master]
   EXEC sp_adddistpublisher @publisher = @@ServerName,
                @distribution_db = N'distribution',
                @security_mode = 0,
                @login = N'<SQL_USER>',
                @password = N'<PASSWORD>',
                @working_directory = N'\\<STORAGE_ACCOUNT>.file.core.windows.net\<SHARE>',
                @storage_connection_string = N'<STORAGE_CONNECTION_STRING>';
   GO
   ```

1. Configurez le serveur de publication pour la réplication. 

    Dans la requête suivante, remplacez `<Publishing_DB>` par le nom de votre base de données du serveur de publication.

    Remplacez `<Publication_Name>` par le nom de votre publication.

    Remplacez `<SQL_USER>` et `<PASSWORD>` par le compte SQL Server et le mot de passe.

    Dès que vous avez modifié la requête, exécutez-la pour créer la publication.

   ```sql
   USE [<Publishing_DB>]
   EXEC sp_replicationdboption @dbname = N'<Publishing_DB>',
                @optname = N'publish',
                @value = N'true';

   EXEC sp_addpublication @publication = N'<Publication_Name>',
                @status = N'active';

   EXEC sp_changelogreader_agent @publisher_security_mode = 0,
                @publisher_login = N'<SQL_USER>',
                @publisher_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>',
                @job_password = N'<PASSWORD>';

   EXEC sp_addpublication_snapshot @publication = N'<Publication_Name>',
                @frequency_type = 1,
                @publisher_security_mode = 0,
                @publisher_login = N'<SQL_USER>',
                @publisher_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>',
                @job_password = N'<PASSWORD>'
   ```

1. Ajoutez l’article, l’abonnement et l’agent d’abonnement par émission de données. 

   Pour ajouter ces objets, modifiez le script suivant.

   Remplacez `<Object_Name>` par le nom de l'objet de publication.

   Remplacez `<Object_Schema>` par le nom du schéma source. 

   Remplacez les autres paramètres entre crochets angulaires `<>` par les valeurs des scripts précédents. 

   ```sql
   EXEC sp_addarticle @publication = N'<Publication_Name>',
                @type = N'logbased',
                @article = N'<Object_Name>',
                @source_object = N'<Object_Name>',
                @source_owner = N'<Object_Schema>'

   EXEC sp_addsubscription @publication = N'<Publication_Name>',
                @subscriber = @@ServerName,
                @destination_db = N'<Subscribing_DB>',
                @subscription_type = N'Push'

   EXEC sp_addpushsubscription_agent @publication = N'<Publication_Name>',
                @subscriber = @@ServerName,
                @subscriber_db = N'<Subscribing_DB>',
                @subscriber_security_mode = 0,
                @subscriber_login = N'<SQL_USER>',
                @subscriber_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>', 
                @job_password = N'<PASSWORD>'
   GO
   ```

## <a name="limitations"></a>Limitations

Les fonctionnalités suivantes ne sont pas prises en charge :

- Abonnements actualisables

- Géoréplication active

## <a name="see-also"></a> Voir aussi

- [Présentation des instances gérées (préversion)](http://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)
