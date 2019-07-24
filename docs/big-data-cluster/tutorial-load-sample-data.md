---
title: Charger un exemple de données
titleSuffix: SQL Server big data clusters
description: Ce didacticiel montre comment charger des exemples de données dans un cluster SQL Server Big Data. Les exemples de données incluent des données relationnelles dans l’instance maître SQL Server. Il comprend également des données HDFS dans le pool de stockage. Ces données prennent en charge d’autres didacticiels dans cette section.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5b35eccece4df47cb483932386cf6a38e45d2dc8
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419276"
---
# <a name="tutorial-load-sample-data-into-a-sql-server-big-data-cluster"></a>Tutoriel : Charger des exemples de données dans un cluster SQL Server Big Data

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Ce didacticiel explique comment utiliser un script pour charger des exemples de données dans un cluster SQL Server 2019 Big Data (version préliminaire). La plupart des autres didacticiels de la documentation utilisent ces exemples de données.

> [!TIP]
> Vous trouverez des exemples supplémentaires pour SQL Server 2019 Big Data cluster (version préliminaire) dans le référentiel GitHub [SQL-Server-Samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster) . Ils se trouvent dans **SQL-Server-Samples/Samples/features/SQL-Big-Data-cluster/** Path.

## <a name="prerequisites"></a>Prérequis

- [Un cluster Big Data déployé](deployment-guidance.md)
- [Outils Big Data](deploy-big-data-tools.md)
   - **azdata**
   - **kubectl**
   - **sqlcmd**
   - **curl**

## <a id="sampledata"></a>Charger les exemples de données

Les étapes suivantes utilisent un script de démarrage pour télécharger une sauvegarde de base de données SQL Server et charger les données dans votre cluster Big Data. Pour faciliter l’utilisation, ces étapes ont été réparties dans les sections [Windows](#windows) et [Linux](#linux) .

## <a id="windows"></a> Windows

Les étapes suivantes décrivent comment utiliser un client Windows pour charger les exemples de données dans votre cluster Big Data.

1. Ouvrez une nouvelle invite de commandes Windows.

   > [!IMPORTANT]
   > N’utilisez pas Windows PowerShell pour ces étapes. Dans PowerShell, le script échouera, car il utilisera la version PowerShell **de l'** opération.

1. Utilisez la **boucle** pour télécharger le script de démarrage pour les exemples de données.

   ```cmd
   curl -o bootstrap-sample-db.cmd "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.cmd"
   ```

1. Téléchargez le script Transact-SQL **bootstrap-Sample-DB. SQL** . Ce script est appelé par le script de démarrage.

   ```cmd
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. Le script de démarrage requiert les paramètres positionnels suivants pour votre cluster Big Data:

   | Paramètre | Description |
   |---|---|
   | < CLUSTER_NAMESPACE > | Le nom que vous avez donné à votre cluster Big Data. |
   | <SQL_MASTER_IP> | L’adresse IP de votre instance maître. |
   | <SQL_MASTER_SA_PASSWORD> | Mot de passe SA pour l’instance maître. |
   | <KNOX_IP> | Adresse IP de la passerelle HDFS/Spark. |
   | <KNOX_PASSWORD> | Mot de passe pour la passerelle HDFS/Spark. |

   > [!TIP]
   > Utilisez [kubectl](cluster-troubleshooting-commands.md) pour rechercher les adresses IP de l’instance principale de SQL Server et Knox. Exécutez `kubectl get svc -n <your-big-data-cluster-name>` et examinez les adresses IP externes de l’instance principale (**Master-SVC-External**) et Knox (**Gateway-SVC-External**). Le nom par défaut d’un cluster est **MSSQL-cluster**.

1. Exécutez le script de démarrage.

   ```cmd
   .\bootstrap-sample-db.cmd <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a id="linux"></a>Linux

Les étapes suivantes décrivent comment utiliser un client Linux pour charger les exemples de données dans votre cluster Big Data.

1. Téléchargez le script de démarrage et affectez-lui des autorisations exécutables.

   ```bash
   curl -o bootstrap-sample-db.sh "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sh"
   chmod +x bootstrap-sample-db.sh
   ```

1. Téléchargez le script Transact-SQL **bootstrap-Sample-DB. SQL** . Ce script est appelé par le script de démarrage.

   ```bash
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. Le script de démarrage requiert les paramètres positionnels suivants pour votre cluster Big Data:

   | Paramètre | Description |
   |---|---|
   | < CLUSTER_NAMESPACE > | Le nom que vous avez donné à votre cluster Big Data. |
   | <SQL_MASTER_IP> | L’adresse IP de votre instance maître. |
   | <SQL_MASTER_SA_PASSWORD> | Mot de passe SA pour l’instance maître. |
   | <KNOX_IP> | Adresse IP de la passerelle HDFS/Spark. |
   | <KNOX_PASSWORD> | Mot de passe pour la passerelle HDFS/Spark. |

   > [!TIP]
   > Utilisez [kubectl](cluster-troubleshooting-commands.md) pour rechercher les adresses IP de l’instance principale de SQL Server et Knox. Exécutez `kubectl get svc -n <your-big-data-cluster-name>` et examinez les adresses IP externes de l’instance principale (**Master-SVC-External**) et Knox (**Gateway-SVC-External**). Le nom par défaut d’un cluster est **MSSQL-cluster**.

1. Exécutez le script de démarrage.

   ```bash
   sudo env "PATH=$PATH" ./bootstrap-sample-db.sh <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a name="next-steps"></a>Étapes suivantes

Après l’exécution du script de démarrage, votre cluster Big Data contient les exemples de bases de données et de données HDFS. Les didacticiels suivants utilisent les exemples de données pour illustrer Big Data fonctionnalités de cluster:

Virtualisation des données:

- [Tutoriel : Interroger HDFS dans un cluster SQL Server Big Data](tutorial-query-hdfs-storage-pool.md)
- [Tutoriel : Interroger Oracle à partir d’un cluster SQL Server Big Data](tutorial-query-oracle.md)

Ingestion de données:

- [Tutoriel : Réception de données dans un pool de données SQL Server avec Transact-SQL](tutorial-data-pool-ingest-sql.md)
- [Tutoriel : Réception de données dans un pool de données SQL Server avec des travaux Spark](tutorial-data-pool-ingest-spark.md)

Blocs-notes

- [Tutoriel : Exécuter un exemple de bloc-notes sur un cluster SQL Server 2019 Big Data](tutorial-notebook-spark.md)