---
title: Créer des workflows SSIS et SSRS avec R
description: Les scénarios d’intégration combinant SQL Server Machine Learning Services et R services, Reporting Services (SSRS) et SQL Server Integration Services (SSIS).
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/17/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 2b8d55e95991437e4d76911fd26afb5b1bc9c550
ms.sourcegitcommit: 1c3f56deaa4c1ffbe5d7f75752ebe10447c3e7af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "68715174"
---
# <a name="create-ssis-and-ssrs-workflows-with-r-on-sql-server"></a>Créer des flux de travail SSIS et SSRS avec R sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article explique comment utiliser le script R et Python incorporé à l’aide du langage et des fonctionnalités de science des données de SQL Server Machine Learning Services avec deux fonctionnalités de SQL Server importantes: SQL Server Integration Services (SSIS) et SQL Server Reporting Services SSRS. Les bibliothèques R et Python dans SQL Server fournissent des fonctions statistiques et prédictives. SSIS et SSRS fournissent respectivement des visualisations et une transformation ETL coordonnées. Cet article explique comment rassembler toutes ces fonctionnalités dans ce modèle de flux de travail:

> [!div class="checklist"]
> * Créer une procédure stockée contenant un exécutable R ou python
> * Exécuter la procédure stockée à partir de SSIS ou de SSRS

Les exemples de cet article concernent essentiellement R et SSIS, mais les concepts et les étapes s’appliquent également à python. La deuxième section fournit des conseils et des liens pour les visualisations SSRS.

<a name="bkmk_ssis"></a> 

## <a name="use-ssis-for-automation"></a>Utiliser SSIS pour l’automatisation

Les workflows de science des données sont hautement itératifs et impliquent beaucoup de transformations de données, notamment la mise à l'échelle, les agrégations, le calcul des probabilités, le renommage et la fusion des attributs. Les scientifiques des données sont habitués à effectuer une grande partie de ces tâches dans R, Python ou un autre langage, mais l’exécution de ces flux de travail sur des données d’entreprise nécessite une intégration transparente avec les outils et processus ETL.

Étant [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] donné que vous permet d’exécuter des opérations complexes dans R via des procédures stockées et Transact-SQL, vous pouvez intégrer des tâches de science des données à des processus ETL existants. Au lieu d’effectuer une chaîne de tâches gourmandes en mémoire, la préparation des données peut être optimisée à l' [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] aide [!INCLUDE[tsql](../../includes/tsql-md.md)]des outils les plus efficaces, y compris et. 

Voici quelques idées sur la façon dont vous pouvez automatiser le traitement des données et les pipelines de modélisation à l’aide [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]de:

+ Extraire des données à partir de sources locales ou Cloud pour créer des données d’apprentissage 
+ Générer et exécuter des modèles R ou python dans le cadre d’un flux de travail d’intégration de données
+ Reformer les modèles sur une base régulière (planifiée)
+ Chargez les résultats du script R ou python dans d’autres destinations, comme Excel, Power BI, Oracle et Teradata, pour n’en nommer que quelques-uns.
+ Utiliser des tâches SSIS pour créer des fonctionnalités de données dans la base de données SQL
+ Utiliser la branche conditionnelle pour basculer le contexte de calcul pour les travaux R et Python

## <a name="ssis-example"></a>Exemple SSIS

L’exemple suivant provient d’un billet de blog MSDN maintenant mis hors service créé par Jimmy Wong à l’adresse suivante:`https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/`

Cet exemple vous montre comment automatiser des tâches à l’aide de SSIS. Vous créez des procédures stockées avec R incorporé à l’aide de SQL Server Management Studio, puis vous exécutez ces procédures stockées à partir des [tâches exécuter T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) dans un package SSIS.

Pour effectuer un pas à pas détaillé dans cet exemple, vous devez connaître Management Studio, SSIS, concepteur SSIS, conception de package et T-SQL. Le package SSIS utilise trois [tâches exécuter T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) qui insèrent des données d’apprentissage dans une table, modélisent les données et notent les données pour obtenir une sortie de prédiction.

