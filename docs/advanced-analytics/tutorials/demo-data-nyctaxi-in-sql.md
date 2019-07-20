---
title: Télécharger les scripts et les données de démonstration de la montre de New York pour Embedded R et Python
description: Instructions pour télécharger des exemples de données de taxi de New York et créer une base de données. Les données sont utilisées dans les didacticiels de SQL Server Python et R, qui montrent comment incorporer des scripts dans des procédures stockées SQL Server et des fonctions T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/31/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 1b0eea71105cb22cce81ac482c8ad6df50e63fa0
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68343434"
---
# <a name="nyc-taxi-demo-data-for-sql-server-python-and-r-tutorials"></a>Données de démonstration sur le taxi de New York pour SQL Server didacticiels Python et R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article explique comment configurer un exemple de base de données qui se compose de données publiques à partir des taxis de [New York et de limousines Commission](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml). Ces données sont utilisées dans plusieurs didacticiels R et Python pour l’analyse dans la base de données sur SQL Server. Pour accélérer l’exécution de l’exemple de code, nous avons créé un échantillon représentatif de 1% des données. Sur votre système, le fichier de sauvegarde de la base de données est légèrement supérieur à 90 Mo, ce qui fournit 1,7 million lignes dans la table de données principale.

Pour effectuer cet exercice, vous devez disposer d' [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) ou d’un autre outil capable de restaurer un fichier de sauvegarde de base de données et d’exécuter des requêtes T-SQL.

Les didacticiels et les guides de démarrage rapide utilisant ce jeu de données sont les suivants:

+ [En savoir plus sur l’analytique dans la base de données à l’aide de R dans SQL Server](sqldev-in-database-r-for-sql-developers.md)
+ [En savoir plus sur l’analytique dans la base de données à l’aide de Python dans SQL Server](sqldev-in-database-python-for-sql-developers.md)

## <a name="download-files"></a>Télécharger des fichiers

L’exemple de base de données est un fichier SQL Server 2016 BAK hébergé par Microsoft. Vous pouvez le restaurer sur SQL Server 2016 et versions ultérieures. Le téléchargement de fichiers commence immédiatement lorsque vous cliquez sur le lien. 

La taille du fichier est d’environ 90 Mo.

1. Cliquez sur [NYCTaxi_Sample. bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak) pour télécharger le fichier de sauvegarde de la base de données.

2. Copiez le fichier dans le dossier C:\Program files\Microsoft SQL Server\MSSQL-instance-name\MSSQL\Backup

3. Dans Management Studio, cliquez avec le bouton droit sur **bases de données** , puis sélectionnez **restaurer les fichiers et les groupes de fichiers**.

4. Entrez *NYCTaxi_Sample* comme nom de la base de données.

5. Cliquez sur **à partir de l’appareil** , puis ouvrez la page de sélection du fichier pour sélectionner le fichier de sauvegarde. Cliquez sur **Ajouter** pour sélectionner NYCTaxi_Sample. bak.

6. Activez la case à cocher **restaurer** , puis cliquez sur **OK** pour restaurer la base de données.

## <a name="review-database-objects"></a>Examiner les objets de base de données
   
Vérifiez que les objets de base de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données existent [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]sur l’instance à l’aide de. Vous devez voir la base de données, les tables, les fonctions et les procédures stockées.
  
   ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")

### <a name="objects-in-nyctaxisample-database"></a>Objets dans la base de données NYCTaxi_Sample

Le tableau suivant récapitule les objets créés dans la base de données de démonstration du taxi de New York.

|**Nom de l'objet**|**Type d'objet**|**Description**|
|----------|------------------------|---------------|
|**NYCTaxi_Sample** | base de données | Crée une base de données et deux tables :<br /><br />table dbo. nyctaxi_sample: Contient le jeu de données principal des taxis de New York. Un index cluster columnstore est ajouté à la table pour améliorer les performances du stockage et des requêtes. L’échantillon de 1% du jeu de données des taxis de New York est inséré dans cette table.<br /><br />table dbo. _taxi_models: Utilisé pour rendre persistant le modèle d’analyse avancée formé.|
|**fnCalculateDistance** |fonction scalaire | Calcule la distance directe entre les emplacements Pickup et arrivée. Cette fonction est utilisée dans les [fonctionnalités de création de données](sqldev-create-data-features-using-t-sql.md), de [formation et d’enregistrement d’un modèle](sqldev-train-and-save-a-model-using-t-sql.md) et de [fonctionnement du modèle R](sqldev-operationalize-the-model.md).|
|**fnEngineerFeatures** |fonction table | Crée de nouvelles fonctionnalités de données pour l’apprentissage du modèle. Cette fonction est utilisée dans les [fonctionnalités de création de données](sqldev-create-data-features-using-t-sql.md) et de [fonctionnement du modèle R](sqldev-operationalize-the-model.md).|


