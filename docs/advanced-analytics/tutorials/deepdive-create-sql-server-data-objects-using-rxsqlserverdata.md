---
title: Créer des objets de données SQL Server à l’aide de RevoScaleR RxSqlServerData
description: Didacticiel procédure pas à pas sur la création d’objets de données à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: f78087e226f41c53555cf3356705f8b84a185392
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344696"
---
# <a name="create-sql-server-data-objects-using-rxsqlserverdata-sql-server-and-revoscaler-tutorial"></a>Créer des objets de données SQL Server à l’aide de RxSqlServerData (didacticiel SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cette leçon fait partie du [didacticiel RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

La leçon 2 est la suite de la création d’une base de données: l’ajout de tables et le chargement de données. Si un administrateur de base de données a créé la base de données et la connexion dans la [leçon 1](deepdive-work-with-sql-server-data-using-r.md), vous pouvez ajouter des tables à l’aide d’un IDE R comme RStudio ou d’un outil intégré tel que **RGUI**.

À partir de R, connectez-vous à SQL Server et utilisez les fonctions **RevoScaleR** pour effectuer les tâches suivantes:

> [!div class="checklist"]
> * Créer des tables pour les données d’apprentissage et les prédictions
> * Charger des tables avec des données d’un fichier. csv local

Les exemples de données sont des données simulées de fraude de carte de crédit (le jeu de données ccFraud), partitionnées en jeux de données d’apprentissage et de notation. Le fichier de données est inclus dans **RevoScaleR**.

Utilisez un IDE R ou une interface **RGUI** pour terminer ces Taks. Veillez à utiliser les exécutables R trouvés à cet emplacement: C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64 (RGUI. exe si vous utilisez cet outil, ou un IDE R pointant sur C:\Program Files\Microsoft\R Client\R_SERVER). Le fait de disposer d’une [station de travail cliente R](../r/set-up-a-data-science-client.md) avec ces fichiers exécutables est considéré comme un prérequis de ce didacticiel.

## <a name="create-the-training-data-table"></a>Créer la table de données d’apprentissage

1. Stocke la chaîne de connexion de base de données dans une variable R. Voici deux exemples de chaînes de connexion ODBC valides pour SQL Server: une à l’aide d’une connexion SQL et une pour l’authentification intégrée de Windows. 

   Veillez à modifier le nom du serveur, le nom d’utilisateur et le mot de passe, le cas échéant.

    **Connexion SQL**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=<server-name>; Database=RevoDeepDive;Uid=<user_name>;Pwd=<password>"
    ```

    **Authentification Windows**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=<server-name>;Database=RevoDeepDive;Trusted_Connection=True"
    ```

2. Spécifiez le nom de la table que vous voulez créer et enregistrez-le dans une variable R.
  
    ```R
    sqlFraudTable <- "ccFraudSmall"
    ```
  
    Étant donné que l’instance de serveur et le nom de la base de données sont déjà spécifiés dans la chaîne de connexion, quand vous combinez les deux variables, *le nom complet* de la nouvelle table devient *instance. Database. Schema. ccFraudSmall*.
  
3.  Si vous le souhaitez, spécifiez *rowsPerRead* pour contrôler le nombre de lignes de données lues dans chaque lot.
  
    ```R
    sqlRowsPerRead = 5000
    ```
  
    Bien que ce paramètre soit facultatif, sa définition peut entraîner des calculs plus efficaces. La plupart des fonctions analytiques améliorées dans **RevoScaleR** et **MicrosoftML** traitent les données en segments. Le paramètre *rowsPerRead* détermine le nombre de lignes dans chaque segment.
  
    Vous devrez peut-être expérimenter ce paramètre pour trouver le bon équilibre. Si la valeur est trop grande, l’accès aux données peut être lent s’il n’y a pas assez de mémoire pour traiter les données en segments de cette taille. À l’inverse, sur certains systèmes, si la valeur de *rowsPerRead* est trop petite, les performances peuvent également être ralenties.
  
    Comme valeur initiale, utilisez la taille du processus de traitement par lots par défaut définie par l’instance du moteur de base de données pour contrôler le nombre de lignes dans chaque segment (5 000 lignes). Enregistrez cette valeur dans la variable *sqlRowsPerRead*.
  