### <a name="load-training-data"></a>Charger les données d’apprentissage

Exécutez le script suivant dans SQL Server Management Studio pour créer une table pour le stockage des données. Vous devez créer et utiliser une base de données de test pour cet exercice. 

```T-SQL
Use test-db
GO

Create table ssis_iris (
    id int not null identity primary key
    , "Sepal.Length" float not null, "Sepal.Width" float not null
    , "Petal.Length" float not null, "Petal.Width" float not null
    , "Species" varchar(100) null
);
GO
```

Créer une procédure stockée qui charge les données d’apprentissage dans une trame de données. Cet exemple utilise le jeu de données Iris intégré. 

```T-SQL
Create procedure load_iris
as
begin
    execute sp_execute_external_script
        @language = N'R'
        , @script = N'iris_df <- iris;'
        , @input_data_1 = N''
        , @output_data_1_name = N'iris_df'
    with result sets (("Sepal.Length" float not null, "Sepal.Width" float not null, "Petal.Length" float not null, "Petal.Width" float not null, "Species" varchar(100)));
end;
```

Dans le concepteur SSIS, créez une [tâche d’exécution SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) qui exécute la procédure stockée que vous venez de définir. Le script pour **SQLStatement** supprime les données existantes, spécifie les données à insérer, puis appelle la procédure stockée pour fournir les données.

```T-SQL
truncate table ssis_iris;
insert into ssis_iris("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
exec dbo.load_iris;
```

![Insérer des données](../media/create-workflows-using-r-in-sql-server/ssis-exec-sql-insert-data.png "Insérer des données")

### <a name="generate-a-model"></a>Générer un modèle

Exécutez le script suivant dans SQL Server Management Studio pour créer une table qui stocke un modèle. 

```T-SQL
Use test-db
GO

Create table ssis_iris_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
GO
```

Créez une procédure stockée qui génère un modèle linéaire à l’aide de [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod). Les bibliothèques RevoScaleR et revoscalepy sont automatiquement disponibles dans les sessions R et Python sur SQL Server et il n’est donc pas nécessaire d’importer la bibliothèque.

```T-SQL
Create procedure generate_iris_rx_model
as
begin
    execute sp_execute_external_script
        @language = N'R'
        , @script = N'
          irisLinMod <- rxLinMod(Sepal.Length ~ Sepal.Width + Petal.Length + Petal.Width + Species, data = ssis_iris);
          trained_model <- data.frame(payload = as.raw(serialize(irisLinMod, connection=NULL)));'
        , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" from ssis_iris'
        , @input_data_1_name = N'ssis_iris'
        , @output_data_1_name = N'trained_model'
    with result sets ((model varbinary(max)));
end;
GO
```

Dans le concepteur SSIS, créez une [tâche d’exécution SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) pour exécuter la procédure stockée **generate_iris_rx_model** . Le modèle est sérialisé et enregistré dans la table ssis_iris_models. Le script pour **SQLStatement** est le suivant:

```T-SQL
insert into ssis_iris_models (model)
exec generate_iris_rx_model;
update ssis_iris_models set model_name = 'rxLinMod' where model_name = 'default model';
```

![Génère un modèle linéaire](../media/create-workflows-using-r-in-sql-server/ssis-exec-rxlinmod.png "Génère un modèle linéaire")

En tant que point de contrôle, une fois cette tâche terminée, vous pouvez interroger le ssis_iris_models pour voir qu’il contient un modèle binaire.

### <a name="predict-score-outcomes-using-the-trained-model"></a>Résultats de prédiction (score) à l’aide du modèle «formé»

Maintenant que vous avez du code qui charge les données d’apprentissage et génère un modèle, la seule étape restante consiste à utiliser le modèle pour générer des prédictions. 