Les procédures stockées sont créées à l’aide du script R et Python qui se trouvent dans différents didacticiels. Le tableau suivant récapitule les procédures stockées que vous pouvez éventuellement ajouter à la base de données de démonstration des taxis de New York quand vous exécutez un script à partir de différentes leçons.

|**Procédure stockée**|**Langage**|**Description**|
|-------------------------|------------|---------------|
|**RxPlotHistogram** |R | Appelle la fonction RevoScaleR rxHistogram pour tracer l’histogramme d’une variable, puis retourne le tracé sous la forme d’un objet binaire. Cette procédure stockée est utilisée dans [Explorer et visualiser les données](sqldev-explore-and-visualize-the-data.md).|
|**RPlotRHist** |R| Crée un graphique à l’aide de la fonction hist et enregistre la sortie sous la forme d’un fichier PDF local. Cette procédure stockée est utilisée dans [Explorer et visualiser les données](sqldev-explore-and-visualize-the-data.md).|
|**RxTrainLogitModel**  |R| Forme un modèle de régression logistique en appelant un package R. Le modèle prédit la valeur de la colonne tipped et est formé à l’aide d’un échantillon de 70 % des données sélectionné de façon aléatoire. La sortie de la procédure stockée représente le modèle formé, qui est enregistré dans la table nyc_taxi_models. Cette procédure stockée est utilisée dans [former et enregistrer un modèle](sqldev-train-and-save-a-model-using-t-sql.md).|
|**RxPredictBatchOutput**  |R | Appelle le modèle formé pour créer des prédictions à l’aide du modèle. La procédure stockée accepte une requête comme paramètre d’entrée et retourne une colonne de valeurs numériques qui contient les scores pour les lignes d’entrée. Cette procédure stockée est utilisée dans prédire les [résultats potentiels](sqldev-operationalize-the-model.md).|
|**RxPredictSingleRow**  |R| Appelle le modèle formé pour créer des prédictions à l’aide du modèle. Cette procédure stockée accepte une nouvelle observation comme entrée, avec des valeurs de caractéristiques passées comme paramètres inline, et retourne une valeur qui prédit l’issue de la nouvelle observation. Cette procédure stockée est utilisée dans prédire les [résultats potentiels](sqldev-operationalize-the-model.md).|

## <a name="query-the-data"></a>Interroger les données

En guise d’étape de validation, exécutez une requête pour confirmer que les données ont été téléchargées.

1. Dans l’Explorateur d’objets, sous bases de données, cliquez avec le bouton droit sur la base de données **NYCTaxi_Sample** et démarrez une nouvelle requête.

2. Exécuter des requêtes simples:

    ```sql
    SELECT TOP(10) * FROM dbo.nyctaxi_sample;
    SELECT COUNT(*) FROM dbo.nyctaxi_sample;
    ```
La base de données contient 1,7 million lignes.

3. Dans la base de données se trouve une table **nyctaxi_sample** qui contient le jeu de données. La table a été optimisée pour les calculs basés sur des ensembles, avec l’ajout d’un [index ColumnStore](../../relational-databases/indexes/columnstore-indexes-overview.md). Exécutez cette instruction pour générer un résumé rapide sur la table.

    ```sql
    SELECT DISTINCT [passenger_count]
        , ROUND (SUM ([fare_amount]),0) as TotalFares
        , ROUND (AVG ([fare_amount]),0) as AvgFares
    FROM [dbo].[nyctaxi_sample]
    GROUP BY [passenger_count]
    ORDER BY  AvgFares DESC
    ````
Les résultats doivent être similaires à ceux affichés dans la capture d’écran suivante.

  ![Informations récapitulatives sur la table](media/nyctaxidatatablesummary.png "Résultats") de la requête

## <a name="next-steps"></a>Étapes suivantes

Les exemples de données de taxi de New York sont désormais disponibles pour une formation pratique.

+ [En savoir plus sur l’analytique dans la base de données à l’aide de R dans SQL Server](sqldev-in-database-r-for-sql-developers.md)
+ [En savoir plus sur l’analytique dans la base de données à l’aide de Python dans SQL Server](sqldev-in-database-python-for-sql-developers.md)