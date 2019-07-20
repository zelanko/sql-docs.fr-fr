---
title: Bibliothèque de fonctions R RevoScaleR
description: Présentation de la bibliothèque de fonctions RevoScaleR dans SQL Server 2016 R services et SQL Server 2017 Machine Learning Services avec R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 24c751051ff09fa80e738fc4723a00722b6b2e12
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344528"
---
# <a name="revoscaler-r-library-in-sql-server"></a>RevoScaleR (bibliothèque R dans SQL Server)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**RevoScaleR** est une bibliothèque de fonctions de science des données hautes performances de Microsoft. Les fonctions prennent en charge l’importation des données, la transformation des données, le résumé, la visualisation et l’analyse.

Contrairement aux fonctions R de base, les opérations RevoScaleR peuvent être effectuées sur des jeux de données très volumineux, en parallèle et sur des systèmes de fichiers distribués. Les fonctions peuvent opérer sur des jeux de données qui ne tiennent pas en mémoire en utilisant la segmentation et en réassemblant les résultats lorsque les opérations sont terminées.

Les fonctions RevoScaleR sont dénotées avec un préfixe **RX** ou **RX** pour faciliter leur identification.

RevoScaleR sert de plate-forme pour la science des données distribuées. Par exemple, vous pouvez utiliser les contextes de calcul RevoScaleR et les transformations avec les algorithmes de pointe dans [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package). Vous pouvez également utiliser [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) pour exécuter des fonctions R de base en parallèle.

## <a name="full-reference-documentation"></a>Documentation de référence complète

La bibliothèque **RevoScaleR** est distribuée dans plusieurs produits Microsoft, mais l’utilisation est la même que vous obteniez la bibliothèque dans SQL Server ou un autre produit. Étant donné que les fonctions sont identiques, la [documentation des fonctions RevoScaleR individuelles](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) est publiée dans un seul emplacement sous la [référence R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) pour Microsoft machine learning Server. Si des comportements spécifiques à un produit existent, les différences seront signalées dans la page d’aide de la fonction.

## <a name="versions-and-platforms"></a>Versions et plateformes

La bibliothèque **RevoScaleR** est basée sur R 3.4.3 et n’est disponible que lorsque vous installez l’un des produits ou téléchargements Microsoft suivants:

