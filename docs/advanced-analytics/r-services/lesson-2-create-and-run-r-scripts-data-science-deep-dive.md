---
title: "Le&#231;on 2 : Cr&#233;er et ex&#233;cuter des scripts R (Immersion dans la science des donn&#233;es) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "10/26/2016"
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
ms.assetid: 51e8e66f-a0a5-4e96-aa71-f5c870e6d0d4
caps.latest.revision: 18
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 18
---
# Le&#231;on 2 : Cr&#233;er et ex&#233;cuter des scripts R (Immersion dans la science des donn&#233;es)
Maintenant que vous avez configuré vos sources de données et établi un ou plusieurs contextes de calcul, vous êtes prêt à exécuter des scripts R haute performance à l’aide de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Dans cette leçon, vous allez utiliser le contexte de calcul du serveur pour effectuer certaines tâches courantes d’apprentissage automatique :  
  
-   Visualiser des données et générer des statistiques de synthèse    
-   Créer un modèle de régression linéaire    
-   Créer un modèle de régression logistique    
-   Affecter un score à de nouvelles données et créer un histogramme des scores  
  
## Basculer vers le contexte de calcul de serveur  
Avant d’exécuter tout code R, vous devez spécifier le contexte de calcul *actuel* ou *actif*.  
  
1.  Pour activer un contexte de calcul que vous avez déjà défini à l’aide de R, utilisez la fonction *rxSetComputeContext*, comme indiqué ici :  
  
    ```R  
    rxSetComputeContext(sqlCompute)   
    ```  
  
    Dès que vous exécutez cette instruction, tous les calculs suivants sont effectués sur l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifié dans le paramètre *sqlCompute*.  
  
  
2.  Si vous préférez exécuter le code R sur votre station de travail, vous pouvez rebasculer le contexte de calcul vers l’ordinateur local à l’aide du mot clé  **local** .  
  
    ```R  
    rxSetComputeContext ("local")    
    ```  
  
    Pour obtenir la liste des autres mots clés pris en charge par cette fonction, tapez `help("rxSetComputeContext")` sur une ligne de commande R.  
  
> [!NOTE]  
> Une fois que vous avez spécifié un contexte de calcul, il reste actif jusqu’à ce que vous le changiez. Cependant, tout script R qui *ne peut pas* être exécuté dans un contexte de serveur distant sera exécuté localement.  
  
## Calculer des statistiques de synthèse  
Pour voir comment fonctionne le contexte de calcul, essayez de générer des statistiques de synthèse à l’aide de la source de données *sqlFraudDS*.  N’oubliez pas que l’objet de source de données définit uniquement les données que vous allez utiliser. Il ne change pas le contexte de calcul.

