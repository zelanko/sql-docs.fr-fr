---
title: Configurer la réplication (SSMS)
description: Cet article décrit comment configurer la réplication SQL Server sur Linux.
ms.custom: seo-dt-2019
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 03/20/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.technology: linux
titleSuffix: SQL Server on Linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 0979f05808c59336dec7a6e4a664b2e970029dd6
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "75952497"
---
# <a name="configure-sql-server-replication-on-linux"></a>Configurer la réplication SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] introduit la réplication SQL Server pour les instances SQL Server sur Linux.

Pour plus d’informations sur la réplication, consultez la [documentation sur la réplication SQL Server](../relational-databases/replication/sql-server-replication.md).

Configurez la réplication sur Linux avec SQL Server Management Studio (SSMS) ou les procédures stockées Transact-SQL.

* Pour utiliser le SSMS, suivez les instructions de cet article.

  Utilisez SSMS sur un système d'exploitation Windows pour vous connecter aux instances SQL Server. Pour obtenir plus de contexte et des instructions, voir [Utiliser SSMS pour gérer SQL Server sur Linux](./sql-server-linux-manage-ssms.md).
  
* Pour un exemple avec des procédures stockées, suivez le tutoriel [Configurer la réplication SQL Server sur Linux](sql-server-linux-replication-tutorial-tsql.md).

## <a name="prerequisites"></a>Prérequis

Avant de configurer des éditeurs, distributeurs et abonnés, vous devez effectuer quelques étapes de configuration pour l'instance SQL Server.

1. Activez SQL Server Agent pour utiliser les agents de réplication. Sur tous les serveurs Linux, exécutez les commandes suivantes dans le terminal.

  ```bash
  sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
  sudo systemctl restart mssql-server
  ```

1. Configurez l'instance SQL Server pour la réplication. Afin de configurer l'instance SQL Server pour la réplication, exécutez `sys.sp_MSrepl_createdatatypemappings` sur toutes les instances participant à la réplication.

  ```sql
  USE msdb
  GO
  exec sys.sp_MSrepl_createdatatypemappings;
  GO
  ```

1. Créez un dossier d’instantanés. Les agents SQL Server nécessitent un dossier d'instantanés pour la lecture et l’écriture. Créez le dossier d’instantanés sur le distributeur.

  Pour créer le dossier d’instantanés et accorder l'accès à l’utilisateur `mssql`, exécutez la commande suivante :

  ```bash
  sudo mkdir /var/opt/mssql/data/ReplData/
  sudo chown mssql /var/opt/mssql/data/ReplData/
  sudo chgrp mssql /var/opt/mssql/data/ReplData/
  ```

## <a name="configure-and-monitor-replication-with-sql-server-management-studio-ssms"></a>Configurer et surveiller la réplication avec SQL Server Management Studio (SSMS)

### <a name="configure-the-distributor"></a>Configurer le serveur de distribution
  
Pour configurer le distributeur : 

1. Sur SSMS, connectez-vous à votre instance SQL Server dans l’Explorateur d'objets.

1. Cliquez avec le bouton droit sur **Réplication**, puis sélectionnez **Configurer la distribution**.

1. Suivez les instructions de l'**Assistant Configuration de la distribution**.

### <a name="create-publication-and-articles"></a>Créer une publication et des articles

Pour créer une publication et des articles :

1. Dans l'Explorateur d'objets, cliquez sur **Réplication** > **Publications locales**> **Nouvelle publication...** .

1. Suivez les instructions de l’**Assistant Nouvelle publication** pour configurer le type de réplication et les articles qui appartiennent à la publication.

### <a name="configure-the-subscription"></a>Configurer l'abonnement

Pour configurer l'abonnement dans l'Explorateur d'objets, cliquez sur **Réplication** > **Abonnements locaux**> **Nouveaux abonnements...** .

### <a name="monitor-replication-jobs"></a>Surveiller les travaux de réplication

Utilisez le moniteur de réplication pour surveiller les travaux de réplication.

Dans l’Explorateur d'objets, cliquez avec le bouton droit sur **Réplication**, puis sélectionnez **Lancer le moniteur de réplication**.

## <a name="next-steps"></a>Étapes suivantes

[Concepts : Réplication SQL Server sur Linux](sql-server-linux-replication.md)

[Procédures stockées de réplication](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).
