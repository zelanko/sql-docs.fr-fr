---
title: "Le Feature Pack SQL Server Integration Services (SSIS) pour Azure | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SQL13.SSIS.AZURE.F1"
  - "SQL14.SSIS.AZURE.F1"
ms.assetid: 31de555f-ae62-4f2f-a6a6-77fea1fa8189
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 15
---
# Le Feature Pack SQL Server Integration Services (SSIS) pour Azure
  Le Feature Pack SQL Server Integration Services (SSIS) pour Azure associé à SQL Server 2016 est une extension qui fournit les composants suivants pour SSIS dans le cadre de la connexion à Azure, du transfert de données entre des sources de données Azure et locales et du traitement de données stockées dans Azure.

[![Télécharger le Feature Pack SSIS pour Azure](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=626967) **Télécharger** le [Feature Pack SSIS pour Azure pour SQL Server 2016](http://go.microsoft.com/fwlink/?LinkID=626967)


-   Gestionnaires de connexions

    -   [Gestionnaire de connexions de stockage Azure](../integration-services/connection-manager/azure-storage-connection-manager.md)

    -   [Gestionnaire de connexions d’abonnement Azure](../integration-services/connection-manager/azure-subscription-connection-manager.md)
    
    -   [Gestionnaire de connexions Azure Data Lake Store](../integration-services/connection-manager/azure-data-lake-store-connection-manager.md)

-   Tâches

    -   [Tâche de chargement d’objets blob Azure](../integration-services/control-flow/azure-blob-upload-task.md)

    -   [Tâche de téléchargement d’objets blob Azure](../integration-services/control-flow/azure-blob-download-task.md)

    -   [Tâche Hive Azure HDInsight](../integration-services/control-flow/azure-hdinsight-hive-task.md)

    -   [Tâche Pig Azure HDInsight](../integration-services/control-flow/azure-hdinsight-pig-task.md)

    -   [Tâche de création d’un cluster Azure HDInsight](../integration-services/control-flow/azure-hdinsight-create-cluster-task.md)

    -   [Tâche de suppression d’un cluster Azure HDInsight](../integration-services/control-flow/azure-hdinsight-delete-cluster-task.md)
    
    -   [Tâche de chargement Azure SQL Data Warehouse](../integration-services/control-flow/azure-sql-dw-upload-task.md)

-   Composants de flux de données

    -   [Source des objets blob Azure](../integration-services/data-flow/azure-blob-source.md)

    -   [Destination des objets blob Azure](../integration-services/data-flow/azure-blob-destination.md)
    
    -   [Source Azure Data Lake Store](../integration-services/data-flow/azure-data-lake-store-source.md)
    
    -   [Destination Azure Data Lake Store](../integration-services/data-flow/azure-data-lake-store-destination.md)

-   Énumérateur d'objets Blob Azure. Voir [Énumérateur = Énumérateur d’objets blob Azure Foreach](../../../Topic/Foreach%20Loop%20Editor%20\(Collection%20Page\).md#ForeachAzureBlob)

## <a name="download-the-feature-pack"></a>Télécharger le Feature Pack
 Vous pouvez télécharger le Feature Pack SQL Server Integration Services (SSIS) pour Azure associé à SQL Server 2016 [ici](http://go.microsoft.com/fwlink/?LinkID=626967).

## <a name="prerequisites"></a>Conditions préalables
 Avant d’installer le Feature Pack, vous devez vérifier que les conditions préalables suivantes sont remplies.

-   SQL Server Integration Services

-   .Net Framework 4.5

## <a name="scenario-processing-big-data"></a>Scénario : traitement du Big Data
 Utilisez le connecteur Azure pour accomplir le travail suivant de traitement de données volumineuses :

1.  Utilisez la tâche de téléchargement d'objet blob Azure pour charger des données d'entrée dans le stockage d'objets blob Azure.

2.  Utilisez la tâche de création de cluster Azure HDInsight pour créer un cluster Azure HDInsight. Cette étape est facultative si vous souhaitez utiliser votre propre cluster.

3.  Utilisez la tâche Hive ou Pig Azure HDInsight pour invoquer un travail Pig ou Hive sur le cluster Azure HDInsight.

4.  Utilisez la tâche de suppression de cluster Azure HDInsight pour supprimer le cluster HDInsight après utilisation, si vous avez créé un cluster HDInsight à la demande à l'étape 2.

5.  Utilisez la tâche de téléchargement d'objet blob Azure HDInsight pour télécharger les données de sortie des travaux Pig/Hive à partir du stockage d'objets blob Azure.

![SSIS-AzureConnector-BigDataScenario](../integration-services/media/ssis-azureconnector-bigdatascenario.png)
 
## <a name="scenario-managing-data-in-the-cloud"></a>Scénario : gestion des données dans le cloud
 Utilisez la destination d’objets blob Azure dans un package SSIS pour écrire des données de sortie dans un Azure Blob Storage, ou la source d’objets blob Azure pour lire des données à partir d’un stockage Azure Blob Storage.

![SSIS-AzureConnector-CloudArchive-1](../integration-services/media/ssis-azureconnector-cloudarchive-1.png)
 
 ![SSIS-AzureConnector-CloudArchive-2](../integration-services/media/ssis-azureconnector-cloudarchive-2.png)

 Utilisez le conteneur de boucles Foreach avec l’énumérateur d’objet blob Azure pour traiter des données dans plusieurs fichiers blob.

![SSIS-AzureConnector-CloudArchive-3](../integration-services/media/ssis-azureconnector-cloudarchive-3.png)
  