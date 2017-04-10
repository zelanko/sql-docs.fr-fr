---
title: "Le&#231;on 5 : Cr&#233;er une simulation simple (Immersion dans la science des donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "10/03/2016"
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
ms.assetid: f420b816-ddab-4a1a-89b9-c8285a2d33a3
caps.latest.revision: 16
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 15
---
# Le&#231;on 5 : Cr&#233;er une simulation simple (Immersion dans la science des donn&#233;es)
Jusqu’à présent, vous avez utilisé des fonctions R fournies par SQL Server R Services spécifiquement conçues pour déplacer des données entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et un contexte de calcul local. Toutefois, supposons que vous écrivez une fonction R totalement personnalisée et que souhaitez l’exécuter dans le contexte du serveur.  
  
Vous pouvez appeler une fonction arbitraire dans le contexte de l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à l’aide de la fonction *rxExec*. Vous pouvez également utiliser *rxExec* pour répartir explicitement le travail entre les cœurs d’un même nœud serveur.  
  
Dans cette leçon, vous allez utiliser le serveur distant pour créer une simulation simple. La simulation ne nécessite aucune donnée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L’exemple montre uniquement comment concevoir une fonction personnalisée, puis comment l’appeler à l’aide de la fonction *rxExec*.  
  
Pour obtenir un exemple plus complexe de l’utilisation de *rxExec*, consultez l’article [http://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html](http://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html).  
  
## Créer la fonction  
Un jeu de casino classique consiste à lancer une paire de dés, avec les règles suivantes :  
  
-   Si vous obtenez 7 ou 11 au premier lancer, vous gagnez.  
  
-   Si vous obtenez 2, 3 ou 12, vous perdez.  
  
-   Si vous obtenez 4, 5, 6, 8, 9 ou 10, ce nombre devient votre référence et vous continuez à lancer les dés jusqu’à ce que vous que retombiez sur cette référence (lancer gagnant) ou que vous obteniez 7 (lancer perdant).  
  
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
                { result <- "Loss" }    
                else if (count > 1 && roll == 7 )   
                { result <- "Loss" }    
                else if (count > 1 && point == roll)   
                { result <- "Win" }    
                else { count <- count + 1 }   
            }   
            result   
    }  
  
    ```  
  
2.  Pour simuler un jeu de dés unique, exécutez la fonction.  
  
    ```R  
    rollDice()   
    ```  
  
    Avez-vous gagné ou perdu ?  
  
Maintenant, nous allons voir comment vous pouvez exécuter la fonction à plusieurs reprises, pour créer une simulation qui permet de déterminer la probabilité d’une victoire.  
  
## Créer la simulation  
Pour exécuter une fonction arbitraire dans le contexte de l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez appeler la fonction *rxExec*. Bien que *rxExec* prenne également en charge l’exécution distribuée d’une fonction en parallèle sur les nœuds ou cœurs dans un contexte de serveur, ici, vous allez uniquement l’utiliser pour exécuter votre fonction personnalisée sur le serveur.  
  
1.  Appelez la fonction personnalisée comme argument de *rxExec*, ainsi que certains autres paramètres qui modifient la simulation.  
  
    ```R  
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")   
    length(sqlServerExec)   
    ```  
  
    -   Utilisez l’argument *timesToRun* pour indiquer le nombre d’exécutions de la fonction.  Dans ce cas, vous lancez les dés 20 fois.  
  
    -   Les arguments *RNGseed* et *RNGkind* peuvent être utilisés pour contrôler la génération de nombres aléatoires. Quand *RNGseed* est défini sur **auto**, un flux de nombres aléatoires parallèle est initialisé sur chaque processus de travail.  
  
2.  La fonction *rxExec* crée une liste comportant un élément pour chaque exécution. Toutefois, vous ne verrez pas grand-chose se produire tant que la liste n’est pas complète. Quand toutes les itérations sont terminées, la ligne commençant par `length` retourne une valeur.  
  
    Vous pouvez ensuite passer à l’étape suivante pour obtenir un résumé de votre bilan de victoires et de pertes.  
  
3.  Convertissez la liste renvoyée en vecteur utilisant la fonction *unlist* de R, et résumez les résultats à l’aide de la fonction *table*.  
  
    ```R  
    table(unlist(sqlServerExec))  
    ```  
  
    Vos résultats doivent se présenter comme suit :  
  
     *Loss  Win*   
     *12  8*  
  
## Conclusions  
Dans ce didacticiel, vous vous être familiarisé avec les tâches suivantes :  
  
-   Obtention de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à utiliser dans des analyses  
  
-   Création et modification de sources de données en R  
  
-   Transmission de modèles, de données et de traçages entre votre station de travail et le serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
>  [!TIP]
> 
> Si vous souhaitez expérimenter ces techniques à l’aide d’un dataset plus volumineux de 10 millions d’observations, les fichiers de données sont disponibles à l’adresse [http://packages.revolutionanalytics.com/datasets](http://packages.revolutionanalytics.com/datasets).  
>   
> Pour réutiliser cette procédure pas à pas avec les fichiers de données plus volumineux, téléchargez les données, puis modifiez les sources de données comme suit :   
>  -   Définissez les variables *ccFraudCsv* et *ccScoreCsv* pour qu’elles pointent vers les nouveaux fichiers de données.     
>  -   Modifiez le nom de la table référencée dans *sqlFraudTable* en *ccFraud10*.    
>  -   Modifiez le nom de la table référencée dans *sqlScoreTable* en *ccFraudScore10*.   
  
## Étape précédente  
[Déplacer des données entre SQL Server et un fichier XDF &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/move-data-between-sql-server-and-xdf-file-data-science-deep-dive.md)  
  
  
  
