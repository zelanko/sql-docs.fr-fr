---
title: Créer des flux de travail SSIS et de SSRS avec R - Services de SQL Server Machine Learning
description: Scénarios d’intégration combinant SQL Server Machine Learning Services et R Services, Reporting Services (SSRS) et SQL Server Integration Services (SSIS).
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/15/2019
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 76ddf3e3fdb43fea6bb8fd224f8199cda4134b64
ms.sourcegitcommit: e9fcd10c7eb87a4f09ac2d8f7647018e83a5f5c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57976299"
---
# <a name="create-ssis-and-ssrs-workflows-with-r-on-sql-server"></a>Créer des flux de travail SSIS et de SSRS avec R sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article explique comment utiliser des procédures stockées dans les deux fonctionnalités importantes de SQL Server, SQL Server Integration Services (SSIS) et SQL Server Reporting Services SSRS, de façon qui combine des données relationnelles, les fonctions de science des données dans les bibliothèques Microsoft R, et les fonctionnalités BI pour les transformations de données coordonné et de visualisation. Découvrez les fonctionnalités de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] se prêtent à une solution de science des données. Cet article rappelle que code et les données sur SQL Server, telles que le code R incorporé dans les procédures stockées, facilement utilisables dans les visualisations fournies dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].

## <a name="bring-compute-power-to-the-data"></a>Apportez la puissance de calcul aux données

Un objectif de conception de la clé de l’intégration de R et Python avec SQL Server a été de mettre analytique proche des données. Cela présente plusieurs avantages :

