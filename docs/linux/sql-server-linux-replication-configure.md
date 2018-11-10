---
title: Configurer la réplication SQL Server sur Linux | Microsoft Docs
description: Cet article décrit comment configurer la réplication SQL Server sur Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/20/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
ms.workload: On Demand
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 71ad9b87f701a1f1de4f13a7788bba13543056e8
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51030016"
---
# <a name="configure-sql-server-replication-on-linux"></a>Configurer la réplication SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] introduit la réplication SQL Server pour les instances de SQL Server sur Linux.

Pour plus d’informations sur la réplication, consultez [documentation de réplication SQL Server](../relational-databases/replication/sql-server-replication.md).

Configurer la réplication sur Linux avec SQL Server Management Studio (SSMS) ou des procédures stockées Transact-SQL.

* Pour utiliser SSMS, suivez les instructions de cet article.

  Utiliser SSMS sur un système d’exploitation de Windows pour se connecter aux instances de SQL Server. Pour l’arrière-plan et des instructions, consultez [utiliser SSMS pour gérer SQL Server sur Linux](./sql-server-linux-manage-ssms.md).
  
* Pour obtenir un exemple avec des procédures stockées, suivez le [réplication configurer SQL Server sur Linux](sql-server-linux-replication-tutorial-tsql.md) didacticiel.

## <a name="prerequisites"></a>Prérequis

Avant de configurer des éditeurs, distributeurs et abonnés, vous devez effectuer quelques étapes de configuration pour l’instance de SQL Server.

1. Activer l’Agent SQL Server à utiliser des agents de réplication. Sur tous les serveurs Linux, exécutez les commandes suivantes dans le terminal.

  ```bash
  sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
  sudo systemctl restart mssql-server
  ```

1. Configurez l’instance de SQL Server pour la réplication. Pour configurer l’instance de SQL Server pour la réplication, exécutez `sys.sp_MSrepl_createdatatypemappings` sur toutes les instances participant à la réplication.

  ```sql
  USE msdb
  GO
  exec sys.sp_MSrepl_createdatatypemappings;
  GO
  ```

1. Créer un dossier d’instantanés. Les agents SQL Server nécessitent un dossier d’instantanés en lecture/écriture à. Créer le dossier d’instantanés sur le serveur de distribution.

  Pour créer le dossier d’instantanés et accorder l’accès à `mssql` utilisateur, exécutez la commande suivante :

  ```bash
  sudo mkdir /var/opt/mssql/data/ReplData/
  sudo chown mssql /var/opt/mssql/data/ReplData/
  sudo chgrp mssql /var/opt/mssql/data/ReplData/
  ```

## <a name="configure-and-monitor-replication-with-sql-server-management-studio-ssms"></a>Configurer et surveiller la réplication SQL Server Management Studio (SSMS)

### <a name="configure-the-distributor"></a>Configurer le serveur de distribution
  
Pour configurer le serveur de distribution : 

1. Dans SSMS, connectez-vous à votre instance de SQL Server dans l’Explorateur d’objets.

1. Avec le bouton droit **réplication**, puis cliquez sur **configurer la Distribution...** .

1. Suivez les instructions la **Assistant Configuration de Distribution**.

### <a name="create-publication-and-articles"></a>Créer des publications et articles

Pour créer une publication et les articles :

1. Dans l’Explorateur d’objets, cliquez sur **réplication** > **Publications locales**> **nouvelle Publication...** .

1. Suivez les instructions la **Assistant Nouvelle Publication** pour configurer le type de réplication et les articles qui appartiennent à la publication.

### <a name="configure-the-subscription"></a>Configurer l’abonnement

Pour configurer l’abonnement dans l’Explorateur d’objets, cliquez sur **réplication** > **abonnements locaux**> **nouveaux abonnements...** .

### <a name="monitor-replication-jobs"></a>Surveiller les travaux de réplication

Moniteur de réplication permet de surveiller les travaux de réplication.

Dans l’Explorateur d’objets, cliquez sur **réplication**, puis cliquez sur **lancer le moniteur de réplication**.

## <a name="next-steps"></a>Étapes suivantes

[Concepts : Réplication de SQL Server sur Linux](sql-server-linux-replication.md)

[Procédures stockées de réplication](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).
