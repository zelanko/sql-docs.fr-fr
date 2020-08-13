---
title: Connecter Spark à SQL Server
titleSuffix: SQL Server big data clusters
description: Découvrez comment utiliser le connecteur Apache Spark pour SQL Server et Azure SQL pour lire et écrire dans SQL Server.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning-bdc
ms.openlocfilehash: 3cb36c4bdddfaa97b9b6c08015308799d54cb0dc
ms.sourcegitcommit: 56f6892b3795da308d226d4b3c5c859ead2e830a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86438071"
---
# <a name="how-to-read-and-write-to-sql-server-from-spark-using-the-apache-spark-connector-for-sql-server-and-azure-sql"></a>Comment lire et écrire dans SQL Server à partir de Spark à l’aide du connecteur Apache Spark pour SQL Server et Azure SQL

Un modèle d’utilisation clé du Big Data est le traitement de données volumineuses dans Spark, suivi de l’écriture des données dans SQL Server pour l’accès aux applications métier. Ces modèles d’utilisation tirent parti d’un connecteur qui utilise des optimisations SQL clés et fournit un mécanisme d’écriture efficace.

Cet article présente l’interface du connecteur Apache Spark pour SQL Server et Azure SQL, et explique comment l’instancier en vue d’une utilisation en mode non AD et en mode AD. Ensuite, il fournit un exemple d’utilisation du connecteur Apache Spark Connector for SQL Server et Azure SQL pour lire et écrire des données aux emplacements suivants au sein d’un cluster Big Data :
1. Instance maître SQL Server
1. Pool de données SQL Server

   ![Diagramme du connecteur Apache Spark pour SQL Server et Azure SQL](./media/spark-mssql-connector/mssql-spark-connector-diagram.png)

## <a name="apache-spark-connector-for-sql-server-and-azure-sql-interface"></a>Interface du connecteur Apache Spark pour SQL Server et Azure SQL

