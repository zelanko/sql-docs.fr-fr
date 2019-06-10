---
title: Connecter Spark à SQL Server
titleSuffix: SQL Server big data clusters
description: Découvrez comment utiliser le connecteur Spark MSSQL dans Spark pour lire et écrire à SQL Server.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: faa9d90cf78df5d73f125c7660b79d39e2bd5622
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66770941"
---
# <a name="how-to-read-and-write-to-sql-server-from-spark-using-the-mssql-spark-connector"></a>Comment lire et écrire dans SQL Server à partir de Spark à l’aide du connecteur Spark MSSQL

Un modèle d’utilisation de clé de données volumineuses est le traitement de données de volume élevé dans Spark, suivie de l’écriture des données dans SQL Server pour l’accès à line of business applications. Ces modèles d’utilisation bénéficient d’un connecteur qui utilise des clés optimisations de SQL et fournit un mécanisme efficace d’écriture.

Les Clusters de données volumineuses fournit un nouveau connecteur MSSQL Spark qui utilise SQL Server en bloc écrire des API pour une performante Spark à l’écriture SQL. Cet article fournit un exemple montrant comment lire et écrire dans SQL Server à partir de Spark à l’aide du connecteur Spark MSSQL. Dans cet exemple, les données sont lues à partir de HDFS dans un cluster de données volumineuses, traitées par Spark et ensuite écrites dans l’instance principale de SQL Server dans le cluster en utilisant le nouveau connecteur MSSQL Spark.

## <a name="mssql-spark-connector-interface"></a>Interface de connecteur Spark MSSQL

Connecteur Spark de MSSQL est basé sur la source de données Spark API et fournit une interface de connecteur Spark JDBC familière. Pour les paramètres de l’interface référence [documentation Apache Spark](http://spark.apache.org/docs/latest/sql-data-sources-jdbc.html). Le connecteur Spark de MSSQL est référencé par le nom **com.microsoft.sqlserver.jdbc.spark**.

Le tableau suivant décrit les paramètres d’interface qui ont été modifiées ou sont nouveaux :

| Nom de la propriété | Ce paramètre est facultatif | Description |
|---|---|---|
| **isolationLevel** | Oui | Cette section décrit le niveau d’isolation de la connexion. Est la valeur par défaut pour le connecteur de MSSQLSpark **READ_COMMITTED** |

Le connecteur utilise en bloc de SQL Server écrire des API. Toute écriture en bloc de paramètres peuvent être passés comme paramètres facultatifs par l’utilisateur et sont passés en tant que-est par le connecteur à l’API sous-jacente. Pour plus d’informations en bloc les opérations d’écriture, consultez [SQLServerBulkCopyOptions]( ../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#sqlserverbulkcopyoptions).

## <a name="prerequisites"></a>Prérequis

- Un [cluster de données volumineux de SQL Server](deploy-get-started.md).

- [Azure Data Studio](../azure-data-studio/download.md).

## <a name="create-the-target-database"></a>Créer la base de données cible

1. Ouvrez Azure Data Studio, et [se connecter à l’instance principale de SQL Server de votre cluster big data](connect-to-big-data-cluster.md).

1. Créer une nouvelle requête et exécutez la commande suivante pour créer une base de données exemple nommé **MyTestDatabase**.

   ```sql
   Create DATABASE MyTestDatabase
   GO
   ```

## <a name="load-sample-data-into-hdfs"></a>Charger des exemples de données dans HDFS

1. Télécharger [AdultCensusIncome.csv](https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv) sur votre ordinateur local.

1. Dans Azure Data Studio, avec le bouton droit sur le dossier HDFS dans votre cluster de données volumineux, puis sélectionnez **nouveau répertoire**. Nommez le répertoire **spark_data**.

1. Cliquez avec le bouton droit sur le **spark_data** répertoire, puis sélectionnez **charger des fichiers**. Télécharger le **AdultCensusIncome.csv** fichier.

   ![Fichier CSV de AdultCensusIncome](./media/spark-mssql-connector/spark_data.png)

## <a name="run-the-sample-notebook"></a>Exécutez l’exemple de notebook

Pour illustrer l’utilisation du connecteur Spark MSSQL avec ces données, vous pouvez télécharger un exemple de notebook, ouvrez-le dans Azure Data Studio et exécuter chaque bloc de code. Pour plus d’informations sur l’utilisation des blocs-notes, consultez [comment utiliser des blocs-notes en version préliminaire de SQL Server 2019](notebooks-guidance.md).

1. À partir d’une ligne de commande PowerShell ou bash, exécutez la commande suivante pour télécharger le **mssql_spark_connector.ipynb** exemple de notebook :

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/spark_to_sql/mssql_spark_connector.ipynb"
   ```

1. Dans Azure Data Studio, ouvrez l’exemple de fichier de bloc-notes. Vérifiez qu’il est connecté à votre passerelle HDFS/Spark de votre cluster big data.

1. Exécutez chaque cellule de code dans l’exemple pour afficher l’utilisation du connecteur de MSSQL Spark.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses, consultez [comment déployer des données volumineuses de SQL Server clusters sur Kubernetes](deployment-guidance.md)