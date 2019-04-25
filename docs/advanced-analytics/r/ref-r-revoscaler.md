---
title: Bibliothèque de fonctions RevoScaleR R - Services de SQL Server Machine Learning
description: Introduction à la bibliothèque de fonctions RevoScaleR dans SQL Server 2016 R Services et SQL Server 2017 Machine Learning Services avec R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 3745c6cd8c340ce4ad89cac84c5b6286126e3f89
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62641931"
---
# <a name="revoscaler-r-library-in-sql-server"></a>RevoScaleR (bibliothèque R dans SQL Server)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**RevoScaleR** est une bibliothèque de fonctions de science des données hautes performances à partir de Microsoft. Fonctions prennent en charge l’importation de données, de transformation des données, de synthèse, de visualisation et d’analyse.

Contrairement aux fonctions de base R, les opérations de RevoScaleR peuvent être exécutées sur des datasets très volumineux, en parallèle et sur les systèmes de fichiers distribués. Fonctions peuvent opérer sur des jeux de données qui ne tiennent pas dans la mémoire à l’aide de segmentation et résultats REASSEMBLAGE lorsque les opérations sont terminées.

Les fonctions RevoScaleR sont signalées par un **rx** ou **Rx** préfixe pour les rendre plus faciles à identifier.

RevoScaleR constitue une plateforme pour la science des données distribuées. Par exemple, vous pouvez utiliser les contextes de calcul RevoScaleR et les transformations avec les algorithmes de pointe dans [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package). Vous pouvez également utiliser [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) pour exécuter des fonctions base R en parallèle.

## <a name="full-reference-documentation"></a>Documentation de référence complète

Le **RevoScaleR** library est distribué dans plusieurs produits Microsoft, mais l’utilisation est la même, si vous obtenez la bibliothèque dans SQL Server ou un autre produit. Étant donné que les fonctions sont les mêmes, [documentation pour les fonctions RevoScaleR individuelles](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) est publié dans un seul emplacement sous la [référence de R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) pour Microsoft Machine Learning Server. Doivent tout propres au produit comportements existent, les différences sont notées dans la page d’aide (fonction).

## <a name="versions-and-platforms"></a>Versions et plateformes

