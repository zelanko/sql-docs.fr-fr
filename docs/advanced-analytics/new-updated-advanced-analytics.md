---
title: "Mis à jour - Advanced Analytique des documents de SQL Server | Documents Microsoft"
description: "Extraits de l’affichage de contenu mis à jour pour obtenir une documentation récemment modifié dans, pour avancée d’Analytique pour Microsoft SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 07/17/2017
ms.author: genemi
ms.workload: advanced-analytics
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 79f979ecda1ff0851978d19ef28fa3cf909f9a43
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>Nouveaux et mis à jour récemment : Advanced Analytique pour SQL Server



Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Plage de dates des mises à jour :* &nbsp; **23-05-2017** &nbsp; - au - &nbsp; **17-07-2017**
- *Zone de sujet :* &nbsp; **avancées d’Analytique pour SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [Problèmes courants liés à l’exécution du Script externe](common-issues-external-script-execution.md)
2. [Collecte de données pour la résolution des problèmes de l’apprentissage](data-collection-ml-troubleshooting-process.md)
3. [Didacticiels pour SQL Server Python](tutorials/sql-server-python-tutorials.md)
4. [Didacticiels pour SQL Server R](tutorials/sql-server-r-tutorials.md)




&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Consultez plutôt l’article.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-introducing-revoscalepypythonwhat-is-revoscalepymd"></a>1. &nbsp;[Revoscalepy de présentation](python/what-is-revoscalepy.md)

