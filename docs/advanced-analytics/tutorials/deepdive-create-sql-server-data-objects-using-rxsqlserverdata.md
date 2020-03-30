---
title: Créer des objets RxSqlServerData
description: 'Tutoriel RevoScaleR 2 : Comment créer des objets de données avec le langage R sur SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7869fc3fc67cb24542223c2300cd7b6ebcf1eb41
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "76922569"
---
# <a name="create-sql-server-data-objects-using-rxsqlserverdata-sql-server-and-revoscaler-tutorial"></a>Créer des objets de données SQL Server avec RxSqlServerData (tutoriel SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Il s’agit du tutoriel 2 de la [série de tutoriels RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) qui traite de l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Ce tutoriel est la suite de la création d’une base de données : ajout de tables et chargement de données. Si un administrateur de base de données a créé la base de données et la connexion dans le [tutoriel 2](deepdive-work-with-sql-server-data-using-r.md), vous pouvez ajouter des tables en utilisant un IDE R comme RStudio ou un outil intégré comme **Rgui**.

Dans R, connectez-vous à SQL Server et utilisez des fonctions **RevoScaleR** pour effectuer les tâches suivantes :

> [!div class="checklist"]
> * Créer des tables pour les données d’entraînement et les prédictions
> * Charger des tables avec des données à partir d’un fichier .csv local

Les exemples de données sont des données simulées de fraude à la carte de crédit (le jeu de données ccFraud), partitionnées en jeux de données d’entraînement et de scoring. Le fichier de données est inclus dans **RevoScaleR**.

Utilisez un IDE R ou **Rgui** pour effectuer ces tâches. Veillez à utiliser les exécutables R qui se trouvent à cet emplacement : C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64 (Rgui.exe si vous utilisez cet outil ou un IDE R pointant vers C:\Program Files\Microsoft\R Client\R_SERVER). Le fait de disposer d’une [station de travail cliente R](../r/set-up-a-data-science-client.md) avec ces fichiers exécutables est considéré comme un prérequis de ce tutoriel.

## <a name="create-the-training-data-table"></a>Créer la table de données d’entraînement

1. Stockez la chaîne de connexion de base de données dans une variable R. Voici deux exemples de chaînes de connexion ODBC valides pour SQL Server : une qui utilise une connexion SQL et une pour l’authentification intégrée de Windows. 

   Veillez à modifier le nom du serveur, le nom d’utilisateur et le mot de passe de façon appropriée.

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
  
    Comme l’instance du serveur et le nom de la base de données sont déjà spécifiés dans la chaîne de connexion, quand vous combinez les deux variables, le nom *complet* de la nouvelle table devient *instance.base_de_données.schéma.ccFraudSmall*.
  
3.  Vous pouvez aussi spécifier *rowsPerRead* pour contrôler le nombre de lignes de données lues dans chaque lot.
  
    ```R
    sqlRowsPerRead = 5000
    ```
  
    Bien que ce paramètre soit facultatif, sa définition peut aboutir à des calculs plus efficaces. La plupart des fonctions analytiques améliorées dans **RevoScaleR** et **MicrosoftML** traitent les données en segments. Le paramètre *rowsPerRead* détermine le nombre de lignes dans chaque segment.
  
    Il peut être nécessaire de faire des expériences avec ce paramètre pour trouver le bon équilibre. Si la valeur est trop grande, l’accès aux données peut être ralenti s’il n’y a pas assez de mémoire pour traiter les données en segments de cette taille. À l’inverse, sur certains systèmes, si la valeur de *rowsPerRead* est trop faible, les performances peuvent également être ralenties.
  
    Comme valeur initiale, utilisez la taille du processus de traitement par lot par défaut définie par l’instance du moteur de base de données pour contrôler le nombre de lignes dans chaque segment (5 000 lignes). Enregistrez cette valeur dans la variable *sqlRowsPerRead*.
  
