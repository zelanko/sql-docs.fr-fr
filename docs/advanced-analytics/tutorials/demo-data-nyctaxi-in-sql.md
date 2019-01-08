---
title: Télécharger des données de démonstration NYC Taxi et de scripts pour R et Python - SQL Server Machine Learning incorporés
description: Instructions de téléchargement des exemples de données New York City taxi et de création d’une base de données. Données sont utilisées dans les didacticiels de langage R et SQL Server Python montrant comment incorporer un script dans les procédures stockées SQL Server et des fonctions T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/31/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 25ac1b4884b0d12de9de59f44ba02ac9fec7e952
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645025"
---
# <a name="nyc-taxi-demo-data-for-sql-server-python-and-r-tutorials"></a>Données de démonstration NYC Taxi pour les didacticiels de SQL Server Python et R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article explique comment configurer une base de données exemple constitué de données publiques à partir de la [taxis de New York City et de Limousines Commission](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml). Ces données sont utilisées dans les didacticiels plusieurs R et Python pour l’analytique en base de données sur SQL Server. Pour exécuter l’exemple de code plus rapidement, nous avons créé un échantillon représentatif de 1 % des données. Sur votre système, le fichier de sauvegarde de base de données est légèrement supérieure 90 Mo, fournissant des millions de 1.7 de lignes dans la table de données primaire.

Pour effectuer cet exercice, vous devez disposer [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) ou un autre outil que vous pouvez restaurer un fichier de sauvegarde de base de données et exécuter des requêtes T-SQL.

Didacticiels et guides de démarrage rapide à l’aide de ce jeu de données sont les suivantes :

+ [Découvrez l’analytique en base de données à l’aide de R dans SQL Server](sqldev-in-database-r-for-sql-developers.md)
+ [Découvrez l’analytique en base de données à l’aide de Python dans SQL Server](sqldev-in-database-python-for-sql-developers.md)

## <a name="download-files"></a>Télécharger des fichiers

La base de données est un fichier SQL Server 2016 BAK hébergé par Microsoft. Vous pouvez le restaurer sur SQL Server 2016 et versions ultérieures. Téléchargement de fichiers commence immédiatement lorsque vous cliquez sur le lien. 

Taille du fichier est d’environ 90 Mo.

1. Cliquez sur [NYCTaxi_Sample.bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak) pour télécharger le fichier de sauvegarde de base de données.

2. Copiez le fichier à C:\Program files\Microsoft SQL Server\MSSQL-instance-name\MSSQL\Backup dossier.

3. Dans Management Studio, cliquez sur **bases de données** et sélectionnez **restaurer les fichiers et groupes de fichiers**.

4. Entrez *NYCTaxi_Sample* en tant que le nom de la base de données.

5. Cliquez sur **à partir de l’appareil** , puis ouvrez la page de sélection de fichier pour sélectionner le fichier de sauvegarde. Cliquez sur **ajouter** pour sélectionner NYCTaxi_Sample.bak.

6. Sélectionnez le **restaurer** case à cocher et cliquez sur **OK** pour restaurer la base de données.

## <a name="review-database-objects"></a>Passez en revue les objets de base de données
   