+ Pour effectuer la synthèse localement, utilisez *rxSetComputeContext* et spécifiez le mot clé « local ».
+ Pour créer les mêmes calculs sur l’ordinateur SQL Server, basculez vers le contexte de calcul SQL que vous avez défini précédemment.  

  
1.  Appelez la fonction *rxSummary* et passez les arguments nécessaires, tels que la formule et la source de données, puis attribuez les résultats à la variable *sumOut*.  
  
    ```R  
    sumOut <- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)  
  
    ```  
  
    Le langage R fournit de nombreuses fonctions de synthèses, mais *rxSummary* prend en charge l’exécution sur les différents contextes de calcul à distance, y compris [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Pour plus d’informations sur les fonctions similaires, consultez [Data Summaries](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-summaries) (Synthèses de données) dans la [documentation de référence ScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler).
  
2.  Lorsque le traitement est terminé, vous pouvez imprimer le contenu de la variable *sumOut* dans la console.  
  
    ```R  
    sumOut  
    ```  
  
    > [!NOTE]  
    > Si vous essayez d’imprimer les résultats avant qu’ils n’aient été retournés à partir de l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez obtenir une erreur.  
  
  
**Résultats**  
  
*Summary Statistics Results for: ~gender + balance + numTrans +*   
 *numIntlTrans + creditLine*    
 *Data: sqlFraudDS (RxSqlServerData Data Source)*    
 *Number of valid observations: 10000*    
 *Name  Mean    StdDev  Min Max ValidObs    MissingObs*    
 *balance       4075.0318 3926.558714            0   25626 100000*    
 *numTrans        29.1061   26.619923 0     100 10000    0           100000*    
 *numIntlTrans     4.0868    8.726757 0      60 10000    0           100000*    
 *creditLine       9.1856    9.870364 1      75 10000    0          100000 Category Counts for gender*    
 *Number of categories: 2*    
 *Number of valid observations: 10000*   
 *Number of missing observations: 0*    
 *gender Counts*    
 *Male   6154*    
  *Female 3846*  
  
## Ajouter les valeurs maximales et minimales  
D’après les statistiques de synthèse calculées, vous avez trouvé des informations utiles sur les données que vous souhaitez placer dans la source de données afin de les utiliser dans d’autres calculs. Par exemple, vous pouvez utiliser les valeurs minimale et maximale pour calculer des histogrammes. Vous décidez donc d’ajouter les valeurs minimale et maximale à la source de données *RxSqlServerData*.  
  
Heureusement, [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] comprend des fonctions optimisées capables de convertir avec une grande efficacité des données entières en données factorielles catégoriques.  
  
1.  Commencez par configurer des variables temporaires.  
  
    ```R  
    sumDF <- sumOut$sDataFrame   
    var <- sumDF$Name    
    ```  
  
2.  Utilisez la variable *ccColInfo* créée précédemment pour définir les colonnes de la source de données.  
  
    Vous ajouterez également certaines nouvelles colonnes calculées (*numTrans*, *numIntlTrans* et *creditLine*) à la collection de colonnes.  
  
    ```R 
    ccColInfo <- list(
        gender = list(type = "factor",  
          levels = c("1", "2"), 
          newLevels = c("Male", "Female")), 
        cardholder = list(type = "factor",  
          levels = c("1", "2"), 
          newLevels = c("Principal", "Secondary")), 
        state = list(type = "factor", 
          levels = as.character(1:51), 
          newLevels = stateAbb), 
        balance  = list(type = "numeric"),
        numTrans = list(type = "factor", 
          levels = as.character(sumDF[var == "numTrans", "Min"]:sumDF[var == "numTrans", "Max"])),
        numIntlTrans = list(type = "factor",  
            levels = as.character(sumDF[var == "numIntlTrans", "Min"]:sumDF[var =="numIntlTrans", "Max"])),
        creditLine = list(type = "numeric")
            )
  
    ```  
  
3.  Ayant mis à jour la collection de colonnes, vous pouvez appliquer l’instruction suivante pour créer une version mise à jour de la source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] déjà définie.  
  
    ```R  
    sqlFraudDS <- RxSqlServerData(  
        connectionString = sqlConnString,   
        table = sqlFraudTable,   
        colInfo = ccColInfo,        
        rowsPerRead = sqlRowsPerRead)   
    ```  
  
    La source de données *sqlFraudDS* inclut désormais les nouvelles colonnes ajoutées dans *ccColInfo*.  
  
Notez que les modifications affectent uniquement l’objet de source de données en R. Aucune nouvelle donnée n’a encore été écrite dans la table de base de données. Toutefois, vous pouvez utiliser les données capturées dans la variable *sumOut* pour créer des visualisations et des synthèses. À l’étape suivante, vous allez découvrir comment procéder en changeant de contexte de calcul. 

> [!TIP]
> Si vous avez oublié le contexte de calcul que vous utilisez, utilisez `rxGetComputeContext()`.  Si la valeur de retour est `RxLocalSeq Compute Context`, vous utilisez le contexte de calcul local.
  
## Étape suivante  
[Visualiser des données SQL Server à l’aide de R &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/visualize-sql-server-data-using-r-data-science-deep-dive.md)  
  
## Étape précédente  
[Définir et utiliser des contextes de calcul &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/define-and-use-compute-contexts-data-science-deep-dive.md)  
  
  
  