4.  Définissez une variable pour le nouvel objet de source de données et transmettez les arguments définis précédemment au constructeur **RxSqlServerData** . Notez que cette opération ne fait que créer l’objet de source de données, elle ne le remplit pas. Le chargement des données est une étape distincte.
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlFraudTable,
       rowsPerRead = sqlRowsPerRead)
    ```

## <a name="create-the-scoring-data-table"></a>Créer la table de données de notation

À l’aide des mêmes étapes, créez la table qui contient les données de calcul de score en utilisant le même processus.

1. Créez une variable R, *sqlScoreTable*, pour stocker le nom de la table utilisée pour le calcul de score.
  
    ```R
    sqlScoreTable <- "ccFraudScoreSmall"
    ```
  
2. Fournissez cette variable comme argument à la fonction **RxSqlServerData** pour définir un deuxième objet de source de données ( *sqlScoreDS*).
  
    ```R
    sqlScoreDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlScoreTable, rowsPerRead = sqlRowsPerRead)
    ```

Étant donné que vous avez déjà défini la chaîne de connexion et d’autres paramètres en tant que variables dans l’espace de travail R, vous pouvez la réutiliser pour de nouvelles sources de données représentant différentes tables, vues ou requêtes.

> [!NOTE]
> La fonction utilise différents arguments pour définir une source de données basée sur une table entière plutôt que sur une source de données basée sur une requête. Cela est dû au fait que le moteur de base de données SQL Server doit préparer les requêtes différemment. Plus loin dans ce didacticiel, vous allez apprendre à créer un objet source de données basé sur une requête SQL.

## <a name="load-data-into-sql-tables-using-r"></a>Charger des données dans des tables SQL à l’aide de R

Maintenant que vous avez créé les tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous pouvez y charger des données à l’aide de la fonction **Rx** appropriée.

Le package **RevoScaleR** contient des fonctions spécifiques aux types de sources de données. Pour les données de texte, utilisez [RxTextData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxtextdata) pour générer l’objet de source de données. Il existe des fonctions supplémentaires pour créer des objets de source de données à partir des données Hadoop, des données ODBC et ainsi de suite.

> [!NOTE]
> Pour cette section, vous devez disposer d’autorisations d' **exécution DDL** sur la base de données.

### <a name="load-data-into-the-training-table"></a>Charger des données dans la table de formation

1. Créez une variable R, *ccFraudCsv*, et assignez à la variable le chemin d’accès du fichier csv contenant les exemples de données. Ce jeu de données est fourni dans **RevoScaleR**. «SampleDataDir» est un mot clé sur la fonction **rxGetOption** .
  
    ```R
    ccFraudCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudSmall.csv")
    ```
  
    Notez l’appel à **rxGetOption**, qui est la méthode d’extraction associée à [rxOptions](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxoptions) dans **RevoScaleR**. Utilisez cet utilitaire pour définir et répertorier les options relatives aux contextes de calcul locaux et distants, tels que le répertoire partagé par défaut, ou le nombre de processeurs (cœurs) à utiliser dans les calculs.
    
    Cet appel permet d’obtenir les exemples de la bibliothèque appropriée, quel que soit l’emplacement d’exécution de votre code. Par exemple, essayez d’exécuter la fonction sur SQL Server et sur votre ordinateur de développement, et voyez comment les chemins diffèrent.
  
2. Définissez une variable pour stocker les nouvelles données et utilisez la fonction **RxTextData** pour spécifier la source de données texte.
  
    ```R
    inTextData <- RxTextData(file = ccFraudCsv,      colClasses = c(
        "custID" = "integer", "gender" = "integer", "state" = "integer",
        "cardholder" = "integer", "balance" = "integer",
        "numTrans" = "integer",
        "numIntlTrans" = "integer", "creditLine" = "integer",
        "fraudRisk" = "integer"))
    ```
  
    L’argument *colClasses* est important. Vous l’utilisez pour indiquer le type de données à affecter à chaque colonne de données chargées à partir du fichier texte. Dans cet exemple, toutes les colonnes sont gérées comme du texte, sauf les colonnes nommées qui sont gérées comme des entiers.
  
3. À ce stade, vous souhaiterez peut-être suspendre un moment et afficher votre base [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]de données dans. Actualisez la liste de tables dans la base de données.
  
    Vous pouvez constater que, même si les objets de données R ont été créés dans votre espace de travail local, les tables n’ont [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pas été créées dans la base de données. En outre, aucune donnée n’a été chargée à partir du fichier texte dans la variable R.
  
4. Insérez les données en appelant la fonction [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) function.
  
    ```R
    rxDataStep(inData = inTextData, outFile = sqlFraudDS, overwrite = TRUE)
    ```
    
    En supposant que votre chaîne de connexion n’ait rencontré aucun problème, après une courte pause, vous devez voir les résultats suivants :
  
    *Nombre total de lignes écrites: 10000, temps total:*  0,466*lignes lues: 10000, nombre total de lignes traitées: 10000, durée totale du segment: 0,577 secondes*
  
5. Actualisez la liste des tables. Pour vérifier que chaque variable possède les types de données corrects et a été correctement importée, vous pouvez également cliquer [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] avec le bouton droit sur la table dans et sélectionner **Sélectionner les 1000 premières lignes**.

### <a name="load-data-into-the-scoring-table"></a>Charger des données dans la table de scores

1. Répétez les étapes pour charger le jeu de données utilisé pour le calcul de score dans la base de données.
  
    Commencez par fournir le chemin du fichier source.
  
    ```R
    ccScoreCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudScoreSmall.csv")
    ```
  
2. Utilisez la fonction **RxTextData** pour obtenir les données et les enregistrer dans la variable *inTextData*.
  
    ```R
    inTextData <- RxTextData(file = ccScoreCsv,      colClasses = c(
        "custID" = "integer", "gender" = "integer", "state" = "integer",
        "cardholder" = "integer", "balance" = "integer",
        "numTrans" = "integer",
        "numIntlTrans" = "integer", "creditLine" = "integer"))
    ```
  
3.  Appelez la fonction **rxDataStep** pour remplacer la table actuelle par le nouveau schéma et les nouvelles données.
  
    ```R
    rxDataStep(inData = inTextData, sqlScoreDS, overwrite = TRUE)
    ```
  
    - L’argument *inData* définit la source de données à utiliser.
  
    - L’argument *outFile* spécifie la table de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans laquelle vous voulez enregistrer les données.
  
    - Si la table existe déjà et que vous n’utilisez pas l’option de *remplacement* , les résultats sont insérés sans troncation.
  
Là encore, si la connexion a réussi, vous devez voir un message indiquant l’achèvement et le temps qui a été nécessaire à l’écriture des données dans la table :

*Nombre total de lignes écrites: 10000, temps total: 0,384*
ligneslues *: 10000, nombre total de lignes traitées: 10000, durée totale du segment: 0,456 secondes*

## <a name="more-about-rxdatastep"></a>En savoir plus sur rxDataStep

[rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) est une fonction puissante qui peut effectuer plusieurs transformations sur une trame de données R. Vous pouvez également utiliser rxDataStep pour convertir des données dans la représentation requise par la destination: dans ce cas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)],.

Si vous le souhaitez, vous pouvez spécifier des transformations sur les données, en utilisant des fonctions R dans les arguments de **rxDataStep**. Des exemples de ces opérations sont fournis plus loin dans ce didacticiel.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Interroger et modifier les données SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)