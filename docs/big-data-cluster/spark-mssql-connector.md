---
title: Connecter Spark à SQL Server
titleSuffix: SQL Server big data clusters
description: Découvrez comment utiliser le connecteur Spark MSSQL dans Spark pour lire et écrire dans SQL Server.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: shivsood
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7720db661d90c3ff2ebec593b22a5aa638038132
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2019
ms.locfileid: "73844218"
---
# <a name="how-to-read-and-write-to-sql-server-from-spark-using-the-mssql-spark-connector"></a>Comment lire et écrire dans SQL Server à partir de Spark à l’aide du connecteur Spark MSSQL

Un modèle d’utilisation clé du Big Data est le traitement de données volumineuses dans Spark, suivi de l’écriture des données dans SQL Server pour l’accès aux applications métier. Ces modèles d’utilisation tirent parti d’un connecteur qui utilise des optimisations SQL clés et fournit un mécanisme d’écriture efficace.

Cet article fournit un exemple d’utilisation du connecteur Spark MSSQL pour lire et écrire des données aux emplacements suivants au sein d’un cluster Big Data :

1. Instance maître SQL Server
1. Pool de données SQL Server

   ![Diagramme du connecteur Spark de MSSQL](./media/spark-mssql-connector/mssql-spark-connector-diagram.png)

L’exemple effectue les tâches suivantes :

- Lire un fichier à partir de HDFS et effectuer un traitement de base.
- Écrire le dataframe dans une instance maître SQL Server en tant que table SQL, puis lire la table dans un dataframe.
- Écrire le dataframe dans un pool de données SQL Server en tant que table SQL externe, puis lire la table externe dans un dataframe.

## <a name="mssql-spark-connector-interface"></a>Interface du connecteur Spark MSSQL

SQL Server 2019 fournit le **connecteur Spark MSSQL** pour les clusters Big Data qui utilisent des API d’écriture en bloc SQL Server pour les écritures de Spark à SQL. Le connecteur Spark MSSQL est basé sur des API de source de données Spark et fournit une interface familière au connecteur JDBC Spark. Pour obtenir les paramètres d’interface, consultez la [documentation sur Apache Spark](http://spark.apache.org/docs/latest/sql-data-sources-jdbc.html). Le connecteur Spark MSSQL est référencé par le nom **com.microsoft.sqlserver.jdbc.spark**.

Le tableau suivant décrit les nouveaux paramètres d’interface et ceux qui ont été modifiés :

| Nom de la propriété | Ce paramètre est facultatif | Description |
|---|---|---|
| **isolationLevel** | Oui | Décrit le niveau d’isolation de la connexion. La valeur par défaut pour le connecteur MSSQLSpark est **READ_COMMITTED** |

Le connecteur utilise les API d’écriture en bloc SQL Server. Tous les paramètres d’écriture en bloc peuvent être passés en tant que paramètres facultatifs par l’utilisateur et sont passés en l’état par le connecteur à l’API sous-jacente. Pour plus d’informations sur les opérations d’écriture en bloc, consultez [SQLServerBulkCopyOptions]( ../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#sqlserverbulkcopyoptions).

## <a name="prerequisites"></a>Conditions préalables requises

- [Cluster Big Data SQL Server](deploy-get-started.md)

- [Azure Data Studio](https://aka.ms/getazuredatastudio)

## <a name="create-the-target-database"></a>Créer la base de données cible

1. Ouvrez Azure Data Studio et [connectez-vous à l’instance maître SQL Server de votre cluster Big Data](connect-to-big-data-cluster.md).

1. Créez une requête, puis exécutez la commande suivante pour créer un exemple de base de données nommé **MyTestDatabase**.

   ```sql
   Create DATABASE MyTestDatabase
   GO
   ```

## <a name="load-sample-data-into-hdfs"></a>Charger des exemples de données dans HDFS

1. Téléchargez [AdultCensusIncome.csv](https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv) sur votre ordinateur local.

1. Lancez Azure Data Studio et [connectez-vous à votre cluster Big Data](connect-to-big-data-cluster.md).

1. Cliquez avec le bouton droit sur le dossier HDFS dans votre cluster Big Data, puis sélectionnez **Nouveau répertoire**. Nommez le répertoire **spark_data**.

1. Cliquez avec le bouton droit sur le répertoire **spark_data**, puis sélectionnez **Charger des fichiers**. Chargez le fichier **AdultCensusIncome.csv**.

   ![Fichier CSV AdultCensusIncome](./media/spark-mssql-connector/spark_data.png)

## <a name="run-the-sample-notebook"></a>Exécuter l’exemple de notebook

Pour illustrer l’utilisation du connecteur Spark MSSQL avec ces données, vous pouvez télécharger un exemple de notebook, l’ouvrir dans Azure Data Studio et exécuter chaque bloc de code. Pour plus d’informations sur l’utilisation des notebooks, consultez [Guide pratique pour utiliser des notebooks dans SQL Server](notebooks-guidance.md).

1. À partir d’une ligne de commande PowerShell ou bash, exécutez la commande suivante pour télécharger l’exemple de notebook **mssql_spark_connector.ipynb** :

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/data-virtualization/mssql_spark_connector.ipynb"
   ```

1. Dans Azure Data Studio, ouvrez le fichier de l’exemple de notebook. Vérifiez qu’il est connecté à votre passerelle HDFS/Spark pour votre cluster Big Data.

1. Exécutez chaque cellule de code dans l’exemple pour voir l’utilisation du connecteur Spark MSSQL.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Guide pratique pour déployer des [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] sur Kubernetes](deployment-guidance.md)