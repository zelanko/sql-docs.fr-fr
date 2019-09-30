---
title: Feature Pack SQL Server Integration Services (SSIS) pour Azure | Microsoft Docs
ms.custom: ''
ms.date: 08/17/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.SSIS.AZURE.F1
- SQL14.SSIS.AZURE.F1
ms.assetid: 31de555f-ae62-4f2f-a6a6-77fea1fa8189
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e8188dd6b26b3eb81596394ce8b7947654b00df5
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71294949"
---
# <a name="azure-feature-pack-for-integration-services-ssis"></a>Le Feature Pack SQL Server Integration Services (SSIS) pour Azure

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Le Feature Pack SQL Server Integration Services (SSIS) pour Azure est une extension qui fournit les composants répertoriés dans cette page afin de permettre à SSIS de se connecter aux services Azure, de transférer des données entre des sources de données Azure et locales, et de traiter des données stockées dans Azure.

[![Télécharger le Feature Pack SSIS pour Azure](https://docs.microsoft.com/analysis-services/analysis-services/media/download.png)](https://www.microsoft.com/download/details.aspx?id=54798) **Télécharger**

- Pour SQL Server 2017 : [Feature Pack Microsoft SQL Server 2017 Integration Services pour Azure](https://www.microsoft.com/download/details.aspx?id=54798)
- Pour SQL Server 2016 : [Feature Pack Microsoft SQL Server 2016 Integration Services pour Azure](https://www.microsoft.com/download/details.aspx?id=49492)
- Pour SQL Server 2014 : [Feature Pack Microsoft SQL Server 2014 Integration Services pour Azure](https://www.microsoft.com/download/details.aspx?id=47366)
- Pour SQL Server 2012 : [Feature Pack Microsoft SQL Server 2012 Integration Services pour Azure](https://www.microsoft.com/download/details.aspx?id=47367)

Les pages de téléchargement incluent également des informations sur les prérequis. Veillez à installer SQL Server avant d’installer Azure Feature Pack sur un serveur. Sinon, il est possible que les composants du Feature Pack ne soient pas disponibles quand vous déployez des packages sur la base de données de catalogues SSIS, SSISDB, sur le serveur.

## <a name="components-in-the-feature-pack"></a>Composants du Feature Pack
-   Gestionnaires de connexions

    -   [Gestionnaire de connexions Azure Data Lake Analytics](connection-manager/azure-data-lake-analytics-connection-manager.md)

    -   [Gestionnaire de connexions Azure Data Lake Store](../integration-services/connection-manager/azure-data-lake-store-connection-manager.md)
    
    -   [Gestionnaire de connexions Azure HDInsight](../integration-services/connection-manager/azure-hdinsight-connection-manager.md)

    -   [Gestionnaire de connexions Azure Resource Manager](../integration-services/connection-manager/azure-resource-manager-connection-manager.md)
    
    -   [Gestionnaire de connexions de stockage Azure](../integration-services/connection-manager/azure-storage-connection-manager.md)

    -   [Gestionnaire de connexions d’abonnement Azure](../integration-services/connection-manager/azure-subscription-connection-manager.md)
    
-   Tâches

    -   [Tâche de téléchargement d’objets blob Azure](../integration-services/control-flow/azure-blob-download-task.md)

    -   [Tâche de chargement d’objets blob Azure](../integration-services/control-flow/azure-blob-upload-task.md)

    -   [Tâche Azure Data Lake Analytics](control-flow/azure-data-lake-analytics-task.md)

    -   [Tâche du système de fichiers Azure Data Lake Store](../integration-services/control-flow/azure-data-lake-store-file-system-task.md)

    -   [Tâche de création d’un cluster Azure HDInsight](../integration-services/control-flow/azure-hdinsight-create-cluster-task.md)

    -   [Tâche de suppression d’un cluster Azure HDInsight](../integration-services/control-flow/azure-hdinsight-delete-cluster-task.md)
    
    -   [Tâche Hive Azure HDInsight](../integration-services/control-flow/azure-hdinsight-hive-task.md)

    -   [Tâche Pig Azure HDInsight](../integration-services/control-flow/azure-hdinsight-pig-task.md)

    -   [Tâche de chargement Azure SQL Data Warehouse](../integration-services/control-flow/azure-sql-dw-upload-task.md)

    -   [Tâche de fichier flexible](../integration-services/control-flow/flexible-file-task.md)

-   Composants de flux de données

    -   [Source des objets blob Azure](../integration-services/data-flow/azure-blob-source.md)

    -   [Destination des objets blob Azure](../integration-services/data-flow/azure-blob-destination.md)
    
    -   [Source Azure Data Lake Store](../integration-services/data-flow/azure-data-lake-store-source.md)
    
    -   [Destination Azure Data Lake Store](../integration-services/data-flow/azure-data-lake-store-destination.md)

    -   [Source de fichier flexible](../integration-services/data-flow/flexible-file-source.md)

    -   [Destination de fichier flexible](../integration-services/data-flow/flexible-file-destination.md)

-   Énumérateur de fichier Data Lake Storage Gen2, Azure Data Lake Store et Objets Blob Azure. Voir [Conteneur de boucles Foreach](../integration-services/control-flow/foreach-loop-container.md).

## <a name="use-tls-12"></a>Utiliser TLS 1.2

La version TLS utilisée par le Feature Pack Azure suit les paramètres du .NET Framework système.
Pour utiliser TLS 1.2, ajoutez une valeur `REG_DWORD` nommée `SchUseStrongCrypto` avec des données `1` sous les deux clés de Registre suivantes.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v4.0.30319`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319`

## <a name="dependency-on-java"></a>Dépendance envers Java

Java est requis pour utiliser des formats de fichier ORC/Parquet avec des connecteurs de fichiers plats/Azure Data Lake Store.  
L’architecture (32/64 bits) de la build Java doit correspondre à celle du runtime SSIS à utiliser.
Les builds Java suivantes ont été testées.

- [Zulu OpenJDK 8u192](https://www.azul.com/downloads/zulu/zulu-windows/)
- [Oracle Java SE Runtime Environment 8u192](https://www.oracle.com/technetwork/java/javase/downloads/java-archive-javase8-2177648.html)

### <a name="set-up-zulus-openjdk"></a>Configurer Zulu OpenJDK

1. Téléchargez et extrayez le package compressé d’installation.
2. À partir de l’invite de commandes, exécutez `sysdm.cpl`.
3. Sous l’onglet **Avancé**, sélectionnez **Variables d’environnement**.
4. Sous la section **Variables système**, sélectionnez **Nouveau**.
5. Entrez `JAVA_HOME` pour le **Nom de la variable**.
6. Sélectionnez **Parcourir les répertoires**, accédez au dossier extrait et sélectionnez le sous-dossier `jre`.
   Sélectionnez ensuite **OK** et la **valeur de la variable** est automatiquement renseignée.
7. Sélectionnez **OK** pour fermer la boîte de dialogue **Nouvelle Variable système**.
8. Sélectionnez **OK** pour fermer la boîte de dialogue **Variables d’environnement**.
9. Sélectionnez **OK** pour fermer la boîte de dialogue **Propriétés du système**.

### <a name="set-up-zulus-openjdk-on-azure-ssis-integration-runtime"></a>Configurer OpenJDK de Zulu sur Azure-SSIS Integration Runtime

Cette opération doit être effectuée via une [interface d’installation personnalisée](https://docs.microsoft.com/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup) pour Azure-SSIS Integration Runtime.
Supposons que `zulu8.33.0.1-jdk8.0.192-win_x64.zip` est utilisé.
Le conteneur d’objets BLOB peut être organisé comme suit.

~~~
main.cmd
install_openjdk.ps1
zulu8.33.0.1-jdk8.0.192-win_x64.zip
~~~

En tant que point d'entrée, `main.cmd` déclenche l’exécution du script PowerShell `install_openjdk.ps1` qui, à son tour, extrait `zulu8.33.0.1-jdk8.0.192-win_x64.zip` et définit `JAVA_HOME` en conséquence.

**main. cmd**

~~~
powershell.exe -file install_openjdk.ps1
~~~

**install_openjdk. ps1**

~~~
Expand-Archive zulu8.33.0.1-jdk8.0.192-win_x64.zip -DestinationPath C:\
[Environment]::SetEnvironmentVariable("JAVA_HOME", "C:\zulu8.33.0.1-jdk8.0.192-win_x64\jre", "Machine")
~~~

### <a name="set-up-oracles-java-se-runtime-environment"></a>Configurer Oracle Java SE Runtime Environment

1. Téléchargez et exécutez le programme d’installation.
2. Suivez les instructions du programme d’installation pour terminer l’installation.

## <a name="scenario-processing-big-data"></a>Scénario : traitement du Big Data
 Utilisez le connecteur Azure pour accomplir le travail suivant de traitement de données volumineuses :

1.  Utilisez la tâche de téléchargement d'objet blob Azure pour charger des données d'entrée dans le stockage d'objets blob Azure.

2.  Utilisez la tâche de création de cluster Azure HDInsight pour créer un cluster Azure HDInsight. Cette étape est facultative si vous souhaitez utiliser votre propre cluster.

3.  Utilisez la tâche Hive ou Pig Azure HDInsight pour invoquer un travail Pig ou Hive sur le cluster Azure HDInsight.

4.  Utilisez la tâche de suppression de cluster Azure HDInsight pour supprimer le cluster HDInsight après utilisation, si vous avez créé un cluster HDInsight à la demande à l'étape 2.

5.  Utilisez la tâche de téléchargement d'objet blob Azure HDInsight pour télécharger les données de sortie des travaux Pig/Hive à partir du stockage d'objets blob Azure.

![SSIS-AzureConnector-BigDataScenario](../integration-services/media/ssis-azureconnector-bigdatascenario.png)
 
## <a name="scenario-managing-data-in-the-cloud"></a>Scénario : gestion des données dans le cloud
 Utilisez la destination d’objets blob Azure dans un package SSIS pour écrire des données de sortie dans un Azure Blob Storage, ou la source d’objets blob Azure pour lire des données à partir d’un stockage Azure Blob Storage.

![SSIS-AzureConnector-CloudArchive-1](../integration-services/media/ssis-azureconnector-cloudarchive-1.png)
 
 ![SSIS-AzureConnector-CloudArchive-2](../integration-services/media/ssis-azureconnector-cloudarchive-2.png)

 Utilisez le conteneur de boucles Foreach avec l’énumérateur d’objet blob Azure pour traiter des données dans plusieurs fichiers blob.

![SSIS-AzureConnector-CloudArchive-3](../integration-services/media/ssis-azureconnector-cloudarchive-3.png)
  
