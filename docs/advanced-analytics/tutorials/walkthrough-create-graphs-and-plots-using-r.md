---
title: Créer des graphiques et des tracés à l’aide de SQL et R - fonctions SQL Server Machine Learning
description: Didacticiel montrant comment créer des graphiques et des tracés à l’aide des fonctions du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: b988105733d8e3a9ee2edae344947cbf9d377e5d
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67140388"
---
# <a name="create-graphs-and-plots-using-sql-and-r-walkthrough"></a>Créer des graphiques et des tracés à l’aide de SQL et R (procédure pas à pas)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans cette partie de la procédure pas à pas, vous découvrez des techniques permettant de générer des tracés et des cartes à l’aide de R avec des données SQL Server. Vous créez un histogramme simple et ensuite développez un tracé de carte plus complexe.

## <a name="prerequisites"></a>Prérequis

Cette étape suppose une session R en cours en fonction des étapes précédentes dans cette procédure pas à pas. Il utilise les connexion chaînes et les objets créés dans ces étapes. Les outils et les packages suivants sont utilisés pour exécuter le script.

+ RGUI.exe pour exécuter des commandes R
+ Management Studio pour exécuter T-SQL
+ googMap
+ package de ggmap
+ package de mapproj

## <a name="create-a-histogram"></a>Créer un histogramme

1. Générez le premier tracé à l’aide de la fonction [rxHistogram](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource) .  La fonction rxHistogram fournit des fonctionnalités similaires à celles dans les packages R open source, mais il peut s’exécuter dans un contexte d’exécution à distance.

    ```R
    # Plot fare amount on SQL Server and return the plot
    start.time <- proc.time()
    rxHistogram(~fare_amount, data = inDataSource, title = "Fare Amount Histogram")
    used.time <- proc.time() - start.time
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2), " seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate plot.", sep=""))
    ```

2. L’image est retourné dans l’appareil graphique R pour votre environnement de développement.  Par exemple, dans RStudio, cliquez sur la fenêtre **Plot** (Tracer).  Dans [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)], une fenêtre graphique distincte est ouverte.

    ![Utilisation de rxHistogram pour tracer les prix](media/rsql-e2e-rxhistogramresult.png "Utilisation de rxHistogram pour tracer les prix")

    > [!NOTE]
    > Votre graphique semble différent ?
    >  
    > C’est parce que _inDataSource_ utilise uniquement les 1000 premières lignes. L’ordre des lignes à l’aide de TOP étant non déterministe en l’absence d’une clause ORDER BY, il est probable que les données et le graphique résultant peuvent varier.
    > Cette image a été générée à l’aide de 10 000 lignes de données environ. Nous vous recommandons de faire des essais avec différents nombres de lignes pour obtenir différents graphiques, et de noter le temps nécessaire pour retourner les résultats dans votre environnement.

## <a name="create-a-map-plot"></a>Créer un tracé de carte

En règle générale, les serveurs de base de données bloquent l’accès à Internet. Cela peut être gênant lors de l’utilisation de packages R que vous avez besoin de télécharger des mappages ou autres images à générer des tracés. Toutefois, il existe une solution de contournement qui peut être utile pour développer vos propres applications. En fait, votre générer la représentation sous forme de carte sur le client, puis superposer sur la carte les points qui sont stockés en tant qu’attributs dans la table SQL Server.

1. Définissez la fonction qui crée l’objet de tracé R. La fonction personnalisée *mapPlot* crée un nuage qui utilise les lieux de taxis et les tracés le nombre de trajets ayant démarré à chaque emplacement. Il utilise le **ggplot2** et **ggmap** packages, qui doivent être déjà [installés et chargés](walkthrough-data-science-end-to-end-walkthrough.md#add-packages).

    ```R
    mapPlot <- function(inDataSource, googMap){
        library(ggmap)
        library(mapproj)
        ds <- rxImport(inDataSource)
        p <- ggmap(googMap)+
        geom_point(aes(x = pickup_longitude, y =pickup_latitude ), data=ds, alpha =.5,
    color="darkred", size = 1.5)
        return(list(myplot=p))
    }
    ```

    + Le *mapPlot* fonction accepte deux arguments : un objet de données existant, que vous avez défini précédemment à l’aide de RxSqlServerData, et la représentation sous forme de carte transmise à partir du client.
    + Dans la ligne commençant par le *ds* variable, rxImport est utilisé pour charger des données de mémoire à partir de la source de données créée précédemment, *inDataSource*. (Cette source de données contient uniquement les 1000 lignes ; si vous souhaitez créer une carte avec plus de points de données, vous pouvez remplacer une autre source de données).
    + Chaque fois que vous utilisez des fonctions R open source, les données doivent être chargées en trames de données dans la mémoire locale. Toutefois, en appelant le [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport) (fonction), vous pouvez exécuter dans la mémoire du contexte de calcul à distance.

2. Remplacez le contexte de calcul local, puis chargez les bibliothèques nécessaires pour créer les cartes.

    ```R
    rxSetComputeContext("local")
    library(ggmap)
    library(mapproj)
    gc <- geocode("Times Square", source = "google")
    googMap <- get_googlemap(center = as.numeric(gc), zoom = 12, maptype = 'roadmap', color = 'color');
    ```

    + La variable `gc` stocke un jeu de coordonnées pour Times Square, NY.

    + La ligne commençant par `googmap` génère une carte avec les coordonnées spécifiées au centre.

3. Basculez vers le contexte de calcul de SQL Server et afficher les résultats, en encapsulant la fonction de traçage dans [rxExec](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxexec) comme indiqué ici. La fonction rxExec fait partie de la **RevoScaleR** package et l’exécution prend en charge des fonctions R arbitraires dans un contexte de calcul à distance.

    ```R
    rxSetComputeContext(sqlcc)
    myplots <- rxExec(mapPlot, inDataSource, googMap, timesToRun = 1)
    plot(myplots[[1]][["myplot"]]);
    ````

    + Les données de carte dans `googMap` est passé en tant qu’argument à la fonction exécutée à distance *mapPlot*. Étant donné que les cartes ont été générées dans votre environnement local, elles doivent être passées à la fonction pour créer le tracé dans le contexte de SQL Server.

    + Lors de la ligne commençant par `plot` s’exécute, les données rendues est resérialisé vers l’environnement R local afin que vous puissiez l’afficher dans votre client de R.

    > [!NOTE]
    > Si vous utilisez SQL Server dans une machine virtuelle Azure, vous pouvez obtenir une erreur à ce stade. Une erreur se produit lorsque la règle de pare-feu par défaut dans Azure bloque l’accès au réseau par le code R. Pour plus d’informations sur la façon de corriger cette erreur, consultez [installation Machine Learning Services (R) sur une machine virtuelle Azure](../install/sql-machine-learning-azure-virtual-machine.md).

4. L’image suivante montre le tracé de sortie. Les emplacements de montée en taxi sont ajoutés à la carte sous forme de points rouges. Votre image peut se présenter différente, selon le nombre d’emplacements est dans la source de données que vous avez utilisé.

    ![Traçage des courses en taxi à l’aide d’une fonction R personnalisée](media/rsql-e2e-mapplot.png "Traçage des courses en taxi à l’aide d’une fonction R personnalisée")

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Créer des caractéristiques de données à l’aide de R et SQL](walkthrough-create-data-features.md)
