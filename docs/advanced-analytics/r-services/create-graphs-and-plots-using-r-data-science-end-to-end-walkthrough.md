---
title: "Cr&#233;er des graphiques et des trac&#233;s &#224; l’aide de R (Proc&#233;dure pas &#224; pas pour une solution compl&#232;te de science des donn&#233;es) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 5f70f0a6-fd4a-410f-9f44-1605503f77ec
caps.latest.revision: 16
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Cr&#233;er des graphiques et des trac&#233;s &#224; l’aide de R (Proc&#233;dure pas &#224; pas pour une solution compl&#232;te de science des donn&#233;es)
Dans cette leçon, vous allez découvrir des techniques de génération de tracés et de cartes à l’aide de R avec des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  Vous allez voir comme il est facile d’afficher des tracés créés sur le serveur, et comment transmettre des objets graphiques au serveur.  
  
## <a name="creating-graphics"></a>Création de graphiques
Dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], les objets graphiques, ainsi que les modèles et les résultats, sont sérialisés entre votre ordinateur et le contexte de calcul [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

Lorsque vous utilisez un contexte de calcul SQL Server, vous ne pouvez pas télécharger la représentation sous forme de carte, car la plupart des serveurs de base de données de production bloquent entièrement l’accès à Internet.  Ainsi, pour créer le deuxième jeu de tracés, vous allez générer la représentation sous forme de carte dans le client, puis superposer sur la carte les points qui sont stockés en tant qu’attributs dans la table *nyctaxi_sample*.   

Pour ce faire, vous devez d’abord créer la représentation sous forme de carte en appelant Google Maps, puis passer la représentation sous forme de carte au contexte SQL.  
  
Il s’agit d’un modèle qui peut être utile pour développer vos propres applications.   
  
### <a name="create-a-histogram"></a>Créer un histogramme  
Pour créer un histogramme, vous allez utiliser la source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créée précédemment, avec la fonction `rxHistogram` fournie dans R Services.  
  
1.  Générez le premier tracé à l’aide de la fonction *rxHistogram*.  La fonction *rxHistogram* fournit une fonctionnalité similaire à celle des packages R open source, mais peut s’exécuter dans un contexte d’exécution à distance. 
  
    ```R  
    #Plot fare amount on SQL Server and return the plot  
    start.time <- proc.time()  
    rxHistogram(~fare_amount, data = inDataSource, title = "Fare Amount Histogram")  
    used.time <- proc.time() - start.time  
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2), " seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""))    
    ```         
  
2.  L’image est retourné dans l’appareil graphique R pour votre environnement de développement.  Par exemple, dans RStudio, cliquez sur la fenêtre **Plot** (Tracer).  Dans [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)], une fenêtre graphique distincte est ouverte.  
  
    ![using rxHistogram to plot fare amounts](../../advanced-analytics/r-services/media/rsql-e2e-rxhistogramresult.png "using rxHistogram to plot fare amounts")  
  
    > [!NOTE]  Étant donné que l’ordonnancement des lignes à l’aide de TOP est non déterministe sans clause ORDER BY, vous pouvez voir des résultats très différents. Nous vous recommandons de faire des essais avec différents nombres de lignes pour obtenir différents graphiques, et de noter le temps nécessaire pour retourner les résultats dans votre environnement.  Cette image a été générée à l’aide d’environ 10 000 lignes de données.
  
### <a name="create-a-map-plot"></a>Créer un tracé de carte  
Dans cet exemple, vous allez générer un objet de tracé en utilisant l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comme contexte de calcul, puis retourner l’objet de tracé au contexte de calcul local pour le rendu.  
   
1.  Tout d’abord, définissez la fonction qui crée l’objet de tracé.  

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
    + La fonction R personnalisée *mapPlot* crée un nuage de points qui utilise les lieux de prise en charge des passagers pour tracer le nombre de trajets ayant démarré à chaque emplacement. Elle utilise les packages **ggplot2** et  **ggmap** , qui doivent déjà être installés et chargés.  
    + La fonction *mapPlot* prend deux arguments : un objet de données existant, que vous avez défini précédemment à l’aide de *RxSqlServerData*, et la représentation sous forme de carte transmise à partir du client.    
    + Notez l’utilisation de la variable *ds* pour charger des données à partir de la source de données créée précédemment, *inDataSource*.  Chaque fois que vous utilisez des fonctions R open source, les données doivent être chargées dans des trames de données en mémoire. Vous pouvez pour cela utiliser la fonction *rxImport* dans le package **RevoScaleR**.  Toutefois, cette fonction s’exécute en mémoire dans le contexte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] défini précédemment. Autrement dit, la fonction n’utilise pas la mémoire de votre poste de travail local.  
  
2.  Ensuite, chargez les bibliothèques nécessaires pour créer les cartes dans votre environnement R local.  
  
    ```R  
    library(ggmap)  
    library(mapproj)  
    gc <- geocode("Times Square", source = "google")  
    googMap <- get_googlemap(center = as.numeric(gc), zoom = 12, maptype = 'roadmap', color = 'color';    
    ```  
    + Ce code s’exécute sur le client R. Notez l’appel répété aux bibliothèques **ggmap** et **mapproj**. Cela est dû au fait que la définition de fonction précédente a été exécutée dans le contexte de serveur, et que les bibliothèques n’ont jamais été chargées localement. Maintenant, vous transférez l’opération de traçage sur votre station de travail.  
  
    -   La variable *gc* stocke un jeu de coordonnées pour Times Square, NY.  
  
    -   La ligne commençant par *googmap* génère une carte avec les coordonnées spécifiées au centre.  
          
  
3.  Exécutez la fonction de traçage et affichez les résultats dans votre environnement R local. Pour ce faire, encapsulez la fonction de traçage dans *rxExec* comme indiqué ici.  La fonction *rxExec* est incluse dans le package **RevoScaleR** et prend en charge l’exécution de fonctions R arbitraires dans un contexte de calcul distant. 
  
    ```R  
    myplots <- rxExec(mapPlot, inDataSource, googMap, timesToRun = 1)  
    plot(myplots[[1]][["myplot"]]);  
  
    ```  
    + Sur la première ligne, vous pouvez constater que les données de carte sont passées comme argument (*googMap*) à la fonction exécutée à distance *mapPlot*. En effet, les cartes ont été générées dans votre environnement local et doivent être passées à la fonction pour créer le tracé dans le contexte de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].   
  
        Les données restituées sont ensuite resérialisées vers l’environnement R local pour que vous puissiez les afficher, à l’aide de la fenêtre **Plot** dans RStudio ou de tout autre périphérique graphique R.  
  
  
4.  Voici le tracé de sortie, qui montre les lieux de prise en charge sur la carte sous forme de points rouges.  
  
    ![plotting taxi rides using a custom R function](../../advanced-analytics/r-services/media/rsql-e2e-mapplot.png "plotting taxi rides using a custom R function")  
  
## <a name="next-lesson"></a>Leçon suivante  
[Leçon 3 : Créer des caractéristiques de données &#40;procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/lesson-3-create-data-features-data-science-end-to-end-walkthrough.md)  
  
  
  