4.  Définissez une variable pour stocker le nouvel objet de source de données et passez les arguments définis précédemment au constructeur **RxSqlServerData**. Notez que cette opération ne fait que créer l’objet de source de données, elle ne le remplit pas. Le chargement des données est une étape distincte.
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlFraudTable,
       rowsPerRead = sqlRowsPerRead)
    ```

## <a name="create-the-scoring-data-table"></a>Créer la table de données de scoring

Utilisez les mêmes étapes pour créer la table qui contient les données de scoring.

1. Créez une variable R, *sqlScoreTable*, pour stocker le nom de la table utilisée pour le calcul de score.
  
    ```R
    sqlScoreTable <- "ccFraudScoreSmall"
    ```
  
2. Fournissez cette variable comme argument à la fonction **RxSqlServerData** pour définir un deuxième objet de source de données ( *sqlScoreDS*).
  
    ```R
    sqlScoreDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlScoreTable, rowsPerRead = sqlRowsPerRead)
    ```

Comme vous avez déjà défini la chaîne de connexion et d’autres paramètres comme variables dans l’espace de travail R, vous pouvez la réutiliser pour de nouvelles sources de données représentant différentes tables, vues ou requêtes.

> [!NOTE]
> La fonction utilise des arguments différents pour définir une source de données basée sur une table entière et pour une source de données basée sur une requête. La raison en est que le moteur de base de données SQL Server doit préparer les requêtes différemment. Plus loin dans ce tutoriel, vous découvrez comment créer un objet de source de données basé sur une requête SQL.

## <a name="load-data-into-sql-tables-using-r"></a>Charger des données dans des tables SQL avec R

Maintenant que vous avez créé les tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous pouvez y charger des données à l’aide de la fonction **Rx** appropriée.

Le package **RevoScaleR** contient des fonctions spécifiques aux types de sources de données. Pour les données texte, utilisez [RxTextData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxtextdata) pour générer l’objet de source de données. Il existe des fonctions supplémentaires pour créer des objets de source de données à partir des données Hadoop, des données ODBC et ainsi de suite.

> [!NOTE]
> Pour cette section, vous devez disposer des autorisations **Exécuter du DDL** sur la base de données.

### <a name="load-data-into-the-training-table"></a>Charger des données dans la table d’entraînement

1. Créez une variable R (*ccFraudCsv*), puis affectez à la variable le chemin du fichier CSV qui contient les exemples de données. Ce jeu de données est fourni dans **RevoScaleR**. « sampleDataDir » est un mot clé sur la fonction **rxGetOption**.
  
    ```R
    ccFraudCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudSmall.csv")
    ```
  
    Notez l’appel à **rxGetOption**, qui est la méthode GET associée à [rxOptions](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxoptions) dans **RevoScaleR**. Utilisez cet utilitaire pour définir et lister les options relatives aux contextes de calcul locaux et distants, comme le répertoire partagé par défaut ou le nombre de processeurs (cœurs) à utiliser dans les calculs.
    
    Cette appel particulier obtient les exemples à partir de la bibliothèque appropriée, quel que soit l’emplacement d’exécution de votre code. Par exemple, essayez d’exécuter la fonction sur SQL Server et sur votre ordinateur de développement, et voyez comment les chemins diffèrent.
  
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
  
3. À ce stade, vous pouvez faire une pause et visualiser votre base de données dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Actualisez la liste de tables dans la base de données.
  
    Vous pouvez voir que, même si les objets de données R ont été créés dans votre espace de travail local, les tables n’ont pas été créées dans la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. De même, aucune donnée du fichier texte n’a été chargée dans la variable R.
  
4. Insérez les données en appelant la fonction [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep).
  
    ```R
    rxDataStep(inData = inTextData, outFile = sqlFraudDS, overwrite = TRUE)
    ```
    
    En supposant que votre chaîne de connexion n’ait rencontré aucun problème, après une courte pause, vous devez voir les résultats suivants :
  
    *Total lignes écrites : 10 000, Durée totale : 0,466* *Lignes lues : 10 000, Nombre total de lignes traitées : 10 000, Durée totale de la segmentation : 0,577 secondes*
  
5. Actualisez la liste des tables. Pour vérifier que chaque variable a le type de données correct et qu’elle a été correctement importée, vous pouvez aussi cliquer avec le bouton droit sur la table dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et sélectionner **Sélectionner les 1 000 premières lignes**.

### <a name="load-data-into-the-scoring-table"></a>Charger les données dans la table de scoring

1. Répétez les étapes pour charger le jeu de données utilisé pour le scoring dans la base de données.
  
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
  
    - Si la table existe déjà et que vous n’utilisez pas l’option *overwrite*, les résultats sont insérés sans troncation.
  
Là encore, si la connexion a réussi, vous devez voir un message indiquant l’achèvement et le temps qui a été nécessaire à l’écriture des données dans la table :

*Total lignes écrites : 10 000, Durée totale : 0,384*
*Lignes lues : 10 000, Nombre total de lignes traitées : 10 000, Durée totale de la segmentation : 0,456 secondes*

## <a name="more-about-rxdatastep"></a>En savoir plus sur rxDataStep

[rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) est une fonction puissante qui peut effectuer plusieurs transformations sur une trame de données R. Vous pouvez également utiliser rxDataStep pour convertir des données dans la représentation nécessaire pour la destination, qui est dans le cas présent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Si vous le souhaitez, vous pouvez spécifier des transformations sur les données en utilisant des fonctions R dans les arguments de **rxDataStep**. Des exemples de ces opérations sont fournis plus loin dans ce tutoriel.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Interroger et modifier les données SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)