+ [SQL Server 2016 R services](../install/sql-r-services-windows-install.md)
+ [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 ou version ultérieure](https://docs.microsoft.com/machine-learning-server/)
+ [Client Microsoft R](set-up-a-data-science-client.md)

> [!NOTE]
> Les versions complètes du produit sont uniquement Windows, à partir de SQL Server 2017. La prise en charge de Linux pour **RevoScaleR** est une nouveauté de [SQL Server 2019 Preview](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="functions-by-category"></a>Fonctions par catégorie

Cette section répertorie les fonctions par catégorie pour vous faire une idée de la façon dont chacune d’elles est utilisée. Vous pouvez également utiliser la [table des matières](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) pour rechercher des fonctions dans l’ordre alphabétique.

## <a name="1-data-source-and-compute"></a>1-source de données et calcul

**RevoScaleR** comprend des fonctions permettant de créer des sources de données et de définir l’emplacement, ou le *contexte de calcul*, de l’endroit où les calculs sont effectués. Un objet source de données est un conteneur qui spécifie une chaîne de connexion assortie du jeu de données de votre choix, défini sous la forme d’une table, d’une vue ou d’une requête. Les appels aux procédures stockées ne sont pas pris en charge. Les fonctions relatives aux scénarios de SQL Server sont répertoriées dans le tableau ci-dessous.

Dans certains cas, SQL Server et R utilisent des types de données différents. Pour obtenir la liste des mappages entre les types de données SQL et R, consultez [types de données r-to-SQL](r-libraries-and-data-types.md).

| Fonction| Description|
| ------- | ---------- |
| [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) |  Créez un objet de contexte de calcul SQL Server pour envoyer des calculs à une instance distante. Plusieurs fonctions **RevoScaleR** prennent le contexte de calcul comme argument. |
|[rxGetComputeContext / rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) | Obtient ou définit le contexte de calcul actif. |
| [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) | Créez un objet de données basé sur une requête ou une table SQL Server. |
| [RxOdbcData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxodbcdata) | Créer une source de données basée sur une connexion ODBC. |
| [RxXdfData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxxdfdata) | Créer une source de données basée sur un fichier XDF local. Les fichiers XDF sont souvent utilisés pour décharger les données en mémoire sur le disque. Un fichier XDF peut être utile lors de l’utilisation de plus de données que celles pouvant être transférées à partir de la base de données en un seul lot, ou plus de données que la mémoire ne peut en contenir. Par exemple, si vous déplacez régulièrement de grandes quantités de données d’une base de données vers une station de travail locale, au lieu d’interroger la base de données à plusieurs reprises pour chaque opération R, vous pouvez utiliser le fichier XDF comme un type de cache pour enregistrer les données localement, puis les utiliser dans votre espace de travail R.|

> [!TIP]
> Si vous débutez avec l’idée des sources de données ou des contextes de calcul, nous vous recommandons de commencer avec l' [informatique distribuée](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing) dans la documentation de Microsoft machine learning Server.

### <a name="perform-ddl-statements"></a>Exécuter des instructions DDL

Vous pouvez exécuter des instructions DDL à partir de R, si vous disposez des autorisations nécessaires sur l’instance et la base de données. Les fonctions suivantes utilisent des appels ODBC pour exécuter des instructions DDL ou récupérer le schéma de base de données.

| Fonction| Description|
| ------- | ---------- |
| [rxSqlServerTableExists et rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) | Supprimer une [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] table ou vérifier l’existence d’une table ou d’un objet de base de données. |
| [rxExecuteSQLDDL](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexecutesqlddl) | Exécutez une commande DDL (Data Definition Language) qui définit ou manipule des objets de base de données. Cette fonction ne peut pas retourner de données et est utilisée uniquement pour récupérer ou modifier le ou les métadonnées du schéma ou de l’objet.|

## <a name="2-data-manipulation-etl"></a>2-manipulation de données (ETL)

Après avoir créé un objet de source de données, vous pouvez utiliser l’objet pour y charger des données, transformer des données ou écrire de nouvelles données dans la destination spécifiée. Selon la taille des données contenues dans la source, vous pouvez aussi définir la taille de lot dans la source de données et déplacer des données en blocs.

| Fonction | Description |
|----------|-------------|
| [rxOpen-méthodes](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxopen-methods) | Vérifier si une source de données est disponible, ouvrir ou fermer une source de données, lire des données à partir d’une source, écrire des données dans la cible et fermer une source de données.|
| [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) | Déplacer des données d’une source de données vers un stockage de fichiers ou dans une trame de données.|
| [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) | Transformez les données lors de leur déplacement entre des sources de données.|

<a name="graphing-functions"></a>

## <a name="3-graphing-functions"></a>3-fonctions graphiques

| Nom de la fonction | Description |
|---------------|-------------|
|[rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram)  |Crée un histogramme à partir de données. | 
|[rxLinePlot](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlineplot) |Crée un tracé de ligne à partir de données. | 
|[rxLorenz](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlorenz)  |Calcule une courbe Lorenz qui peut être tracée. | 
|[rxRocCurve](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxroc)  |Calcule et trace des courbes ROC à partir de données réelles et prédites. | 

<a name="statistics-functions"></a>

## <a name="4-descriptive-statistics"></a>4-statistiques descriptives

| Nom de la fonction | Description |
|---------------|-------------|
|[rxQuantile](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxquantile) <sup>*</sup> |Calcule les quantiles approximatives pour les fichiers. XDF et les trames de données sans tri. | 
|[rxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary)<sup>*</sup> |Statistiques de base des données, y compris les calculs par groupe. L’écriture par les calculs de groupe dans le fichier. XDF n’est pas prise en charge. | 
|[rxCrossTabs](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs) <sup>*</sup> |Tableau croisé de données basé sur des formules. | 
|[rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) <sup>*</sup> |Alternative basée sur des formules croisées, conçue pour une représentation efficace retournant des résultats de cube. L’écriture de la sortie dans le fichier. XDF n’est pas prise en charge. | 
|[rxMarginals](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxmarginals)  |Résumés marginaux des tableaux croisés. | 
|[as.xtabs](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/as.xtabs)  |Convertit les résultats de tabulation croisée en objet xtabs. | 
|[rxChiSquaredTest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Effectue un test de khi-deux sur l’objet xtabs. Utilisé avec les petits jeux de données et ne segmente pas les données. | 
|[rxFisherTest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Effectue le test exact de Fisher sur l’objet xtabs. Utilisé avec les petits jeux de données et ne segmente pas les données. | 
|[rxKendallCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Calcule le coefficient de corrélation de classement Tau de Kendall à l’aide de l’objet xtabs. | 
|[rxPairwiseCrossTab](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpairwisecrosstab)  |Appliquez une fonction pour pairer les combinaisons de lignes et de colonnes d’un objet xtabs. | 
|[rxRiskRatio](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Calcule le risque relatif sur un objet xtabs deux par deux. | 
|[rxOddsRatio](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Calcule le ratio de probabilités sur un objet xtabs deux par deux. | 

<sup>*</sup>Désigne les fonctions les plus populaires de cette catégorie.

<a name="prediction-functions"></a>

## <a name="5-prediction-functions"></a>5-fonctions de prédiction

| Nom de la fonction | Description |
|---------------|-------------|
|[rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) <sup>*</sup> |Ajuste un modèle linéaire aux données. | 
|[rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) <sup>*</sup> |Ajuste un modèle de régression logistique aux données. | 
|[rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm) <sup>*</sup> |Ajuste un modèle linéaire généralisé aux données. | 
|[rxCovCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor) <sup>*</sup> |Calculez la covariance, la corrélation ou la somme de la matrice des carrés/produit croisé pour un ensemble de variables. | 
|[rxDTree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree) <sup>*</sup> |Ajuste un arbre de classification ou de régression aux données. | 
|[rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)<sup>*</sup> |Contienne une forêt de décision de classification ou de régression pour les données à l’aide d’un algorithme d’amélioration du gradient stochastique. | 
|[rxDForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest) <sup>*</sup> |Contienne une forêt de décision de classification ou de régression pour les données. | 
|[rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxPredict) <sup>*</sup> |Calcule les prédictions pour les modèles montés. La sortie doit être une source de données XDF. | 
|[rxKmeans](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxkmeans)<sup>*</sup> |Effectue un clustering k-signifiant. | 
|[rxNaiveBayes](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxnaivebayes) <sup>*</sup> |Exécute la classification Naive Bayes. | 
|[rxCov](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor) |Calculez la matrice de covariance pour un ensemble de variables. | 
|[rxCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Calcule la matrice de corrélation pour un ensemble de variables. | 
|[rxSSCP](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Calcule la somme de la matrice des carrés/produit croisé pour un ensemble de variables. | 
|[rxRoc](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxroc)  |Calculs de caractéristiques de fonctionnement du récepteur (ROC) à l’aide des valeurs réelles et prédites du système de classifieur binaire. | 

<sup>*</sup>Désigne les fonctions les plus populaires de cette catégorie.


## <a name="how-to-work-with-revoscaler"></a>Utilisation de RevoScaleR

Les fonctions dans **RevoScaleR** peuvent être appelées dans du code R encapsulé dans des procédures stockées. La plupart des développeurs créent des solutions **RevoScaleR** localement, puis migrez le code R terminé vers les procédures stockées en tant qu’exercice de déploiement.

Lors d’une exécution locale, vous exécutez généralement un script R à partir de la ligne de commande ou d’un environnement de développement R, puis vous spécifiez un SQL Server contexte de calcul à l’aide de l’une des fonctions **RevoScaleR** . Vous pouvez utiliser le contexte de calcul distant pour l’intégralité du code, ou pour des fonctions individuelles. Par exemple, vous souhaiterez peut-être décharger l’apprentissage du modèle sur le serveur pour utiliser les données les plus récentes et éviter le déplacement des données.

Lorsque vous êtes prêt à encapsuler le script R à l’intérieur d’une procédure stockée, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), nous vous recommandons de réécrire le code sous la forme d’une fonction unique ayant des entrées et des sorties clairement définies. 

## <a name="see-also"></a>Voir aussi

+ [Didacticiels R](../tutorials/sql-server-r-tutorials.md)
+ [En savoir plus sur l’utilisation des contextes de calcul](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R pour les développeurs SQL: Apprentissage et fonctionnement d’un modèle](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Exemples de produits Microsoft sur GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [Référence R (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 