Le **RevoScaleR** bibliothèque est basée sur R 3.4.3 et disponible uniquement lorsque vous installez un des produits Microsoft ou téléchargements suivantes :

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
+ [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 ou version ultérieure](https://docs.microsoft.com/machine-learning-server/)
+ [Microsoft R client](set-up-a-data-science-client.md)

> [!NOTE]
> Les versions de produit complet sont Windows uniquement, en commençant par SQL Server 2017. Prise en charge de Linux pour **RevoScaleR** est une nouveauté de [SQL Server 2019 Preview](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="functions-by-category"></a>Fonctions par catégorie

Cette section répertorie les fonctions par catégorie pour vous donner une idée de l’utilisation de chacun d’eux. Vous pouvez également utiliser le [table des matières](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) pour rechercher des fonctions dans l’ordre alphabétique.

## <a name="1-data-source-and-compute"></a>Calcul et la source de données 1

**RevoScaleR** inclut des fonctions pour la création des sources de données et la définition de l’emplacement, ou *contexte de calcul*, d’où les calculs sont effectués. Un objet source de données est un conteneur qui spécifie une chaîne de connexion assortie du jeu de données de votre choix, défini sous la forme d’une table, d’une vue ou d’une requête. Les appels aux procédures stockées ne sont pas pris en charge. Fonctions liées aux scénarios de SQL Server sont répertoriées dans le tableau ci-dessous.

SQL Server et R utilisent différents types de données dans certains cas. Pour obtenir la liste de mappages entre les types de données SQL et R, consultez [les types de données R-to-SQL](r-libraries-and-data-types.md).

| Fonction| Description|
| ------- | ---------- |
| [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) |  Créer un objet de contexte de calcul de SQL Server pour envoyer des calculs à une instance distante. Plusieurs **RevoScaleR** fonctions acceptent le contexte de calcul en tant qu’argument. |
|[rxGetComputeContext / rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) | Obtient ou définit le contexte de calcul active. |
| [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) | Créer un objet de données basé sur une requête SQL Server ou une table. |
| [RxOdbcData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxodbcdata) | Créer une source de données basée sur une connexion ODBC. |
| [RxXdfData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxxdfdata) | Créer une source de données basée sur un fichier XDF local. Fichiers XDF sont souvent utilisés pour décharger les données en mémoire sur le disque. Un fichier XDF peut être utile lorsque vous travaillez avec plus de données peuvent être transférées à partir de la base de données dans un lot, ou plus de données que peut tenir dans la mémoire. Par exemple, si vous déplacez régulièrement des grandes quantités de données à partir d’une base de données vers une station de travail locale, plutôt que d’interroger la base de données à plusieurs reprises pour chaque opération R, vous pouvez utiliser le fichier XDF comme un type de cache pour enregistrer les données localement et puis les utiliser dans votre espace de travail R.|

> [!TIP]
> Si vous ne connaissez pas l’idée de sources de données ou les contextes de calcul, nous vous recommandons de commencer avec [distributed computing](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing) dans la documentation de Microsoft Machine Learning Server.

### <a name="perform-ddl-statements"></a>Exécuter des instructions DDL

Vous pouvez exécuter des instructions DDL à partir de R, si vous avez les autorisations nécessaires sur l’instance et de la base de données. Les fonctions suivantes utilisent des appels ODBC pour exécuter des instructions DDL ou de récupérer le schéma de base de données.

| Fonction| Description|
| ------- | ---------- |
| [rxSqlServerTableExists et rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) | Supprimer un [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] de table, ou vérifier l’existence d’une table de base de données ou d’un objet. |
| [rxExecuteSQLDDL](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexecutesqlddl) | Exécuter une commande de langage de définition de données (DDL) qui définit ou manipule les objets de base de données. Cette fonction ne peut pas retourner des données et est utilisée uniquement pour récupérer ou modifier le schéma de l’objet ou les métadonnées.|

## <a name="2-data-manipulation-etl"></a>Manipulation de données-2 (ETL)

Après avoir créé un objet de source de données, vous pouvez utiliser l’objet pour charger des données, transformer des données ou écrire de nouvelles données vers la destination spécifiée. Selon la taille des données contenues dans la source, vous pouvez aussi définir la taille de lot dans la source de données et déplacer des données en blocs.

| Fonction | Description |
|----------|-------------|
| [rxOpen-methods](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxopen-methods) | Vérifiez si une source de données est disponible, ouvrez ou fermez une source de données, lire les données à partir d’une source de, écrire des données dans la cible et fermez une source de données.|
| [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) | Déplacer des données à partir d’une source de données dans le stockage de fichiers ou dans une trame de données.|
| [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) | Transformer des données lors de son déplacement entre des sources de données.|

<a name="graphing-functions"></a>

## <a name="3-graphing-functions"></a>Fonctions graphiques de 3

| Nom de la fonction | Description |
|---------------|-------------|
|[rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram)  |Crée un histogramme à partir de données. | 
|[rxLinePlot](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlineplot) |Crée un diagramme en ligne à partir de données. | 
|[rxLorenz](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlorenz)  |Calcule une courbe de Lorenz qui peut être tracée. | 
|[rxRocCurve](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxroc)  |Calcule et trace des courbes ROC à partir des données réelles et prévues. | 

<a name="statistics-functions"></a>

## <a name="4-descriptive-statistics"></a>Statistiques descriptives de 4

| Nom de la fonction | Description |
|---------------|-------------|
|[rxQuantile](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxquantile) <sup>*</sup> |Services de calcul rapprochement de quantiles pour les fichiers .xdf et les trames de données sans effectuer de tri. | 
|[rxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary) <sup>*</sup> |Statistiques de résumé de base de données, y compris des calculs par groupe. Écriture de calculs de groupe à un fichier .xdf ne pas pris en charge. | 
|[rxCrossTabs](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs) <sup>*</sup> |Basé sur la formule de tableau croisé de données. | 
|[rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) <sup>*</sup> |Autre basée sur la formule de tableau croisé conçue pour retourner des résultats de cube une représentation efficace. Écrire la sortie dans le fichier .xdf ne pas pris en charge. | 
|[rxMarginals](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxmarginals)  |Résumés marginal de tableaux à double. | 
|[as.xtabs](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/as.xtabs)  |Convertit les résultats de la zone de liste à un objet xtabs. | 
|[rxChiSquaredTest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Effectue le Test du chi-Squared sur xtabs objet. Utilisé avec petits jeux de données et ne pas découper les données. | 
|[rxFisherTest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Effectue le Test Exact de Fisher sur xtabs objet. Utilisé avec petits jeux de données et ne pas découper les données. | 
|[rxKendallCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Calcule le Coefficient de corrélation de rang Tau de Kendall à l’aide de xtabs objet. | 
|[rxPairwiseCrossTab](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpairwisecrosstab)  |Applique une fonction à des combinaisons par paire de lignes et de colonnes d’un objet xtabs. | 
|[rxRiskRatio](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Calculer le risque relatif sur un objet xtabs de deux par deux. | 
|[rxOddsRatio](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Calculer le ratio de probabilités sur un objet xtabs de deux par deux. | 

<sup>*</sup> Indique les fonctions les plus populaires dans cette catégorie.

<a name="prediction-functions"></a>

## <a name="5-prediction-functions"></a>Fonctions de prédiction de 5

| Nom de la fonction | Description |
|---------------|-------------|
|[rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) <sup>*</sup> |Associe un modèle linéaire aux données. | 
|[rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) <sup>*</sup> |Associe un modèle de régression logistique aux données. | 
|[rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm) <sup>*</sup> |Correspond à un modèle linéaire généralisé aux données. | 
|[rxCovCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor) <sup>*</sup> |Calculer la covariance, la corrélation ou la somme de matrices carrées / produit croisé matrice pour un ensemble de variables. | 
|[rxDTree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree) <sup>*</sup> |Correspond à un arbre de classification ou de régression aux données. | 
|[rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees) <sup>*</sup> |Correspond à une forêt de décision de classification ou de régression pour les données à l’aide d’un stochastique algorithme de gradient boosting. | 
|[rxDForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest) <sup>*</sup> |Correspond à une forêt de décision de classification ou de régression aux données. | 
|[rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxPredict) <sup>*</sup> |Calcule les prévisions pour les modèles. Sortie doit être une source de données XDF. | 
|[rxKmeans](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxkmeans) <sup>*</sup> |Effectue le clustering k-means. | 
|[rxNaiveBayes](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxnaivebayes) <sup>*</sup> |Effectue la classification naïve bayésienne. | 
|[rxCov](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor) |Calculer la matrice de covariance pour un ensemble de variables. | 
|[rxCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Calculer la matrice de corrélation pour un ensemble de variables. | 
|[rxSSCP](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Calculer la somme des carrés / produit croisé matrice pour un ensemble de variables. | 
|[rxRoc](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxroc)  |Calculs de Operating Characteristic (ROC) de récepteur à l’aide des valeurs réelles et prévues à partir du système de classifieur binaire. | 

<sup>*</sup> Indique les fonctions les plus populaires dans cette catégorie.


## <a name="how-to-work-with-revoscaler"></a>Comment travailler avec RevoScaleR

Fonctions dans **RevoScaleR** peuvent être appelées dans le code R encapsulé dans des procédures stockées. La plupart des développeurs build **RevoScaleR** solutions localement, puis migrez le code R terminé à des procédures stockées comme un exercice de déploiement.

Lorsque vous exécutez localement, vous généralement exécuter un script R à partir de la ligne de commande, ou à partir d’un environnement de développement R et spécifiez un contexte de calcul de SQL Server à l’aide d’un de le **RevoScaleR** fonctions. Vous pouvez utiliser le contexte de calcul à distance pour l’ensemble du code, ou pour des fonctions individuelles. Par exemple, vous souhaiterez peut-être décharger l’apprentissage du modèle sur le serveur d’utiliser des données les plus récentes et éviter le déplacement des données.

Lorsque vous êtes prêt à encapsuler le script R à l’intérieur d’une procédure stockée, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), nous vous recommandons de réécrire le code comme une fonction unique qui a défini clairement les entrées et sorties. 

## <a name="see-also"></a>Voir aussi

+ [Didacticiels R](../tutorials/sql-server-r-tutorials.md)
+ [Apprenez à utiliser des contextes de calcul](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R pour les développeurs SQL : Former et de faire fonctionner un modèle](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Microsoft product samples sur GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [Référence de R (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 
