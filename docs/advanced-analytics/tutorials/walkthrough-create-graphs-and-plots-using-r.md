---
title: Créer des graphiques et des tracés à l’aide des fonctions SQL et R-SQL Server Machine Learning
description: Didacticiel illustrant comment créer des graphiques et des tracés à l’aide des fonctions de langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: f14005b8ba9d6f05d2b69deba29d83af5695f657
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470510"
---
# <a name="create-graphs-and-plots-using-sql-and-r-walkthrough"></a>Créer des graphiques et des tracés à l’aide de SQL et R (procédure pas à pas)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans cette partie de la procédure pas à pas, vous allez apprendre des techniques de génération de tracés et de cartes à l’aide de R avec des données SQL Server. Vous créez un histogramme simple, puis vous développez un tracé de carte plus complexe.

## <a name="prerequisites"></a>Prérequis

Cette étape suppose une session R en cours basée sur les étapes précédentes de cette procédure pas à pas. Elle utilise les chaînes de connexion et les objets de source de données créés dans ces étapes. Les outils et les packages suivants sont utilisés pour exécuter le script.

+ RGUI. exe pour exécuter des commandes R
+ Management Studio pour exécuter T-SQL
+ googMap
+ package ggmap
+ package mapproj

## <a name="create-a-histogram"></a>Créer un histogramme

1. Générez le premier tracé à l’aide de la fonction [rxHistogram](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource) .  La fonction rxHistogram fournit des fonctionnalités similaires à celles des packages R Open source, mais peut s’exécuter dans un contexte d’exécution distant.

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
    > Votre graphique est-il différent?
    >  
    > Cela est dû  au fait que l’indatasource utilise uniquement les 1000 premières lignes. L’ordonnancement des lignes à l’aide de TOP est non déterministe en l’absence d’une clause ORDER BY. il est donc prévu que les données et le graphe résultant peuvent varier.
    > Cette image a été générée à l’aide de 10 000 lignes de données environ. Nous vous recommandons de faire des essais avec différents nombres de lignes pour obtenir différents graphiques, et de noter le temps nécessaire pour retourner les résultats dans votre environnement.

## <a name="create-a-map-plot"></a>Créer un tracé de carte

En règle générale, les serveurs de base de données bloquent l’accès à Internet. Cela peut être gênant quand vous utilisez des packages R qui doivent télécharger des cartes ou d’autres images pour générer des tracés. Toutefois, il existe une solution de contournement qui peut s’avérer utile lors du développement de vos propres applications. Fondamentalement, vous générez la représentation cartographique sur le client, puis superposez sur la carte les points qui sont stockés en tant qu’attributs dans la table SQL Server.

1. Définissez la fonction qui crée l’objet de tracé R. La fonction personnalisée *mapPlot* crée un nuage de points qui utilise les emplacements de capture des taxis et trace le nombre de tours qui ont démarré à partir de chaque emplacement. Elle utilise les packages **ggplot2** et **ggmap** , qui doivent déjà être [installés et chargés](walkthrough-data-science-end-to-end-walkthrough.md#add-packages).

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

    + La fonction *mapPlot* accepte deux arguments: un objet de données existant, que vous avez défini précédemment à l’aide de RxSqlServerData, et la représentation cartographique transmise à partir du client.
    + Dans la ligne qui commence par la variable *DS* , rxImport est utilisé pour charger les données de la mémoire à partir de la source de données créée précédemment, indatasource. (Cette source de données contient uniquement 1000 lignes; si vous souhaitez créer une carte avec plus de points de données, vous pouvez substituer une autre source de données.)
    + Chaque fois que vous utilisez des fonctions R Open source, les données doivent être chargées dans des trames de données dans la mémoire locale. Toutefois, en appelant la fonction [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport) , vous pouvez exécuter dans la mémoire du contexte de calcul distant.

2. Modifiez le contexte de calcul en local et chargez les bibliothèques nécessaires pour créer les mappages.

    ```R
    rxSetComputeContext("local")
    library(ggmap)
    library(mapproj)
    gc <- geocode("Times Square", source = "google")
    googMap <- get_googlemap(center = as.numeric(gc), zoom = 12, maptype = 'roadmap', color = 'color');
    ```

    + La variable `gc` stocke un jeu de coordonnées pour Times Square, NY.

    + La ligne commençant par `googmap` génère une carte avec les coordonnées spécifiées au centre.

3. Basculez vers le contexte de calcul SQL Server et affichez les résultats, en encapsulant la fonction de traçage dans [rxExec](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxexec) comme indiqué ici. La fonction rxExec fait partie du package **RevoScaleR** et prend en charge l’exécution de fonctions R arbitraires dans un contexte de calcul distant.

    ```R
    rxSetComputeContext(sqlcc)
    myplots <- rxExec(mapPlot, inDataSource, googMap, timesToRun = 1)
    plot(myplots[[1]][["myplot"]]);
    ````

    + Les données cartographiques `googMap` dans sont passées en tant qu’arguments à la fonction exécutée à distance *mapPlot*. Étant donné que les mappages ont été générés dans votre environnement local, ils doivent être passés à la fonction pour créer le tracé dans le contexte de SQL Server.

    + Lorsque la ligne qui commence `plot` par s’exécute, les données rendues sont sérialisées dans l’environnement r local afin que vous puissiez les afficher dans votre client r.

    > [!NOTE]
    > Si vous utilisez SQL Server sur une machine virtuelle Azure, vous pouvez recevoir une erreur à ce stade. Une erreur se produit lorsque la règle de pare-feu par défaut dans Azure bloque l’accès réseau par le code R. Pour plus d’informations sur la résolution de cette erreur, consultez [installation des Services machine learning (R) sur une machine virtuelle Azure](../install/sql-machine-learning-azure-virtual-machine.md).

4. L’image suivante montre le tracé de sortie. Les emplacements de montée en taxi sont ajoutés à la carte sous forme de points rouges. Votre image peut paraître différente, en fonction du nombre d’emplacements dans la source de données que vous avez utilisée.

    ![Traçage des courses en taxi à l’aide d’une fonction R personnalisée](media/rsql-e2e-mapplot.png "Traçage des courses en taxi à l’aide d’une fonction R personnalisée")

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Créer des fonctionnalités de données à l’aide de R et SQL](walkthrough-create-data-features.md)
