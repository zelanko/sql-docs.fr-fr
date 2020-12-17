---
title: Package R RevoScaleR
description: RevoScaleR est un package R de Microsoft qui prend en charge les traitements distribués, les contextes de calcul distants et des algorithmes de science des données hautes performances. Il gère également l’importation de données, la transformation de données, les résumés, la visualisation et l’analyse. Il est inclus dans SQL Server Machine Learning Services et dans SQL Server 2016 R Services.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 07/14/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: 87d4fbcfa114b9f80f19495b3d3728c2dd7678ac
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470830"
---
# <a name="revoscaler-r-package-in-sql-server-machine-learning-services"></a>RevoScaleR (package R de SQL Server Machine Learning Services)

[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

**RevoScaleR** est un package R de Microsoft qui prend en charge les traitements distribués, les contextes de calcul distants et des algorithmes de science des données hautes performances. Il gère également l’importation de données, la transformation de données, les résumés, la visualisation et l’analyse. Il est inclus dans [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) et dans [SQL Server 2016 R Services](sql-server-r-services.md).

Contrairement aux fonctions R de base, les opérations RevoScaleR peuvent être effectuées sur des jeux de données volumineux, en parallèle et sur des systèmes de fichiers distribués. Les fonctions peuvent être utilisées sur des jeux de données trop volumineux pour la mémoire, grâce à la segmentation et au réassemblage des résultats lorsque les opérations sont terminées.

Les fonctions RevoScaleR sont associées à un préfixe rx** ou **Rx** pour faciliter leur identification.

RevoScaleR sert de plateforme pour la science des données distribuée. Par exemple, vous pouvez utiliser les transformations et les contextes de calcul RevoScaleR avec les algorithmes de pointe dans [MicrosoftML](/machine-learning-server/r/concept-what-is-the-microsoftml-package). Vous pouvez également utiliser [rxExec](/machine-learning-server/r-reference/revoscaler/rxexec) pour exécuter des fonctions R de base en parallèle.

## <a name="full-reference-documentation"></a>Documentation de référence complète

Le package **RevoScaleR** est distribué dans plusieurs produits Microsoft, mais l’utilisation est la même quelle que soit sa provenance (SQL Server ou un autre produit). Étant donné que les fonctions sont les mêmes, la [documentation de chaque fonction RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) est publiée au même endroit sous la [référence R](/machine-learning-server/r-reference/introducing-r-server-r-package-reference) pour Microsoft Machine Learning Server. Si des comportements spécifiques à un produit existent, les différences seront signalées dans la page d’aide de la fonction.

## <a name="versions-and-platforms"></a>Versions et plateformes

Le package **RevoScaleR** s’appuie sur R 3.4.3 et n’est disponible que si l’un des produits ou téléchargements Microsoft suivants est installé :

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
+ [Services de Machine Learning SQL Server](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 ou version ultérieure](/machine-learning-server/)
+ [Microsoft R Client](set-up-a-data-science-client.md)

> [!NOTE]
> Les versions complètes du produit sont uniquement disponibles sous Windows dans SQL Server 2017. Windows et Linux sont pris en charge pour **RevoScaleR** dans [SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="functions-by-category"></a>Fonctions par catégorie

Cette section répertorie les fonctions par catégorie pour vous donner une idée de la façon dont chacune d’elles est utilisée. Vous pouvez également utiliser la [table des matières](/machine-learning-server/r-reference/introducing-r-server-r-package-reference) pour rechercher des fonctions dans l’ordre alphabétique.

## <a name="1-data-source-and-compute"></a>1-Source de données et calcul

**RevoScaleR** comprend des fonctions permettant de créer des sources de données et de définir l’emplacement, ou *contexte de calcul*, où les calculs sont effectués. Un objet source de données est un conteneur qui spécifie une chaîne de connexion assortie du jeu de données de votre choix, défini sous la forme d’une table, d’une vue ou d’une requête. Les appels aux procédures stockées ne sont pas pris en charge. Les fonctions relatives aux scénarios SQL Server sont répertoriées dans le tableau ci-dessous.

Dans certains cas, SQL Server et R utilisent des types de données différents. Pour obtenir la liste des mappages entre les types de données SQL et R, consultez [Types de données R vers SQL](r-libraries-and-data-types.md).

| Fonction| Description|
| ------- | ---------- |
| [RxInSqlServer](/machine-learning-server/r-reference/revoscaler/rxinsqlserver) |  Créez un objet de contexte de calcul SQL Server pour envoyer des calculs à une instance distante. Plusieurs fonctions **RevoScaleR** prennent le contexte de calcul comme argument. |
|[rxGetComputeContext / rxSetComputeContext](/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) | Obtenez ou définissez le contexte de calcul actif. |
| [RxSqlServerData](/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) | Créez un objet de données basé sur une requête ou une table SQL Server. |
| [RxOdbcData](/machine-learning-server/r-reference/revoscaler/rxodbcdata) | Créez une source de données basée sur une connexion ODBC. |
| [RxXdfData](/machine-learning-server/r-reference/revoscaler/rxxdfdata) | Créez une source de données basée sur un fichier XDF local. Les fichiers XDF sont souvent utilisés pour décharger les données en mémoire sur le disque. Un fichier XDF peut être utile quand la quantité des données utilisées est trop importante pour être transférée en un seul lot à partir de la base de données ou pour tenir dans la mémoire. Par exemple, si vous déplacez régulièrement de grandes quantités de données d’une base de données vers une station de travail locale, plutôt que d’interroger de façon répétée la base de données à chaque opération R, vous pouvez vous servir du fichier XDF comme cache pour enregistrer les données localement et les exploiter ensuite dans votre espace de travail R.|

> [!TIP]
> Si vous débutez avec les sources de données ou les contextes de calcul, nous vous recommandons de commencer par vous renseigner sur le [calcul distribué](/machine-learning-server/r/how-to-revoscaler-distributed-computing) dans la documentation de Microsoft Machine Learning Server.

### <a name="perform-ddl-statements"></a>Exécuter des instructions DDL

Vous pouvez exécuter des instructions DDL à partir de R, à condition de disposer des autorisations nécessaires au niveau de l’instance et de la base de données. Les fonctions suivantes utilisent des appels ODBC pour exécuter des instructions DDL ou récupérer le schéma de la base de données.

| Fonction| Description|
| ------- | ---------- |
| [rxSqlServerTableExists et rxSqlServerDropTable](/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) | Déposez une table [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ou vérifiez s’il existe une table ou un objet de base de données. |
| [rxExecuteSQLDDL](/machine-learning-server/r-reference/revoscaler/rxexecutesqlddl) | Exécutez une commande DDL (Data Definition Language) qui définit ou manipule des objets de base de données. Cette fonction ne peut pas renvoyer de données et est utilisée uniquement pour récupérer ou modifier le ou les métadonnées ou le schéma de l’objet.|

## <a name="2-data-manipulation-etl"></a>2-Manipulation de données (ETL)

Après avoir créé un objet de source de données, vous pouvez l’utiliser pour y charger des données, transformer des données ou écrire de nouvelles données dans la destination spécifiée. Selon la taille des données contenues dans la source, vous pouvez aussi définir la taille de lot dans la source de données et déplacer des données en blocs.

| Fonction | Description |
|----------|-------------|
| [rxOpen-methods](/machine-learning-server/r-reference/revoscaler/rxopen-methods) | Vérifiez si une source de données est disponible, ouvrez ou fermez une source de données, lisez des données à partir d’une source, écrivez des données dans la cible et fermez une source de données.|
| [rxImport](/machine-learning-server/r-reference/revoscaler/rximport) | Déplacez des données d’une source de données vers un stockage de fichiers ou dans une trame de données.|
| [rxDataStep](/machine-learning-server/r-reference/revoscaler/rxdatastep) | Transformez les données lors de leur déplacement entre des sources de données.|

<a name="graphing-functions"></a>

## <a name="3-graphing-functions"></a>3-Fonctions graphiques

| Nom de la fonction | Description |
|---------------|-------------|
|[rxHistogram](/machine-learning-server/r-reference/revoscaler/rxhistogram)  |Crée un histogramme à partir des données. | 
|[rxLinePlot](/machine-learning-server/r-reference/revoscaler/rxlineplot) |Crée un tracé en ligne à partir des données. | 
|[rxLorenz](/machine-learning-server/r-reference/revoscaler/rxlorenz)  |Calcule une courbe de Lorenz, qui peut être tracée. | 
|[rxRocCurve](/machine-learning-server/r-reference/revoscaler/rxroc)  |Calcule et trace des courbes ROC à partir de données réelles et prévues. | 

<a name="statistics-functions"></a>

## <a name="4-descriptive-statistics"></a>4-Statistiques descriptives

| Nom de la fonction | Description |
|---------------|-------------|
|[rxQuantile](/machine-learning-server/r-reference/revoscaler/rxquantile) <sup>*</sup> |Calcule l’étendue approximative des fichiers et des trames de données .xdf sans effectuer de tri. | 
|[rxSummary](/machine-learning-server/r-reference/revoscaler/rxsummary) <sup>*</sup> |Statistiques de base sur les données, y compris des calculs par groupe. L’écriture par les calculs par groupe dans le fichier .xdf n’est pas prise en charge. | 
|[rxCrossTabs](/machine-learning-server/r-reference/revoscaler/rxcrosstabs) <sup>*</sup> |Tableau croisé de données basé sur des formules. | 
|[rxCube](/machine-learning-server/r-reference/revoscaler/rxcube) <sup>*</sup> |Tableau croisé alternatif basé sur des formules, conçu pour une représentation efficace qui renvoie des résultats de cube. L’écriture de la sortie dans le fichier .xdf n’est pas prise en charge. | 
|[rxMarginals](/machine-learning-server/r-reference/revoscaler/rxmarginals)  |Résumés marginaux des tableaux croisés. | 
|[as.xtabs](/machine-learning-server/r-reference/revoscaler/as.xtabs)  |Convertit les résultats d’un tableau croisé en objet xtabs. | 
|[rxChiSquaredTest](/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Effectue un test de Khi-deux sur un objet xtabs. Utilisé avec les petits jeux de données et ne segmente pas les données. | 
|[rxFisherTest](/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Effectue un test exact de Fisher sur un objet xtabs. Utilisé avec les petits jeux de données et ne segmente pas les données. | 
|[rxKendallCor](/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Calcule le Tau de Kendall à l’aide d’un objet xtabs. | 
|[rxPairwiseCrossTab](/machine-learning-server/r-reference/revoscaler/rxpairwisecrosstab)  |Appliquez une fonction à des combinaisons par paires de ligne et de colonnes d’un objet xtabs. | 
|[rxRiskRatio](/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Calculez le risque relatif sur un objet xtabs deux par deux. | 
|[rxOddsRatio](/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Calculez le ratio de probabilités sur un objet xtabs deux par deux. | 

<sup>*</sup> Désigne les fonctions les plus populaires de cette catégorie.

<a name="prediction-functions"></a>

## <a name="5-prediction-functions"></a>5-Fonctions de prédiction

| Nom de la fonction | Description |
|---------------|-------------|
|[rxLinMod](/machine-learning-server/r-reference/revoscaler/rxlinmod) <sup>*</sup> |Associe un modèle linéaire aux données. | 
|[rxLogit](/machine-learning-server/r-reference/revoscaler/rxlogit) <sup>*</sup> |Associe un modèle de régression logistique aux données. | 
|[rxGlm](/machine-learning-server/r-reference/revoscaler/rxglm) <sup>*</sup> |Associe un modèle linéaire généralisé aux données. | 
|[rxCovCor](/machine-learning-server/r-reference/revoscaler/rxcovcor) <sup>*</sup> |Calculez la covariance, la corrélation ou la somme de matrices carrées / produit vectoriel pour un ensemble de variables. | 
|[rxDTree](/machine-learning-server/r-reference/revoscaler/rxdtree) <sup>*</sup> |Associe un arbre de régression ou de classification aux données. | 
|[rxBTrees](/machine-learning-server/r-reference/revoscaler/rxbtrees) <sup>*</sup> |Associe une forêt de décision de classification ou de régression aux données à l’aide d’un algorithme de boosting du gradient stochastique. | 
|[rxDForest](/machine-learning-server/r-reference/revoscaler/rxdforest) <sup>*</sup> |Associe une forêt de décision de régression ou de classification aux données. | 
|[rxPredict](/machine-learning-server/r-reference/revoscaler/rxPredict) <sup>*</sup> |Calcule les prévisions pour les modèles associés. La sortie doit être une source de données XDF. | 
|[rxKmeans](/machine-learning-server/r-reference/revoscaler/rxkmeans) <sup>*</sup> |Exécute un clustering K-means. | 
|[rxNaiveBayes](/machine-learning-server/r-reference/revoscaler/rxnaivebayes) <sup>*</sup> |Exécute la classification Naive Bayes. | 
|[rxCov](/machine-learning-server/r-reference/revoscaler/rxcovcor) |Calculez la matrice de covariance pour un ensemble de variables. | 
|[rxCor](/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Calculez la matrice de corrélation pour un ensemble de variables. | 
|[rxSSCP](/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Calculez la somme de matrices carrées/de produit vectoriel pour un ensemble de variables. | 
|[rxRoc](/machine-learning-server/r-reference/revoscaler/rxroc)  |Calculs du ROC (Receiver Operating Characteristic) à l’aide des valeurs réelles et prévues à partir d’un système classifieur binaire. | 

<sup>*</sup> Désigne les fonctions les plus populaires de cette catégorie.


## <a name="how-to-work-with-revoscaler"></a>Procédure d'utilisation de RevoScaleR

Les fonctions de **RevoScaleR** peuvent être appelées dans du code R encapsulé dans des procédures stockées. La plupart des développeurs créent des solutions **RevoScaleR** localement, puis migrent le code R terminé vers les procédures stockées en guise d’exercice de déploiement.

Lors d’une exécution locale, vous exécutez généralement un script R à partir de la ligne de commande, ou à partir d’un environnement de développement R, et vous spécifiez un contexte de calcul SQL Server à l’aide de l’une des fonctions **RevoScaleR**. Vous pouvez utiliser le contexte de calcul distant pour l’intégralité du code, ou pour des fonctions individuelles. Par exemple, vous souhaiterez peut-être décharger l’apprentissage du modèle sur le serveur pour utiliser les données les plus récentes et éviter le déplacement des données.

Lorsque vous êtes prêt à encapsuler le script R à l’intérieur d’une procédure stockée, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), nous vous recommandons de réécrire le code sous la forme d’une fonction unique ayant des entrées et des sorties clairement définies. 

## <a name="see-also"></a>Voir aussi

+ [Tutoriels sur R](../tutorials/r-tutorials.md)
+ [En savoir plus sur l’utilisation des contextes de calcul](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R pour les développeurs SQL : apprentissage et fonctionnement d’un modèle](../tutorials/r-taxi-classification-introduction.md)
+ [Exemples de produits Microsoft sur GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [Référence R (Microsoft Machine Learning Server)](/machine-learning-server/r-reference/introducing-r-server-r-package-reference)