SQL Server 2019 fournit le [**connecteur Apache Spark pour SQL Server et Azure SQL**](https://github.com/microsoft/sql-spark-connector) pour les clusters Big Data qui utilisent des API d’écriture en bloc SQL Server pour les écritures de Spark à SQL. Le connecteur Apache Spark pour SQL Server et Azure SQL est basé sur des API de source de données Spark et fournit une interface familière au connecteur JDBC Spark. Pour obtenir les paramètres d’interface, consultez la [documentation sur Apache Spark](http://spark.apache.org/docs/latest/sql-data-sources-jdbc.html). Le connecteur Apache Spark pour SQL Server et Azure SQL est référencé par le nom **com.microsoft.sqlserver.jdbc.spark**. Le connecteur Apache Spark pour SQL Server et Azure SQL prend en charge deux modes de sécurité pour la connexion avec SQL Server, le mode non AD et le mode AD :
### <a name="non-ad-mode"></a>Mode non AD
En mode de sécurité non AD, chaque utilisateur dispose d’un nom d’utilisateur et d’un mot de passe qui doivent être fournis en tant que paramètres pendant l’instanciation du connecteur afin d’effectuer des opérations de lecture et/ou d’écriture.
Voici un exemple d’instanciation de connecteur pour le mode non AD :
```python
# Note: '?' is a placeholder for a necessary user-specified value
connector_type = "com.microsoft.sqlserver.jdbc.spark" 

url = "jdbc:sqlserver://master-p-svc;databaseName=?;"
writer = df.write \ 
   .format(connector_type)\ 
   .mode("overwrite") 
   .option("url", url) \ 
   .option("user", ?) \ 
   .option("password",?) 
writer.save() 
```
### <a name="ad-mode"></a>Mode AD :
En mode de sécurité AD, une fois que l’utilisateur a généré un fichier keytab, il doit fournir `principal` et `keytab` en tant que paramètres lors de l’instanciation du connecteur.

Dans ce mode, le pilote charge le fichier keytab dans les conteneurs d’exécuteur respectifs. Ensuite, les exécuteurs utilisent le nom principal et le keytab pour générer un jeton qui est utilisé afin de créer un connecteur JDBC pour la lecture et l’écriture de données.

Voici un exemple d’instanciation de connecteur pour le mode AD :
```python
# Note: '?' is a placeholder for a necessary user-specified value
connector_type = "com.microsoft.sqlserver.jdbc.spark"

url = "jdbc:sqlserver://master-p-svc;databaseName=?;integratedSecurity=true;authenticationScheme=JavaKerberos;" 
writer = df.write \ 
   .format(connector_type)\ 
   .mode("overwrite") 
   .option("url", url) \ 
   .option("principal", ?) \ 
   .option("keytab", ?)   

writer.save() 
```

Le tableau suivant décrit les nouveaux paramètres d’interface et ceux qui ont été modifiés :

| Nom de la propriété | Facultatif | Description |
|---|---|---|
| **isolationLevel** | Oui | Décrit le niveau d’isolation de la connexion. La valeur par défaut pour le connecteur est **READ_COMMITTED** |

Le connecteur utilise les API d’écriture en bloc SQL Server. Tous les paramètres d’écriture en bloc peuvent être passés en tant que paramètres facultatifs par l’utilisateur et sont passés en l’état par le connecteur à l’API sous-jacente. Pour plus d’informations sur les opérations d’écriture en bloc, consultez [SQLServerBulkCopyOptions]( ../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#sqlserverbulkcopyoptions).

## <a name="apache-spark-connector-for-sql-server-and-azure-sql-sample"></a>Exemple de connecteur Apache Spark pour SQL Server et Azure SQL
L’exemple effectue les tâches suivantes :

- Lire un fichier à partir de HDFS et effectuer un traitement de base.
- Écrire le dataframe dans une instance maître SQL Server en tant que table SQL, puis lire la table dans un dataframe.
- Écrire le dataframe dans un pool de données SQL Server en tant que table SQL externe, puis lire la table externe dans un dataframe.
### <a name="prerequisites"></a>Prérequis

- [Cluster Big Data SQL Server](deploy-get-started.md)

- [Azure Data Studio](https://aka.ms/getazuredatastudio)

### <a name="create-the-target-database"></a>Créer la base de données cible

1. Ouvrez Azure Data Studio et [connectez-vous à l’instance maître SQL Server de votre cluster Big Data](connect-to-big-data-cluster.md).

1. Créez une requête, puis exécutez la commande suivante pour créer un exemple de base de données nommé **MyTestDatabase**.

   ```sql
   Create DATABASE MyTestDatabase
   GO
   ```

### <a name="load-sample-data-into-hdfs"></a>Charger des exemples de données dans HDFS

1. Téléchargez [AdultCensusIncome.csv](https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv) sur votre ordinateur local.

1. Lancez Azure Data Studio et [connectez-vous à votre cluster Big Data](connect-to-big-data-cluster.md).

1. Cliquez avec le bouton droit sur le dossier HDFS dans votre cluster Big Data, puis sélectionnez **Nouveau répertoire**. Nommez le répertoire **spark_data**.

1. Cliquez avec le bouton droit sur le répertoire **spark_data**, puis sélectionnez **Charger des fichiers**. Chargez le fichier **AdultCensusIncome.csv**.

   ![Fichier CSV AdultCensusIncome](./media/spark-mssql-connector/spark_data.png)

### <a name="run-the-sample-notebook"></a>Exécuter l’exemple de notebook

Pour illustrer l’utilisation du connecteur Apache Spark pour SQL Server et Azure SQL avec ces données en mode non AD, vous pouvez télécharger un exemple de notebook, l’ouvrir dans Azure Data Studio et exécuter chaque bloc de code. Pour plus d’informations sur l’utilisation des notebooks, consultez [Guide pratique pour utiliser des notebooks avec SQL Server](../azure-data-studio/notebooks-guidance.md).

1. À partir d’une ligne de commande PowerShell ou bash, exécutez la commande suivante pour télécharger l’exemple de notebook **mssql_spark_connector_non_ad_pyspark.ipynb** :

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/data-virtualization/mssql_spark_connector_non_ad_pyspark.ipynb"
   ```

1. Dans Azure Data Studio, ouvrez le fichier de l’exemple de notebook. Vérifiez qu’il est connecté à votre passerelle HDFS/Spark pour votre cluster Big Data.

1. Exécutez chaque cellule de code dans l’exemple pour voir l’utilisation du connecteur Apache Spark pour SQL Server et Azure SQL.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Guide pratique pour déployer des [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] sur Kubernetes](deployment-guidance.md)

Vous avez des commentaires ou des recommandations concernant les fonctionnalités des clusters Big Data SQL Server ? [Faites-nous part de vos commentaires sur les clusters Big Data SQL Server](https://aka.ms/sql-server-bdc-feedback).