Vérifiez les objets de base de données existent sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de l’instance [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vous devez voir la base de données, les tables, les fonctions et les procédures stockées.
  
   ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")

### <a name="objects-in-nyctaxisample-database"></a>Objets de base de données NYCTaxi_Sample

Le tableau suivant récapitule les objets créés dans la base de données de démonstration NYC Taxi.

|**Nom de l'objet**|**Type d'objet**|**Description**|
|----------|------------------------|---------------|
|**NYCTaxi_Sample** | base de données | Crée une base de données et deux tables :<br /><br />table dbo.nyctaxi_sample : Contient le jeu de données NYC Taxi principal. Un index cluster columnstore est ajouté à la table pour améliorer les performances du stockage et des requêtes. L’exemple de 1 % du jeu de données NYC Taxi est insérée dans cette table.<br /><br />table de dbo.nyc_taxi_models : Utilisée pour conserver le modèle d’analytique avancée formé.|
|**fnCalculateDistance** |fonction scalaire | Calcule la distance directe entre les emplacements de départ et d’arrivée. Cette fonction est utilisée dans [créer des caractéristiques de données](sqldev-create-data-features-using-t-sql.md), [former et enregistrer un modèle](sqldev-train-and-save-a-model-using-t-sql.md) et [Opérationnaliser le modèle R](sqldev-operationalize-the-model.md).|
|**fnEngineerFeatures** |fonction table | Crée de nouvelles fonctionnalités de données d’apprentissage du modèle. Cette fonction est utilisée dans [créer des caractéristiques de données](sqldev-create-data-features-using-t-sql.md) et [Opérationnaliser le modèle R](sqldev-operationalize-the-model.md).|


Procédures stockées sont créées à l’aide de script R et Python dans les didacticiels différents. Le tableau suivant récapitule les procédures stockées que vous pouvez éventuellement ajouter à la base de données de démonstration NYC Taxi lorsque vous exécutez le script à partir de plusieurs leçons.

|**procédure stockée**|**Langage**|**Description**|
|-------------------------|------------|---------------|
|**RxPlotHistogram** |R | Appelle la fonction de rxHistogram RevoScaleR pour tracer l’histogramme d’une variable, puis retourne le tracé en tant qu’objet binaire. Cette procédure stockée est utilisée dans [Explorer et visualiser les données](sqldev-explore-and-visualize-the-data.md).|
|**RPlotRHist** |R| Crée un graphique à l’aide de la fonction de l’historique et enregistre la sortie sous la forme d’un fichier PDF local. Cette procédure stockée est utilisée dans [Explorer et visualiser les données](sqldev-explore-and-visualize-the-data.md).|
|**RxTrainLogitModel**  |R| Effectue l’apprentissage d’un modèle de régression logistique en appelant un package R. Le modèle prédit la valeur de la colonne tipped et est formé à l’aide d’un échantillon de 70 % des données sélectionné de façon aléatoire. La sortie de la procédure stockée représente le modèle formé, qui est enregistré dans la table nyc_taxi_models. Cette procédure stockée est utilisée dans [former et enregistrer un modèle](sqldev-train-and-save-a-model-using-t-sql.md).|
|**RxPredictBatchOutput**  |R | Appelle le modèle formé pour créer des prédictions à l’aide du modèle. La procédure stockée accepte une requête comme paramètre d’entrée et retourne une colonne de valeurs numériques qui contient les scores pour les lignes d’entrée. Cette procédure stockée est utilisée dans [prédire les résultats potentiels](sqldev-operationalize-the-model.md).|
|**RxPredictSingleRow**  |R| Appelle le modèle formé pour créer des prédictions à l’aide du modèle. Cette procédure stockée accepte une nouvelle observation comme entrée, avec des valeurs de caractéristiques passées comme paramètres inline, et retourne une valeur qui prédit l’issue de la nouvelle observation. Cette procédure stockée est utilisée dans [prédire les résultats potentiels](sqldev-operationalize-the-model.md).|

## <a name="query-the-data"></a>Interroger les données

Comme une étape de validation, exécutez une requête pour confirmer que le téléchargement de données.

1. Dans l’Explorateur d’objets, des bases de données, cliquez sur le **NYCTaxi_Sample** de base de données et démarrer une nouvelle requête.

2. Exécutez des requêtes simples :

    ```sql
    SELECT TOP(10) * FROM dbo.nyctaxi_sample;
    SELECT COUNT(*) FROM dbo.nyctaxi_sample;
    ```
La base de données contient 1.7 millions de lignes.

3. Dans la base de données est un **nyctaxi_sample** table qui contient le jeu de données. La table a été optimisée pour les calculs de jeu avec l’ajout d’un [columnstore index](../../relational-databases/indexes/columnstore-indexes-overview.md). Exécutez cette instruction pour générer un résumé rapide sur la table.

    ```sql
    SELECT DISTINCT [passenger_count]
        , ROUND (SUM ([fare_amount]),0) as TotalFares
        , ROUND (AVG ([fare_amount]),0) as AvgFares
    FROM [dbo].[nyctaxi_sample]
    GROUP BY [passenger_count]
    ORDER BY  AvgFares DESC
    ````
Résultats doivent être similaires à celles affichant dans la capture d’écran suivante.

  ![Informations de résumé de la table](media/nyctaxidatatablesummary.png "résultats de la requête")

## <a name="next-steps"></a>Étapes suivantes

Exemples de données NYC Taxi sont désormais disponibles pour une formation pratique.

+ [Découvrez l’analytique en base de données à l’aide de R dans SQL Server](sqldev-in-database-r-for-sql-developers.md)
+ [Découvrez l’analytique en base de données à l’aide de Python dans SQL Server](sqldev-in-database-python-for-sql-developers.md)