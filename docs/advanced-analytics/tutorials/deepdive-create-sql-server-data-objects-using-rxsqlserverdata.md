---
title: Créer des objets de données SQL Server à l’aide de RevoScaleR RxSqlServerData - SQL Server Machine Learning
description: Didacticiel pas à pas sur la façon de créer des objets de données à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 45643dbcdc2876fe0794ddb731abe6334537169c
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510356"
---
# <a name="create-sql-server-data-objects-using-rxsqlserverdata-sql-server-and-revoscaler-tutorial"></a>Créer des objets de données SQL Server à l’aide de RxSqlServerData (didacticiel sur SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cette leçon fait partie de la [RevoScaleR didacticiel](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Leçon deux est la suite de la création de base de données : ajout de tables et le chargement des données. Si un DBA créé la base de données et le compte de connexion dans [une leçon](deepdive-work-with-sql-server-data-using-r.md), vous pouvez ajouter des tables à l’aide d’un IDE R comme RStudio ou un outil intégré comme **Rgui**.

À partir de R, connectez-vous à SQL Server et utilisez **RevoScaleR** fonctions pour effectuer les tâches suivantes :

> [!div class="checklist"]
> * Créer des tables pour les données d’apprentissage et de prédictions
> * Charger des tables avec des données à partir d’un fichier .csv local

Exemples de données est partitionnées en apprentissage et l’évaluation des jeux de données des données de fraude simulé de carte de crédit (le dataset ccFraud). Le fichier de données est inclus dans **RevoScaleR**.

Utiliser un IDE R ou **Rgui** pour effectuer ces tâches. Veillez à utiliser les fichiers exécutables R trouvées à cet emplacement : C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64 (soit Rgui.exe si vous utilisez cet outil, ou un IDE R pointant vers C:\Program Files\Microsoft\R Client\R_SERVER). Avoir un [station de travail cliente R](../r/set-up-a-data-science-client.md) avec ces exécutables sont considéré comme une condition préalable de ce didacticiel.

## <a name="create-the-training-data-table"></a>Créer la table de données de formation

1. Store de la chaîne de connexion de base de données dans une variable R. Voici deux exemples de chaînes de connexion ODBC valides pour SQL Server : une à l’aide d’une connexion SQL et une pour l’authentification intégrée Windows. 

   Veillez à modifier le nom du serveur, le nom d’utilisateur et le mot de passe comme il convient.

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
  
    Étant donné que l’instance de serveur et nom de la base de données sont déjà spécifiés dans la chaîne de connexion, lorsque vous combinez les deux variables, la *complet* nom de la nouvelle table devient  *instance.database.schema.ccFraudSmall*.
  
3.  Si vous le souhaitez, spécifier *rowsPerRead* pour contrôler le nombre de lignes de données est lues dans chaque lot.
  
    ```R
    sqlRowsPerRead = 5000
    ```
  
    Bien que ce paramètre est facultatif, configurez-la peut entraîner des calculs plus efficaces. La plupart des fonctions analytiques améliorées dans **RevoScaleR** et **MicrosoftML** traiter les données dans des segments. Le *rowsPerRead* paramètre détermine le nombre de lignes dans chaque segment.
  
    Vous devrez peut-être faire des essais avec ce paramètre pour trouver le juste équilibre. Si la valeur est trop grande, accès aux données peut être lente si la mémoire n’est pas suffisante pour traiter les données dans des segments de cette taille. À l’inverse, sur certains systèmes, si la valeur de *rowsPerRead* est trop petite, les performances peuvent également ralentir.
  
    Comme une valeur initiale, utilisez la taille de processus de lot par défaut définie par l’instance du moteur de base de données pour contrôler le nombre de lignes dans chaque segment (5 000 lignes). Enregistrez cette valeur dans la variable *sqlRowsPerRead*.
  