+ Sécurité des données. Apportant R plus près à la source de données permet d’éviter le déplacement des données superflues ou non sécurisé.
+ Vitesse. Les bases de données sont optimisées pour les opérations basées sur un jeu. Les innovations récentes dans les bases de données telles que des tables en mémoire rendent des résumés et les agrégations comme l’éclair et sont un parfait complément de science des données.
+ Facilité d’intégration et de déploiement. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est le point central d’opérations pour de nombreuses autres tâches de gestion de données et applications. À l’aide de données qui résident dans la base de données ou d’un entrepôt de création de rapports, vous assurer que les données utilisées par les solutions d’apprentissage sont cohérent et à jour. 
+ Efficacité d’entre cloud et locales. Au lieu de traiter les données dans R, vous pouvez utiliser les pipelines de données d’entreprise, notamment [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et Azure Data Factory. La création de rapports de résultats ou d’analyses est simple dans Power BI ou [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].

En utilisant le bonne combinaison entre SQL et R pour différentes tâches de traitement et d’analyse des données, tant les scientifiques des données que les développeurs peuvent gagner en productivité.

<a name="bkmk_ssis"></a> 

## <a name="use-ssis-for-data-transformation-and-automation"></a>Utiliser SSIS pour l’automatisation et de transformation des données

Les workflows de science des données sont hautement itératifs et impliquent beaucoup de transformations de données, notamment la mise à l'échelle, les agrégations, le calcul des probabilités, le renommage et la fusion des attributs. Les scientifiques des données sont habitués à effectuer une grande partie de ces tâches dans R, Python ou un autre langage, mais l’exécution de ces flux de travail sur des données d’entreprise nécessite une intégration transparente avec les outils et processus ETL.

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] vous permet d’effectuer des opérations complexes dans R avec Transact-SQL et les procédures stockées. Vous pouvez donc intégrer des tâches propres à R avec des processus ETL existants quasiment sans nouveau développement. Plutôt que d’effectuer une chaîne de tâches gourmandes en mémoire dans R, les préparation des données peut être optimisée à l’aide des outils les plus efficaces, y compris [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et [!INCLUDE[tsql](../../includes/tsql-md.md)]. 

Voici quelques idées pour comment vous pouvez automatiser le traitement de vos données et modélisation des pipelines en [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:

+ Utilisez [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] tâches pour créer des caractéristiques de données nécessaires dans la base de données SQL
+ Utiliser le branchement conditionnel afin de changer de contexte de calcul pour les travaux R
+ Exécuter des travaux R qui génèrent leurs propres données dans la base de données et partager ces données avec des applications
+ Lorsque vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], charger le script R enregistré dans une variable de texte et l’exécuter dans SQL Server

## <a name="ssis-example"></a>Exemple SSIS

L’exemple suivant provient d’un billet de blog MSDN mis hors-service maintenant créé par Jimmy Wong à cette URL : `https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/`.

Cet exemple montre comment automatiser des tâches à l’aide de SSIS. Vous créez des procédures stockées avec R incorporé à l’aide de SQL Server Management Studio et puis exécuter ces procédures stockées à partir de [tâches d’exécution T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) dans un package SSIS.

Pour parcourir cet exemple, vous devez connaître avec Management Studio, SSIS, concepteur SSIS, conception du package et T-SQL. Le package SSIS utilise trois [tâches d’exécution T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) qui insérer des données d’apprentissage dans une table les données de modèle et noter les données pour obtenir la sortie de la prédiction.

### <a name="create-tables"></a>Créer des tables

Exécutez le script suivant dans SQL Server Management Studio pour créer quelques tables : un pour stocker les données et l’autre pour stocker un modèle. Le rôle de la table ssis_iris est d’agir en tant que données d’apprentissage dans un scénario d’Opérationnalisation. 

```T-SQL
Use irissql
GO

Create table ssis_iris (
    id int not null identity primary key
    , "Sepal.Length" float not null, "Sepal.Width" float not null
    , "Petal.Length" float not null, "Petal.Width" float not null
    , "Species" varchar(100) null
);
GO

Create table ssis_iris_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
GO
```

### <a name="create-a-stored-procedure-that-loads-training-data"></a>Créer une procédure stockée qui charge les données d’apprentissage

Ce script crée une procédure stockée qui charge Iris dans une trame de données à l’aide de l’ensemble de données R intégré.

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

### <a name="define-an-execute-sql-task-that-refreshes-the-model"></a>Définir une tâche d’exécution SQL qui actualise le modèle

Dans le concepteur SSIS, créez un [tâche d’exécution SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task).

![Insérer des données](../media/create-workflows-using-r-in-sql-server/ssis-exec-sql-insert-data.png "insérer des données")

Le script pour SQLStatement est comme suit. Le script supprime les données existantes, puis recharge à nouveau à l’aide de données le **load_iris** vous avez créé à l’étape précédente de procédure stockée.

```T-SQL
truncate table ssis_iris;
insert into ssis_iris("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
exec dbo.load_iris;
```

### <a name="create-a-stored-procedure-that-generates-a-model"></a>Créer une procédure stockée qui génère un modèle

Cette procédure stockée est le code qui crée un modèle linéaire à l’aide [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod). Bibliothèques RevoScaleR et revoscalepy sont chargés automatiquement dans les sessions R et Python sur SQL Server.

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

### <a name="define-an-execute-sql-task-that-runs-the-model-generation-stored-procedure"></a>Définir une tâche d’exécution SQL qui exécute la procédure stockée de génération de modèle

Dans cette étape, [tâche d’exécution SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) exécute le **generate_iris_rx_model** procédure stockée, création du modèle et leur insertion dans la table ssis_iris_models.

![Génère un modèle linéaire](../media/create-workflows-using-r-in-sql-server/ssis-exec-rxlinmod.png "génère un modèle linéaire")

```T-SQL
insert into ssis_iris_models (model)
exec generate_iris_rx_model;
update ssis_iris_models set model_name = 'rxLinMod' where model_name = 'default model';
```

Une fois cette tâche terminée, vous pouvez interroger le ssis_iris_models pour voir qu’il contient un modèle binaire.

### <a name="predict-score-outcomes-using-the-trained-model"></a>Prédire les résultats (score) à l’aide du modèle « formé »

Dans cet exemple simple, l’hypothèse est que ssis_iris_model est un modèle formé. Étant donné que l’objectif d’un modèle formé est de générer des prédictions, nous sommes désormais prêts exécuter une prédiction à l’utiliser. 

Pour ce faire, placez le script R dans la requête SQL pour déclencher le [rxPredict](https://docs.microsoft.com//machine-learning-server/r-reference/revoscaler/rxpredict) fonction R intégrée sur ssis_iris_model. Une procédure stockée dans SQL Server appelée **predict_species_length** effectue cette tâche.

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

### <a name="define-an-execute-sql-task-that-predicts-outcomes"></a>Définir une tâche d’exécution SQL qui prédit les résultats

À l’aide de [tâche d’exécution SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task), exécutez le **predict_species_length** procédure stockée pour générer la longueur des pétales prédite.

![Générer des prédictions](../media/create-workflows-using-r-in-sql-server/ssis-exec-predictions.png "générer des prédictions")

```T-SQL
exec predict_species_length 'rxLinMod';
```

### <a name="run-the-solution"></a>Exécuter la solution

Dans le concepteur SSIS, appuyez sur F5 pour exécuter le package. Vous devez voir un résultat semblable à la capture d’écran suivante.

![F5 pour exécuter en mode débogage](../media/create-workflows-using-r-in-sql-server/ssis-exec-F5-run.png "F5 pour exécuter en mode débogage")

<a name="bkmk_ssrs"></a> 

## <a name="use-ssrs-for-visualizations"></a>Utiliser SSRS pour les visualisations

R peut créer des graphiques et des visualisations intéressantes, mais il n’est pas très bien intégré avec des sources de données externes, ce qui signifie que chaque diagramme ou graphique doit être produit individuellement. Le partage peut également être difficile.

À l’aide de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], vous pouvez exécuter des opérations complexes dans R avec [!INCLUDE[tsql](../../includes/tsql-md.md)] des procédures stockées, qui peuvent facilement être utilisées par divers outils, y compris de rapports d’entreprise [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et Power BI.

### <a name="ssrs-example"></a>Exemple SSRS

[Périphérique graphique de R de Microsoft Reporting Services (SSRS)](https://rgraphicsdevice.codeplex.com/)

Ce projet CodePlex fournit le code pour vous aider à créer un élément de rapport personnalisé qui restitue la sortie graphique de R en tant qu’image qui peut être utilisée dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] rapports.  Avec l’élément de rapport personnalisé, vous pouvez :

+ Publier des graphiques et tracés créés à l’aide du périphérique graphique de R dans les tableaux de bord [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]

+ Passer des paramètres [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aux tracés R

> [!NOTE]
> Pour cet exemple, le code qui prend en charge le périphérique graphique R pour Reporting Services doit être installé sur le serveur Reporting Services, ainsi que dans Visual Studio. Vous devez également effectuer manuellement la configuration et la compilation.

## <a name="next-steps"></a>Étapes suivantes

Les exemples SSIS et de SSRS dans cet article illustrent les deux cas de l’exécution de procédures stockées contenant le script R ou Python incorporé. Un élément clé à retenir est que vous pouvez proposer script R ou Python à toute application ou un outil qui peut envoyer une demande d’exécution sur une procédure stockée. Un élément à retenir supplémentaire pour SSIS est que vous pouvez créer des packages qui automatisent et planifier un large éventail d’opérations, telles que l’acquisition de données, de nettoyage, de manipulation et ainsi de suite, avec R ou Python fonctionnalité de science de données incluse dans la chaîne des opérations. Pour plus d’informations et des idées, consultez [code R de faire fonctionner à l’aide de procédures stockées dans SQL Server Machine Learning Services](operationalizing-your-r-code.md).