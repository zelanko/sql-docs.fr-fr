---
title: "Charger des données dans la mémoire à l’aide de rxImport | Documents Microsoft"
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 47a42e9a-05a0-4a50-871d-de73253cf070
caps.latest.revision: "14"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3517ad7bb95f79dc2dec2567ecb88d64e78338bc
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="load-data-into-memory-using-rximport"></a>Charger des données en mémoire à l’aide de rxImport

La fonction **rxImport** peut être utilisée pour déplacer les données d’une source de données dans une trame de données située dans la mémoire de session de R, ou dans un fichier XDF sur disque. Si vous ne spécifiez pas de fichier de destination, les données sont placées en mémoire sous la forme d’une trame de données.

Dans cette étape, vous allez apprendre à obtenir des données à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis utilisez la fonction rxImport pour placer les données d’intérêt dans un fichier local. De cette façon, vous pouvez les analyser dans le contexte de calcul local à plusieurs reprises, sans devoir réinterroger la base de données.

## <a name="extract-a-subset-of-data-from-sql-server-to-local-memory"></a>Extraire un sous-ensemble de données de SQL Server vers la mémoire locale

Supposons que vous souhaitez examiner plus en détail uniquement les individus à haut risque. La table source dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] étant volumineuse, vous allez récupérer uniquement les informations sur les clients à haut risque, et les charger dans une trame de données dans la mémoire de la station de travail locale.

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

3. Vous utilisez la fonction **rxImport** pour charger les données dans une trame de données située dans la session R locale.

    ```R
    highRisk <- rxImport(sqlServerProbDS)
    ```

    Si l’opération réussit, le message d’état suivant s’affiche : « Lignes lues : 35, Nombre total de lignes traitées : 35, Durée totale du segment : 0,036 seconde ».

4. Les observations sur les clients à haut risque se trouvant maintenant dans une trame de données en mémoire, vous pouvez utiliser différentes fonctions R pour manipuler cette trame de données. Pour cet exemple, vous pouvez classer les clients en fonction de leur score de risque et afficher ceux qui présentent le risque le plus élevé.

    ```R
    orderedHighRisk <- highRisk[order(-highRisk$ccFraudProb),]
    row.names(orderedHighRisk) <- NULL
    head(orderedHighRisk)
    ```

**Résultats**

*ccFraudLogitScore   state gender cardholder balance numTrans numIntlTrans creditLine ccFraudProb1*

*9.786345    SD   Male  Principal   23456       25            5 75   0.99994382*

*9.433040    FL Female  Principal   20629       24           28 75   0.99992003*

*8.556785    NY Female  Principal   19064       82           53 43   0.99980784*

*8.188668    AZ Female  Principal   19948       29            0 75   0.99972235*

*7.551699    NY Female  Principal   11051       95            0 75   0.99947516*

*7.335080    NV   Male  Principal   21566        4            6  75   0.9993482*

## <a name="more-about-rximport"></a>En savoir plus sur rxImport

Vous pouvez utiliser rxImport non seulement à déplacer les données, mais pour transformer les données en cours de lecture. Par exemple, vous pouvez spécifier le nombre de caractères pour les colonnes à largeur fixe, fournir une description des variables, définir des niveaux pour les colonnes de facteur et même créer des niveaux à utiliser après l’importation.

La fonction rxImport assigne des noms de variables aux colonnes pendant le processus d’importation, mais vous pouvez indiquer des noms de variables à l’aide de la *colInfo* paramètre, vous pouvez modifier les types de données à l’aide de la *colClasses* paramètre.

En spécifiant des opérations supplémentaires dans le paramètre *transforms* , vous pouvez effectuer un traitement élémentaire sur chaque segment de données lu.

## <a name="next-step"></a>Étape suivante

[Créer la nouvelle Table SQL Server à l’aide de rxDataStep](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)

## <a name="previous-step"></a>Étape précédente

[Transformer des données à l’aide de R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)

## <a name="see-also"></a>Voir aussi

[Didacticiels d’apprentissage](../../advanced-analytics/tutorials/machine-learning-services-tutorials.md)

