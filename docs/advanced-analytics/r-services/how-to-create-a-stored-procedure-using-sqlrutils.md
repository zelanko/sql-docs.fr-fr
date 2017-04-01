---
title: "Guide pratique pour cr&#233;er une proc&#233;dure stock&#233;e &#224; l’aide de sqlrutils | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 5ba99b49-481e-4b30-967a-a429b855b1bd
caps.latest.revision: 10
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# Guide pratique pour cr&#233;er une proc&#233;dure stock&#233;e &#224; l’aide de sqlrutils
Cette rubrique décrit les étapes nécessaires pour convertir votre code R pour qu’il s’exécute en tant que procédure stockée T-SQL. Pour de meilleurs résultats, vous devrez peut-être modifier un peu votre code pour être sûr que toutes les entrées peuvent être paramétrées.

## <a name="step-1-format-your-r-script"></a>Étape 1. Mettre en forme votre script R

1. Encapsulez tout le code dans une fonction unique.

   Cela signifie que toutes les variables utilisées par la fonction doivent être définies à l’intérieur de la fonction ou en tant que paramètres d’entrée. Consultez [l’exemple de code](#samples) dans cette rubrique.

## <a name="step-2-standardize-the-inputs-and-outputs"></a>Étape 2. Normaliser les entrées et sorties

Les paramètres d’entrée de la fonction deviendront les paramètres d’entrée de la procédure stockée SQL. Ils doivent donc être conformes aux exigences de type suivantes :
- Parmi les paramètres d’entrée, il peut y avoir au plus une trame de données.
- Les objets à l’intérieur de la trame de données, ainsi que tous les autres paramètres d’entrée de la fonction, doivent être des types de données R suivants :
    - POSIXct
    - numérique
    - caractère
    - entier
    - logique
    - brut

- Si un type d’entrée n’est pas l’un des types ci-dessus, il doit être sérialisé et transmis à la fonction en tant que type *brut*. Dans ce cas, la fonction doit également inclure du code pour désérialiser l’entrée.

La fonction peut générer l’une des sorties suivantes :

- Une trame de données contenant les types de données pris en charge. Tous les objets dans la trame de données doivent utiliser l’un des types de données pris en charge.
- Une liste nommée contenant au plus une trame de données. Tous les membres de la liste doivent utiliser l’un des types de données pris en charge. 
- Une valeur NULL, si la fonction ne retourne pas de résultat.

## <a name="step-3-make-calls-to-the-sqlrutils-package-to-generate-the-stored-procedure"></a>Étape 3. Passer des appels au package sqlrutils pour générer la procédure stockée

Une fois que votre code R a été nettoyé et peut être appelé comme une fonction unique, vous pouvez commencer à utiliser les fonctions dans **sqlrutils** pour convertir votre code en procédure stockée.

En fonction des types de données des paramètres, vous utiliserez différentes fonctions pour capturer les données et créer un objet de paramètre.

1. Si votre fonction accepte des paramètres d’entrée, créez l’un des objets suivants pour chaque paramètre : 
    - Si le paramètre d’entrée est une trame de données, utilisez `setInputData`.
    - Pour tous les autres paramètres d’entrée, utilisez `setInputParameter`.

2. Si votre fonction génère une liste, créez un objet pour gérer les données de la liste souhaitées comme suit : 
    - Si la variable dans la liste est une trame de données, utilisez `setOutputData`.
    - Pour tous les autres membres de la liste, utilisez `setOutputParameter`.
    - Si votre fonction génère une trame de données directement, sans l’encapsuler au préalable dans une liste, vous pouvez ignorer cette étape. 
    - Ignorez cette étape si la fonction retourne la valeur NULL.

3. Quand tous les paramètres d’entrée et de sortie sont prêts, appelez le constructeur `StoredProcedure` pour générer la procédure stockée contenant la fonction R.
4. Pour inscrire immédiatement la procédure stockée auprès de la base de données, utilisez `registerStoredProcedure`.

## <a name="step-4-execute-the-stored-procedure"></a>Étape 4. Exécuter la procédure stockée

1. Si vous souhaitez exécuter la procédure stockée à partir de code R, plutôt qu’à partir de SQL Server, et que la procédure stockée nécessite une entrée, vous devez définir ces paramètres d’entrée avant que la fonction puisse être exécutée : 
    - Appelez `getInputParameters` pour obtenir une liste d’objets de paramètres d’entrée.
    - Définissez un `$query` ou un `$value` pour chaque paramètre d’entrée. 

2. Utilisez `executeStoredProcedure` pour exécuter la procédure stockée à partir de l’environnement de développement R, en passant la liste des objets de paramètres d’entrée que vous avez définis.

## <a name="a-name-samplesaexamples-prepare-your-code"></a><a name = "samples"></a>Exemples : préparer votre code 

Dans cet exemple, le code R lit à partir d’une base de données, effectue certaines transformations sur les données, puis les enregistre dans une autre base de données. Cet exemple simple sert uniquement à illustrer comment vous pouvez réorganiser votre code R pour fournir une interface plus simple pour la conversion de procédure stockée.

**Avant la mise en forme**


```R
sqlConnFrom <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=AirlineSrc;Trusted_Connection=Yes;"
  
sqlConnTo <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=AirlineTest;Trusted_Connection=Yes;"
  
sqlQueryAirline <- "SELECT TOP 10000 ArrDelay, CRSDepTime, DayOfWeek FROM [AirlineDemoSmall]"
  
dsSqlFrom <- RxSqlServerData(sqlQuery = sqlQueryAirline, connectionString = sqlConnFrom)
  
dsSqlTo <- RxSqlServerData(table = "cleanData", connectionString = sqlConnTo)
  
xFunc <- function(data) {
    data$CRSDepHour <- as.integer(trunc(data$CRSDepTime))
    return(data)
    }
  
xVars <- c("CRSDepTime")
  
sqlCompute <- RxInSqlServer(numTasks = 4, connectionString = sqlConnTo)
  
rxOpen(dsSqlFrom)
rxOpen(dsSqlTo)
  
if (rxSqlServerTableExists("cleanData", connectionString = sqlConnTo))   {
    rxSqlServerDropTable("cleanData")}
  
rxDataStep(inData = dsSqlFrom, 
     outFile = dsSqlTo,
     transformFunc = xFunc,
     transformVars = xVars,
     overwrite = TRUE)
```
Notez que quand vous utilisez une connexion ODBC au lieu d’appeler la fonction *RxSqlServerData*, vous devez ouvrir la connexion à l’aide de *rxOpen* pour pouvoir effectuer des opérations sur la base de données.



**Après la mise en forme**

Dans la version remise en forme, la première ligne définit le nom de fonction.

Le reste du code de votre solution R d’origine devient une partie de cette fonction. 

```R
myetl1function <- function() { 
   sqlConnFrom <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=Airline01;Trusted_Connection=Yes;"
   sqlConnTo <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer02;Database=Airline02;Trusted_Connection=Yes;"
    
   sqlQueryAirline <- "SELECT TOP 10000 ArrDelay, CRSDepTime, DayOfWeek FROM [AirlineDemoSmall]"

   dsSqlFrom <- RxSqlServerData(sqlQuery = sqlQueryAirline, connectionString = sqlConnFrom)
  
   dsSqlTo <- RxSqlServerData(table = "cleanData", connectionString = sqlConnTo)
  
   xFunc <- function(data) {
     data$CRSDepHour <- as.integer(trunc(data$CRSDepTime))
     return(data)}
  
   xVars <- c("CRSDepTime")
  
   sqlCompute <- RxInSqlServer(numTasks = 4, connectionString = sqlConnTo)
  
   if (rxSqlServerTableExists("cleanData", connectionString = sqlConnTo)) {rxSqlServerDropTable("cleanData")}
  
   rxDataStep(inData = dsSqlFrom, 
        outFile = dsSqlTo,
        transformFunc = xFunc,
        transformVars = xVars,
        overwrite = TRUE)
   return(NULL)
}
```
Bien que vous n’ayez pas besoin d’ouvrir la connexion ODBC explicitement dans le cadre de votre code, une connexion ODBC est quand même nécessaire pour utiliser **sqlrutils**. 


## <a name="see-also"></a>Voir aussi

[Génération d’une procédure stockée à l’aide de sqlrutils](../../advanced-analytics/r-services/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)