*Mise à jour : 23-06-2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Suivant](#TitleNum_2))

<!-- Source markdown line 112.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 cab7330ac9944508aaa360e00cbc2e866455776d 33f4e0e2421fa79fc11931dc7f29bff4432c6f5a  (PR=2171  ,  Filename=what-is-revoscalepy.md  ,  Dirpath=docs\advanced-analytics\python\  ,  MergeCommitSha40=7d2dbe0bdc4cbd05f11eacf938b35a9c35ace2e7) -->



**À l’aide de revoscalepy avec MicrosoftML**


Les fonctions de Python pour MicrosoftML sont intégrées avec les contextes de calcul et les sources de données qui sont fournies dans revoscalepy. Par conséquent, vous utilisez un algorithme MicrosoftML pour définir et effectuer l’apprentissage d’un modèle dans Python et a les fonctions revoscalepy permet d’exécuter le code Python localement ou dans un contexte de calcul de SQl Server.

Importer uniquement les modules dans votre code Python, puis faire référence aux fonctions individuelles que vous avez besoin.

```
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

**Spécifications**


Pour exécuter le code Python dans SQL Server, vous devez avoir installé SQL Server 2017 avec la fonctionnalité de **Machine Learning Services**et le langage Python. Les versions antérieures de SQL Server ne gèrent pas l’intégration de Python.

> [!NOTE]
> Distributions d’ouvrir la source de Python ne gèrent pas les contextes de calcul de SQL Server. Toutefois, si vous avez besoin de publier et utiliser des applications Python à partir de Windows, vous pouvez installer Microsoft Machine Learning Server sans installation de SQL Server. Pour plus d’informations, voir [créer un serveur de R autonome--... /r/Create-a-Standalone-r-Server.MD)

**Obtenir de l’aide**





&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-step-5-train-and-save-a-model-using-t-sqltutorialssqldev-py5-train-and-save-a-model-using-t-sqlmd"></a>2. &nbsp;[Étape 5 : formation et enregistrer un modèle à l’aide de T-SQL](tutorials/sqldev-py5-train-and-save-a-model-using-t-sql.md)

*Mise à jour : 2017-06-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_1) | [suivant](#TitleNum_3))

<!-- Source markdown line 121.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5c1cbe92282b96105ffdb69efa803f58dc0ac7e2 e4077a2154a90de468c435efa5b2225125d5b0e7  (PR=1904  ,  Filename=sqldev-py5-train-and-save-a-model-using-t-sql.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=dbf91e0d6f8257227cfe8ac6d13c484d0a566f57) -->



1. Dans [ ! INCLUDE [ssManStudio--... /.. /Includes/ssmanstudio-MD.MD)], ouvrez une nouvelle fenêtre de requête et exécutez l’instruction suivante pour créer la procédure stockée _TrainTipPredictionModelRxPy_.  Ce modèle sera basé sur les données d’apprentissage que vous venez de préparer. Étant donné que la procédure stockée contient déjà une définition des données d’entrée, vous n’avez pas besoin de fournir une requête d’entrée.

    ```SQL
    DROP PROCEDURE IF EXISTS TrainTipPredictionModelRxPy;
    GO

    CREATE PROCEDURE [dbo].[TrainTipPredictionModelRxPy] (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script 
      @language = N'Python',
      @script = N'
    import numpy
    import pickle
    import pandas
    from revoscalepy.functions.RxLogit import rx_logit_ex
    
    ## Create a logistic regression model using rx_logit_ex function from revoscalepy package
    logitObj = rx_logit_ex("tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance", data = InputDataSet);
    
    ## Serialize model
    trained_model = pickle.dumps(logitObj)
    ',
    @input_data_1 = N'
    select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, 
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
    from nyctaxi_sample_training
    ',
    @input_data_1_name = N'InputDataSet',
    @params = N'@trained_model varbinary(max) OUTPUT',
    @trained_model = @trained_model OUTPUT;
    ;
    END;
    ```



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-step-6-operationalize-the-modeltutorialssqldev-py6-operationalize-the-modelmd"></a>3. &nbsp;[Étape 6 : rendez le modèle opérationnel](tutorials/sqldev-py6-operationalize-the-model.md)

*Mise à jour : 2017-06-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_2) | [suivant](#TitleNum_4))

<!-- Source markdown line 236.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1eb50ac902d4e80bafb1dd7fdf8f607dcdf0d33f 57d5abdc6119db1ecd81587d625054a5bbfb5fc8  (PR=1904  ,  Filename=sqldev-py6-operationalize-the-model.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=dbf91e0d6f8257227cfe8ac6d13c484d0a566f57) -->



Voici la définition de la procédure stockée qui effectue le calcul de score à l’aide de la **revoscalepy** modèle.

```
CREATE PROCEDURE [dbo].[PredictTipSingleModeRxPy] (@model varchar(50), @passenger_count int = 0,
  @trip_distance float = 0,
  @trip_time_in_secs int = 0,
  @pickup_latitude float = 0,
  @pickup_longitude float = 0,
  @dropoff_latitude float = 0,
  @dropoff_longitude float = 0)
AS
BEGIN
  DECLARE @inquery nvarchar(max) = N'
    SELECT * FROM [dbo].[fnEngineerFeatures-- 
      @passenger_count,
      @trip_distance,
      @trip_time_in_secs,
      @pickup_latitude,
      @pickup_longitude,
      @dropoff_latitude,
      @dropoff_longitude)
    '
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models2 where name = @model);
  EXEC sp_execute_external_script 
    @language = N'Python',
    @script = N'
      import pickle;
      import numpy;
      import pandas;
      from revoscalepy.functions.RxPredict import rx_predict_ex;
```




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-use-python-with-revoscalepy-to-create-a-modeltutorialsuse-python-revoscalepy-to-create-modelmd"></a>4. &nbsp;[Utilisation de Python avec revoscalepy pour créer un modèle](tutorials/use-python-revoscalepy-to-create-model.md)

*Mise à jour : 2017-06-21* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_3))

<!-- Source markdown line 119.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0886939f86fe12d7ff7b339689a02c7fc75e0786 23dd469349a05d535063aab3c14aec152ed2cd7b  (PR=2141  ,  Filename=use-python-revoscalepy-to-create-model.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=76839e39427e24688609353b8708d59fee772d28) -->



**Passez en revue le code**


Nous allons examiner le code et mettre en évidence certaines étapes clés.

**Définition de données source et contexte de calcul**


Il s’agit d’une partie importante de l’utilisation de **revoscalepy** et son package de R connexe **RevoScaleR**. Une source de données est différente à partir d’un contexte de calcul. Le _source de données_ définit les données utilisées dans votre code. Le _contexte de calcul_ définit où le code sera exécuté.

> [!NOTE]
> Prise en charge de certains types de sources de données pris en charge dans RevoScaleR peut-être être limitée dans la version préliminaire. Pour plus d’informations sur les fonctions disponibles dans la dernière version, consultez la rubrique [What revoscalepy--... /Python/What-is-revoscalepy.MD).

Global traiter pour la création et à l’aide d’une source de données et calcul de contexte est la suivante :

1. Créez des variables de Python, tel que _sqlQuery_ et _connectionString_, qui définissent la source et les données que vous souhaitez utiliser. Passer ces variables à la **RxSqlServerData** constructeur pour implémenter le **objet source de données** nommé _source de données_.
2. Créer un objet de contexte de calcul à l’aide de la **RxInSqlServer** constructeur. Dans cet exemple, vous passez la chaîne de connexion que vous avez défini précédemment, en supposant que les données sont sur la même instance de SQL Server que vous utiliserez comme contexte de calcul. Toutefois, la source de données et le contexte de calcul peut être sur des serveurs différents. Résultant **objet de contexte de calcul** est nommé _computeContext_.
3. Choisissez le contexte de calcul active. Par défaut, les opérations sont exécutées localement, ce qui signifie que si vous ne spécifiez pas un contexte de calcul différentes, les données seront extraites à partir de la source de données, et l’ajustement de modèle s’exécute dans votre environnement actuel de Python.

    Dans RevoScaleR, vous pouvez également utiliser la fonction `rxSetComputeContext` pour basculer entre les contextes de calcul. La fonction n’est pas encore implémentée dans la version d’évaluation **revoscalepy**, mais vous pouvez spécifier le contexte de calcul en tant qu’argument à **rx_lin_mod_ex**.





<a name="similars2"/>

&nbsp;

## <a name="similar-articles"></a>Articles similaires

Cette section liste les articles très similaires récemment mis à jour dans d’autres zones de sujet, dans le même dépôt GitHub.com : [MicrosoftDocs/**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/).

<!--  20170717-1101  -->

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Zones de sujet avec des articles nouveaux ou mis à jour récemment

- [Nouveaux + Mis à jour (4 + 4) : **Analyse avancée pour SQL** (documentation)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveaux + Mis à jour (2 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveaux + Mis à jour (1 + 2) : **Connexion à SQL** (documentation)](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (6 + 0) : **Moteur de base de données pour SQL** (documentation)](../database-engine/new-updated-database-engine.md)
- [Nouveaux + Mis à jour (13 + 2) : **Linux pour SQL** (documentation)](../linux/new-updated-linux.md)
- [Nouveaux + Mis à jour (1 + 0) : **MDS (Master Data Services) pour SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (1 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (8 + 4) : **Bases de données relationnelles pour SQL** (documentation)](../relational-databases/new-updated-relational-databases.md)
- [Nouveaux + Mis à jour (2 + 2) : **Microsoft SQL Server** (documentation)](../sql-server/new-updated-sql-server.md)
- [Nouveaux + Mis à jour (0 + 1) : **SQL Server Management Studio (SSMS)** (documentation)](../ssms/new-updated-ssms.md)
- [Nouveaux + Mis à jour (1 + 0) : **Transact-SQL** (documentation)](../t-sql/new-updated-t-sql.md)
- [Nouveaux + Mis à jour (1 + 0) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)


#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Zones de sujet sans article nouveau ou mis à jour récemment

- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Integration Services pour SQL** (documentation)](../integration-services/new-updated-integration-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (0 + 0) : **Reporting Services pour SQL** (documentation)](../reporting-services/new-updated-reporting-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveaux + Mis à jour (0 + 0) : **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveaux + Mis à jour (0 + 0) : **SQL Server Migration Assistant (SSMA)** (documentation)](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)


&nbsp;


