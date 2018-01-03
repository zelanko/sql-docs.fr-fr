---
title: "Créez une simulation simple (SQL et R approfondie) | Documents Microsoft"
ms.custom: 
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs: R
ms.assetid: f420b816-ddab-4a1a-89b9-c8285a2d33a3
caps.latest.revision: "16"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 047ce5984129eadde9ef92505b7c5448f7c37d4f
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2017
---
# <a name="create-a-simple-simulation-sql-and-r-deep-dive"></a>Créez une simulation simple (SQL et R approfondie)

Cet article est la dernière étape du didacticiel de présentation approfondie de science des données, sur l’utilisation de [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Jusqu'à présent vous utilisez les fonctions R qui sont conçues spécifiquement pour le déplacement des données entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et contexte de calcul local. Toutefois, supposons que vous écrivez une fonction R totalement personnalisée et que souhaitez l’exécuter dans le contexte du serveur.

Vous pouvez appeler une fonction arbitraire dans le contexte de l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , à l’aide de la fonction [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) . Vous pouvez également utiliser **rxExec** pour répartir le travail entre les cœurs dans un seul serveur explicitement.

Dans cette leçon, vous utilisez le serveur distant pour créer une simulation simple. La simulation ne nécessite aucune donnée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . L’exemple montre uniquement comment concevoir une fonction personnalisée, puis comment l’appeler à l’aide de la fonction **rxExec** .

Pour obtenir un exemple plus complexe de l’utilisation de **rxExec**, consultez l’article : [parallélisme de granularité grossière avec foreach et rxExec](http://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html)

## <a name="create-the-custom-function"></a>Créer la fonction personnalisée

Un jeu de casino classique consiste à lancer une paire de dés, avec les règles suivantes :

- Si vous obtenez 7 ou 11 au premier lancer, vous gagnez.
- Si vous obtenez 2, 3 ou 12, vous perdez.
- Si vous obtenez 4, 5, 6, 8, 9 ou 10, ce nombre devient votre référence et vous continuez à lancer les dés jusqu’à ce que vous que retombiez sur cette référence (lancer gagnant) ou que vous obteniez 7 (lancer perdant).

Vous pouvez facilement simuler le jeu en R, en créant une fonction personnalisée, puis en l’exécutant plusieurs fois.

1.  Créez la fonction personnalisée à l’aide du code R suivant :
  
    ```R
    rollDice <- function()
    {
        result <- NULL
        point <- NULL
        count <- 1
            while (is.null(result))
            {
                roll <- sum(sample(6, 2, replace=TRUE))
  
                if (is.null(point))
                { point <- roll }
                if (count == 1 && (roll == 7 || roll == 11))
                {  result <- "Win" }
                else if (count == 1 && (roll == 2 || roll == 3 || roll == 12))
                { result \<- "Loss" }
                else if (count > 1 && roll == 7 )
                { result \<- "Loss" }
                else if (count > 1 && point == roll)
                { result <- "Win" }
                else { count <- count + 1 }
            }
            result
    }
    ```
  
2.  Pour simuler un jeu unique de découper, exécutez la fonction.
  
    ```R
    rollDice()
    ```
  
    Avez-vous gagné ou perdu ?
  
Maintenant nous allons voir comment vous pouvez utiliser **rxExec** plusieurs exécutions de la fonction, pour créer une simulation permettant de déterminer la probabilité d’un avantage.

## <a name="create-the-simulation"></a>Créer la simulation

Pour exécuter une fonction arbitraire dans le contexte de l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous pouvez appeler la fonction **rxExec** . Bien que **rxExec** également prend en charge distribués de l’exécution d’une fonction en parallèle sur les nœuds ou cœurs dans un contexte de serveur, ici s’exécute votre personnalisé fonctionne sur l’ordinateur SQL Server.

1. Appeler la fonction personnalisée en tant qu’argument à **rxExec**, avec les autres paramètres qui modifient la simulation.
  
    ```R
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")
    length(sqlServerExec)
    ```
  
    - Utilisez l’argument *timesToRun* pour indiquer le nombre d’exécutions de la fonction.  Dans ce cas, vous lancez les dés 20 fois.
  
    - Les arguments *RNGseed* et *RNGkind* peuvent être utilisés pour contrôler la génération de nombres aléatoires. Quand *RNGseed* est défini sur **auto**, un flux de nombres aléatoires parallèle est initialisé sur chaque processus de travail.
  
2. La fonction **rxExec** crée une liste comportant un élément pour chaque exécution. Toutefois, vous ne verrez pas grand-chose se produire tant que la liste n’est pas complète. Quand toutes les itérations sont terminées, la ligne commençant par `length` retourne une valeur.
  
    Vous pouvez ensuite passer à l’étape suivante pour obtenir un résumé de votre bilan de victoires et de pertes.
  
3. Convertissez la liste renvoyée en vecteur utilisant la fonction `unlist` de R, et résumez les résultats à l’aide de la fonction `table` .
  
    ```R
    table(unlist(sqlServerExec))
    ```
  
    Vos résultats doivent se présenter comme suit :
  
     *Perte Win* *12 8*

## <a name="conclusions"></a>Conclusions

Dans ce didacticiel, vous vous être familiarisé avec les tâches suivantes :
  
-   Obtention de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à utiliser dans des analyses
  
-   Création et modification de sources de données en R
  
-   Transmission de modèles, de données et de traçages entre votre station de travail et le serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
  

Si vous souhaitez faire des essais avec ces techniques à l’aide d’un jeu de données plu de 10 millions d’observations, les fichiers de données sont disponibles à partir du site web d’analytique Revolution : [Index des jeux de données](http://packages.revolutionanalytics.com/datasets)

Pour réutiliser cette procédure pas à pas avec les fichiers de données plus volumineux, télécharger les données et modifier chacune des sources de données comme suit :

1. Modifier les variables `ccFraudCsv` et `ccScoreCsv` pour pointer vers les nouveaux fichiers de données
2. Modifier le nom de la table référencée dans *sqlFraudTable* à`ccFraud10`
3. Modifier le nom de la table référencée dans *sqlScoreTable* à`ccFraudScore10`

## <a name="additional-samples"></a>Exemples supplémentaires

Maintenant que vous maîtrisez l’utilisation de contextes de calcul et les fonctions RevoScaler pour transmettre et transformer des données, consultez ces didacticiels :

[Didacticiels de R pour les Services de Machine Learning](machine-learning-services-tutorials.md)
## <a name="previous-step"></a>Étape précédente

[Déplacer des données entre SQL Server et un fichier XDF](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
