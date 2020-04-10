---
title: Charger des données avec rxImport
description: 'Tutoriel RevoScaleR 10 : Comment charger des données à l’aide du langage R sur SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fd78a315ed648313ce371dd9cc54a67b18fb8be9
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "81116882"
---
# <a name="load-data-into-memory-using-rximport-sql-server-and-revoscaler-tutorial"></a>Charger des données en mémoire à l’aide de rxImport (didacticiel SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Il s’agit du tutoriel 10 de la [série de tutoriels RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) qui traite de l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans ce tutoriel, vous allez apprendre à obtenir des données à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis à utiliser la fonction **rxImport** pour placer les données dignes d’intérêt dans un fichier local. De cette façon, vous pouvez les analyser dans le contexte de calcul local à plusieurs reprises, sans devoir réinterroger la base de données.

La fonction [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) peut être utilisée pour déplacer les données d’une source de données dans une trame de données située dans la mémoire de session de R, ou dans un fichier XDF sur disque. Si vous ne spécifiez pas de fichier de destination, les données sont placées en mémoire sous la forme d’une trame de données.

## <a name="extract-a-subset-of-data-from-sql-server-to-local-memory"></a>Extraire un sous-ensemble de données de SQL Server vers la mémoire locale

Vous avez décidé d’examiner plus en détail les individus à haut risque uniquement. La table source de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est volumineuse, donc vous souhaitez obtenir des informations sur les clients à haut risque uniquement. Vous chargez ensuite ces données dans une trame de données dans la mémoire de la station de travail locale.

1. Réinitialisez le contexte de calcul sur votre station de travail locale.

    ```R
    rxSetComputeContext("local")
    ```

2. Créez un objet de source de données SQL Server en fournissant une instruction SQL valide dans le paramètre *sqlQuery* . Cet exemple récupère une partie des observations ayant les scores de risque les plus élevés. De cette façon, seules les données dont vous avez vraiment besoin sont placées dans la mémoire locale.

    ```R
    sqlServerProbDS \<- RxSqlServerData(
        sqlQuery = paste("SELECT * FROM ccScoreOutput2",
        "WHERE (ccFraudProb > .99)"),
        connectionString = sqlConnString)
    ```

3. Appelez la fonction [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) pour lire les données dans une trame de données située dans la session R locale.

    ```R
    highRisk <- rxImport(sqlServerProbDS)
    ```

    Si l’opération a réussi, vous devez voir un message d’état semblable à celui-ci : « Lignes lues : 35, Nombre total de lignes traitées : 35, durée totale de la segmentation : 0,036 seconde »

4. Les observations sur les clients à haut risque se trouvant maintenant dans une trame de données en mémoire, vous pouvez utiliser différentes fonctions R pour manipuler la trame de données. Vous pouvez par exemple classer les clients en fonction de leur score de risque et imprimer une liste de ceux qui présentent le risque le plus élevé.

    ```R
    orderedHighRisk <- highRisk[order(-highRisk$ccFraudProb),]
    row.names(orderedHighRisk) <- NULL
    head(orderedHighRisk)
    ```

**Résultats**

```R
ccFraudLogitScore   state gender cardholder balance numTrans numIntlTrans creditLine ccFraudProb1
9.786345    SD   Male  Principal   23456       25            5 75   0.99994382
9.433040    FL Female  Principal   20629       24           28 75   0.99992003
8.556785    NY Female  Principal   19064       82           53 43   0.99980784
8.188668    AZ Female  Principal   19948       29            0 75   0.99972235
7.551699    NY Female  Principal   11051       95            0 75   0.99947516
7.335080    NV   Male  Principal   21566        4            6  75   0.9993482
```

## <a name="more-about-rximport"></a>En savoir plus sur rxImport

Vous pouvez utiliser **rxImport** non seulement pour déplacer des données, mais aussi pour transformer les données pendant leur lecture. Par exemple, vous pouvez spécifier le nombre de caractères pour les colonnes à largeur fixe, fournir une description des variables, définir des niveaux pour les colonnes de facteur et même créer des niveaux à utiliser après l’importation.

La fonction **rxImport** attribue des noms de variables aux colonnes pendant le processus d’importation, mais vous pouvez indiquer de nouveaux noms de variables à l’aide du paramètre *colInfo* ou modifier les types de données à l’aide du paramètre *colClasses*.

En spécifiant des opérations supplémentaires dans le paramètre *transforms* , vous pouvez effectuer un traitement élémentaire sur chaque segment de données lu.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Créer une table SQL Server à l’aide de rxDataStep](../../machine-learning/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)