4.  Définissez une variable pour le nouvel objet de source de données et passez les arguments définis précédemment au **RxSqlServerData** constructeur. Notez que cette opération ne fait que créer l’objet de source de données, elle ne le remplit pas. Le chargement des données est une étape distincte.
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlFraudTable,
       rowsPerRead = sqlRowsPerRead)
    ```

## <a name="create-the-scoring-data-table"></a>Créer la table de données de notation

À l’aide de la même procédure, créez la table qui contient les données de notation en utilisant le même processus.

1. Créez une variable R, *sqlScoreTable*, pour stocker le nom de la table utilisée pour le calcul de score.
  
    ```R
    sqlScoreTable <- "ccFraudScoreSmall"
    ```
  
2. Fournissez cette variable comme argument à la fonction **RxSqlServerData** pour définir un deuxième objet de source de données ( *sqlScoreDS*).
  
    ```R
    sqlScoreDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlScoreTable, rowsPerRead = sqlRowsPerRead)
    ```

Étant donné que vous avez déjà défini la chaîne de connexion et d’autres paramètres comme variables dans l’espace de travail R, vous pouvez le réutiliser pour des sources de données représentant les différentes tables, des vues ou des requêtes.

> [!NOTE]
> La fonction utilise des arguments différents pour la définition d’une source de données basée sur une table entière que pour une source de données basée sur une requête. Il s’agit, car le moteur de base de données SQL Server doit préparer les requêtes différemment. Plus loin dans ce didacticiel, vous allez apprendre à créer un objet de source de données basé sur une requête SQL.

## <a name="load-data-into-sql-tables-using-r"></a>Charger des données dans des tables SQL à l’aide de R

Maintenant que vous avez créé les tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous pouvez y charger des données à l’aide de la fonction **Rx** appropriée.

Le **RevoScaleR** package contient des fonctions spécifiques aux types de source de données. Pour les données de texte, utilisez [RxTextData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxtextdata) pour générer l’objet de source de données. Il existe des fonctions supplémentaires pour créer des objets de source de données à partir des données Hadoop, des données ODBC et ainsi de suite.

> [!NOTE]
> Dans cette section, vous devez avoir **DDL d’exécution** autorisations sur la base de données.

### <a name="load-data-into-the-training-table"></a>Charger des données dans la table d’apprentissage

1. Créez une variable R, *ccFraudCsv*et affectez à la variable le chemin d’accès de fichier pour le fichier CSV contenant les exemples de données. Ce jeu de données est fourni dans **RevoScaleR**. Le « sampleDataDir » est un mot clé sur le **rxGetOption** (fonction).
  
    ```R
    ccFraudCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudSmall.csv")
    ```
  
    Notez l’appel à **rxGetOption**, qui est la méthode GET associée [rxOptions](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxoptions) dans **RevoScaleR**. Cet utilitaire permet de définir et répertorient les options relatives aux contextes de calcul locaux et distants, tels que le répertoire partagé par défaut, ou le nombre de processeurs (cœurs) à utiliser dans les calculs.
    
    Cet appel particulier Obtient les exemples à partir de la bibliothèque appropriée, quel que soit l’où vous exécutez votre code. Par exemple, essayez d’exécuter la fonction sur SQL Server et sur votre ordinateur de développement, et voyez comment les chemins diffèrent.
  
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
  
3. À ce stade, vous souhaiterez peut-être mettre en pause un moment et afficher votre base de données dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Actualisez la liste de tables dans la base de données.
  
    Vous pouvez voir que, bien que les objets de données R ont été créés dans votre espace de travail local, les tables n'ont pas été créées dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données. En outre, aucune donnée n’a été chargée à partir du fichier texte dans la variable R.
  
4. Insérer les données en appelant la fonction [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) (fonction).
  
    ```R
    rxDataStep(inData = inTextData, outFile = sqlFraudDS, overwrite = TRUE)
    ```
    
    En supposant que votre chaîne de connexion n’ait rencontré aucun problème, après une courte pause, vous devez voir les résultats suivants :
  
    *Total lignes écrites : 10000, durée totale : 0,466* *lignes lues : 10000, total des lignes traitées : 10000, durée du segment total : 0,577 seconde*
  
5. Actualiser la liste des tables. Pour vérifier que chaque variable possède les types de données correcte et a été importé avec succès, vous pouvez également cliquer sur la table dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et sélectionnez **sélectionner les 1000 premières lignes**.

### <a name="load-data-into-the-scoring-table"></a>Charger des données dans la table calcul de score

1. Répétez les étapes pour charger le jeu de données utilisé pour calculer les scores dans la base de données.
  
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
  
    - Si la table existe déjà et que vous n’utilisez pas le *remplacer* option, résultats sont insérés sans troncation.
  
Là encore, si la connexion a réussi, vous devez voir un message indiquant l’achèvement et le temps qui a été nécessaire à l’écriture des données dans la table :

*Total lignes écrites : 10000, durée totale : 0,384*
*lignes lues : 10000, total des lignes traitées : 10000, durée du segment total : 0,456 seconde*

## <a name="more-about-rxdatastep"></a>En savoir plus sur rxDataStep

[rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) est une fonction puissante qui peut effectuer plusieurs transformations sur une trame de données R. Vous pouvez également utiliser rxDataStep pour convertir des données en une représentation demandée par la destination : dans ce cas, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Si vous le souhaitez, vous pouvez spécifier des transformations sur les données, à l’aide des fonctions R dans les arguments de **rxDataStep**. Exemples de ces opérations sont fournis plus loin dans ce didacticiel.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Interroger et modifier les données SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)