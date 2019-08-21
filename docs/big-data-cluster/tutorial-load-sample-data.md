---
title: Charger un exemple de données
titleSuffix: SQL Server big data clusters
description: Ce tutoriel montre comment charger un exemple de données dans un cluster Big Data SQL Server. L’exemple de données inclut des données relationnelles dans l’instance maître SQL Server. Il comprend également des données HDFS dans le pool de stockage. Ces données prennent en charge d’autres tutoriels dans cette section.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 405df2c66917dc5e5b350aaaa0769bede6ccf6c9
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653285"
---
# <a name="tutorial-load-sample-data-into-a-sql-server-big-data-cluster"></a>Tutoriel : Charger un exemple de données dans votre cluster Big Data

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Ce didacticiel explique comment utiliser un script pour charger des exemples de données dans [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]un. La plupart des autres tutoriels de la documentation utilisent cet exemple de données.

> [!TIP]
> Vous trouverez des exemples supplémentaires pour [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] dans le référentiel GitHub [SQL-Server-Samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster) . Le chemin de ce dépôt est le suivant : **sql-server-samples/samples/features/sql-big-data-cluster/** .

## <a name="prerequisites"></a>Prérequis

- [Cluster Big Data déployé](deployment-guidance.md)
- [Outils Big Data](deploy-big-data-tools.md)
   - **azdata**
   - **kubectl**
   - **sqlcmd**
   - **curl**
 
## <a id="sampledata"></a> Charger un exemple de données

Les étapes suivantes utilisent un script d’amorçage pour télécharger une sauvegarde de base de données SQL Server et charger les données dans votre cluster Big Data. Pour faciliter les choses, ces étapes sont réparties en deux sections : [Windows](#windows) et [Linux](#linux).

## <a id="windows"></a> Windows

Les étapes suivantes décrivent comment utiliser un client Windows pour charger l’exemple de données dans votre cluster Big Data.

1. Ouvrez une nouvelle invite de commandes Windows.

   > [!IMPORTANT]
   > N’utilisez pas Windows PowerShell pour ces étapes. Dans PowerShell, le script échoue car il utilise la version PowerShell de **curl**.

1. Utilisez **curl** pour télécharger le script d’amorçage pour l’exemple de données.

   ```cmd
   curl -o bootstrap-sample-db.cmd "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.cmd"
   ```

1. Téléchargez le script Transact-SQL **bootstrap-sample-db.sql**. Ce script est appelé par le script d’amorçage.

   ```cmd
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. Le script d’amorçage nécessite les paramètres positionnels suivants pour votre cluster Big Data :

   | Paramètre | Description |
   |---|---|
   | <CLUSTER_NAMESPACE> | Nom que vous avez donné à votre cluster Big Data. |
   | <SQL_MASTER_IP> | Adresse IP de votre instance maître. |
   | <SQL_MASTER_SA_PASSWORD> | Mot de passe d’administrateur système pour l’instance maître. |
   | <KNOX_IP> | Adresse IP de la passerelle HDFS/Spark. |
   | <KNOX_PASSWORD> | Mot de passe de la passerelle HDFS/Spark. |

   > [!TIP]
   > Utilisez [kubectl](cluster-troubleshooting-commands.md) pour rechercher les adresses IP de l’instance maître de SQL Server et de Knox. Exécutez `kubectl get svc -n <your-big-data-cluster-name>` et examinez les adresses EXTERNAL-IP de l’instance maître (**master-svc-external**) et de Knox (**gateway-svc-external**). Le nom par défaut d’un cluster est **mssql-cluster**.

1. Exécutez le script d’amorçage.

   ```cmd
   .\bootstrap-sample-db.cmd <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a id="linux"></a> Linux

Les étapes suivantes décrivent comment utiliser un client Linux pour charger l’exemple de données dans votre cluster Big Data.

1. Téléchargez le script d’amorçage et affectez-lui les autorisations d’un exécutable.

   ```bash
   curl -o bootstrap-sample-db.sh "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sh"
   chmod +x bootstrap-sample-db.sh
   ```

1. Téléchargez le script Transact-SQL **bootstrap-sample-db.sql**. Ce script est appelé par le script d’amorçage.

   ```bash
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. Le script d’amorçage nécessite les paramètres positionnels suivants pour votre cluster Big Data :

   | Paramètre | Description |
   |---|---|
   | <CLUSTER_NAMESPACE> | Nom que vous avez donné à votre cluster Big Data. |
   | <SQL_MASTER_IP> | Adresse IP de votre instance maître. |
   | <SQL_MASTER_SA_PASSWORD> | Mot de passe d’administrateur système pour l’instance maître. |
   | <KNOX_IP> | Adresse IP de la passerelle HDFS/Spark. |
   | <KNOX_PASSWORD> | Mot de passe de la passerelle HDFS/Spark. |

   > [!TIP]
   > Utilisez [kubectl](cluster-troubleshooting-commands.md) pour rechercher les adresses IP de l’instance maître de SQL Server et de Knox. Exécutez `kubectl get svc -n <your-big-data-cluster-name>` et examinez les adresses EXTERNAL-IP de l’instance maître (**master-svc-external**) et de Knox (**gateway-svc-external**). Le nom par défaut d’un cluster est **mssql-cluster**.

1. Exécutez le script d’amorçage.

   ```bash
   sudo env "PATH=$PATH" ./bootstrap-sample-db.sh <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a name="next-steps"></a>Étapes suivantes

Après l’exécution du script d’amorçage., votre cluster Big Data contient les exemples de bases de données et de données HDFS. Les tutoriels suivants utilisent l’exemple de données pour illustrer les fonctionnalités du cluster Big Data :

Virtualisation de données :

- [Tutoriel : Interroger HDFS dans un cluster Big Data SQL Server](tutorial-query-hdfs-storage-pool.md)
- [Tutoriel : Interroger Oracle à partir d’un cluster Big Data SQL Server](tutorial-query-oracle.md)

Ingestion des données :

- [Tutoriel : Ingérer des données dans un pool de données SQL Server avec Transact-SQL](tutorial-data-pool-ingest-sql.md)
- [Tutoriel : Ingérer des données dans un pool de données SQL Server avec des travaux Spark](tutorial-data-pool-ingest-spark.md)

Notebooks :

- [Tutoriel : Exécuter un exemple de notebook sur un cluster Big Data SQL Server 2019](tutorial-notebook-spark.md)