Pour ce faire, placez le script R dans la requête SQL pour déclencher la fonction R intégrée [rxPredict](https://docs.microsoft.com//machine-learning-server/r-reference/revoscaler/rxpredict) sur ssis_iris_model. Une procédure stockée appelée **predict_species_length** effectue cette tâche.

```T-SQL
Create procedure predict_species_length (@model varchar(100))
as
begin
    declare @rx_model varbinary(max) = (select model from ssis_iris_models where model_name = @model);
    -- Predict based on the specified model:
    exec sp_execute_external_script
        @language = N'R'
        , @script = N'
irismodel <-unserialize(rx_model);
irispred <- rxPredict(irismodel, ssis_iris[,2:6]);
OutputDataSet <- cbind(ssis_iris[1], irispred$Sepal.Length_Pred, ssis_iris[2]);
colnames(OutputDataSet) <- c("id", "Sepal.Length.Actual", "Sepal.Length.Expected");
#OutputDataSet <- subset(OutputDataSet, Species.Length.Actual != Species.Expected);
'
    , @input_data_1 = N'
    select id, "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" from ssis_iris
    '
    , @input_data_1_name = N'ssis_iris'
    , @params = N'@rx_model varbinary(max)'
    , @rx_model = @rx_model
    with result sets ( ("id" int, "Species.Length.Actual" float, "Species.Length.Expected" float)
        );
end;
```

Dans le concepteur SSIS, créez une [tâche d’exécution SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) qui exécute la procédure stockée **predict_species_length** pour générer une longueur de pétale prédite.

```T-SQL
exec predict_species_length 'rxLinMod';
```

![Générer](../media/create-workflows-using-r-in-sql-server/ssis-exec-predictions.png "Générer des prédictions")

### <a name="run-the-solution"></a>Exécuter la solution

Dans le concepteur SSIS, appuyez sur F5 pour exécuter le package. Vous devez voir un résultat similaire à la capture d’écran suivante.

![F5 pour s’exécuter en mode débogage](../media/create-workflows-using-r-in-sql-server/ssis-exec-F5-run.png "F5 pour s’exécuter en mode débogage")

<a name="bkmk_ssrs"></a> 

## <a name="use-ssrs-for-visualizations"></a>Utiliser SSRS pour les visualisations

Bien que R puisse créer des graphiques et des visualisations intéressantes, il n’est pas bien intégré avec des sources de données externes, ce qui signifie que chaque graphique ou graphique doit être produit individuellement. Le partage peut également être difficile.

À l' [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]aide de, vous pouvez exécuter des opérations complexes [!INCLUDE[tsql](../../includes/tsql-md.md)] dans R via des procédures stockées, qui peuvent facilement être utilisées par divers outils de création [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de rapports d’entreprise, y compris et Power bi.

### <a name="ssrs-example"></a>Exemple SSRS

[Appareil graphique R pour Microsoft Reporting Services (SSRS)](https://rgraphicsdevice.codeplex.com/)

Ce projet CodePlex fournit le code pour vous aider à créer un élément de rapport personnalisé qui restitue la sortie graphique de R sous la forme d’une image [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui peut être utilisée dans les rapports.  Avec l’élément de rapport personnalisé, vous pouvez :

+ Publier des graphiques et tracés créés à l’aide du périphérique graphique de R dans les tableaux de bord [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]

+ Passer des paramètres [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aux tracés R

> [!NOTE]
> Pour cet exemple, le code qui prend en charge le périphérique graphique R pour Reporting Services doit être installé sur le serveur Reporting Services, ainsi que dans Visual Studio. Vous devez également effectuer manuellement la configuration et la compilation.

## <a name="next-steps"></a>Étapes suivantes

Les exemples SSIS et SSRS de cet article illustrent deux cas d’exécution de procédures stockées qui contiennent un script R ou python incorporé. Le principal avantage est que vous pouvez rendre le script R ou python disponible pour n’importe quelle application ou outil pouvant envoyer une demande d’exécution sur une procédure stockée. Un autre recours pour SSIS est que vous pouvez créer des packages qui automatisent et planifient une grande variété d’opérations, telles que l’acquisition de données, le nettoyage, la manipulation, etc., avec la fonctionnalité de science des données R ou python incluse dans la chaîne d’opérations. Pour plus d’informations et d’idées, consultez [fonctionnement du code R à l’aide de procédures stockées dans SQL Server machine learning services](operationalizing-your-r-code.md).