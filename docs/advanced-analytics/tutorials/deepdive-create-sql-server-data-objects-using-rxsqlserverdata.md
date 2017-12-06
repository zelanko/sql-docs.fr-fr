---
title: "Créer des objets de données SQL Server à l’aide de RxSqlServerData | Microsoft Docs"
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: bcf5f7ff-795b-4815-b163-bcddd496efce
caps.latest.revision: "18"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: c6208de7eedf66640ab2b8131a4b73c51e6fbaba
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="create-sql-server-data-objects-using-rxsqlserverdata"></a>Créer des objets de données SQL Server à l’aide de RxSqlServerData

Maintenant que vous avez créé la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et que vous disposez des autorisations nécessaires pour utiliser les données, vous allez créer des objets en code R pour pouvoir utiliser les données sur le serveur et sur votre station de travail.

## <a name="create-the-sql-server-data-objects"></a>Créer les objets de données SQL Server

Dans cette étape, vous allez créer et remplir deux tables. Les deux tables contiennent des données simulées de fraude de carte de crédit. Une table est utilisée pour former les modèles et l’autre pour le calcul de score.

Pour créer des tables sur l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] distant, vous utilisez la fonction **RxSqlServerData** fournie dans le package **RevoScaleR** .

> [!TIP]
> Si vous utilisez les outils R pour Visual Studio, sélectionnez **Outils R** dans la barre d’outils, puis cliquez sur **Windows** pour afficher les options pour le débogage et l’affichage des variables R.

### <a name="create-the-training-data-table"></a>Créer la table de données d’apprentissage

1. Fournissez votre chaîne de connexion de base de données dans une variable R. Nous vous proposons deux exemples de chaînes de connexion ODBC valides pour SQL Server : une qui utilise une connexion SQL et une pour l’authentification intégrée de Windows (recommandée).

    **Utilisation d’une connexion SQL**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name; Database=DeepDive;Uid=user_name;Pwd=password"
    ```

    **Avec l’authentification Windows**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=DeepDive;Trusted_Connection=True"
    ```

    Veillez à modifier le nom d’instance, le nom de base de données, le nom d’utilisateur et le mot de passe comme il convient.
  
2. Spécifiez le nom de la table que vous voulez créer et enregistrez-le dans une variable R.
  
    ```R
    sqlFraudTable <- "ccFraudSmall"
    ```
  
    Étant donné que les noms d’instances et de bases de données sont déjà spécifiés dans la chaîne de connexion, quand vous combinez les deux variables, le nom *complet* de la nouvelle table devient _instance.database.schema.ccFraudSmall_.
  
3.  Avant d’instancier l’objet de source de données, ajoutez une ligne spécifiant un paramètre supplémentaire, *rowsPerRead*.  Le paramètre *rowsPerRead* contrôle le nombre de lignes de données lues dans chaque lot.
  
    ```R
    sqlRowsPerRead = 5000
    ```
  
    Bien que ce paramètre soit facultatif, il est important pour gérer l’utilisation de la mémoire et pour l’efficacité des calculs.  La plupart des fonctions analytiques améliorées dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] traitent les données en segments et cumulent les résultats intermédiaires. Elles retournent les calculs finaux une fois que toutes les données ont été lues.
  
    Si la valeur de ce paramètre est trop grande, l’accès aux données peut être lent, car vous n’avez pas suffisamment de mémoire pour traiter efficacement un segment de données aussi volumineux.  Sur certains systèmes, si la valeur de *rowsPerRead* est trop basse, les performances peuvent être ralenties.
  
    Dans cette procédure pas à pas, vous utilisez la taille du processus de traitement par lots définie par l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour contrôler le nombre de lignes dans chaque segment, puis vous enregistrez cette valeur dans la variable *sqlRowsPerRead*.  Nous vous recommandons de tester ce paramètre sur votre système quand vous utilisez un dataset volumineux.
  
4.  Enfin, définissez une variable pour le nouvel objet de source de données et passez les arguments définis précédemment au constructeur RxSqlServerData. Notez que cette opération ne fait que créer l’objet de source de données, elle ne le remplit pas.
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlFraudTable,
       rowsPerRead = sqlRowsPerRead)
    ```

#### <a name="to-create-the-scoring-data-table"></a>Pour créer la table de données de calcul de score

Vous allez créer la table qui contient les données de calcul de score de la même façon.

1. Créez une variable R, *sqlScoreTable*, pour stocker le nom de la table utilisée pour le calcul de score.
  
    ```R
    sqlScoreTable <- "ccFraudScoreSmall"
    ```
  
2. Fournir cette variable en tant qu’argument à la fonction RxSqlServerData pour définir un second objet de source de données, *sqlScoreDS*.
  
    ```R
    sqlScoreDS \<- RxSqlServerData(connectionString = sqlConnString,
       table = sqlScoreTable, rowsPerRead = sqlRowsPerRead)
    ```

Dans la mesure où vous avez déjà défini la chaîne de connexion et d’autres paramètres comme variables dans l’espace de travail R, il est facile de créer des sources de données pour différentes tables, vues ou requêtes. Il suffit de spécifier un autre nom de table.

Plus loin dans ce didacticiel, vous allez apprendre à créer un objet de source de données basé sur une requête SQL.

## <a name="load-data-into-sql-tables-using-r"></a>Charger des données dans des tables SQL à l’aide de R

Maintenant que vous avez créé les tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous pouvez y charger des données à l’aide de la fonction **Rx** appropriée.

Le **RevoScaleR** package contient des fonctions qui prennent en charge de différentes sources de données : pour les données texte, vous allez utiliser RxTextData pour générer l’objet de source de données. Il existe des fonctions supplémentaires pour créer des objets de source de données à partir des données Hadoop, des données ODBC et ainsi de suite.

> [!NOTE]
> Pour cette section, vous devez disposer des autorisations d’exécution de DDL sur la base de données.

### <a name="load-data-into-the-training-table"></a>Charger des données dans la table de formation

1. Créez une variable R, *ccFraudCsv*et affectez à la variable, le chemin d’accès de fichier pour le fichier CSV contenant les exemples de données.
  
    ```R
    ccFraudCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudSmall.csv")
    ```
  
    Notez la fonction utilitaire **rxGetOption**. Cette fonction est fournie dans le package **RevoScaleR** pour vous aider à définir et gérer les options relatives aux contextes de calcul locaux et distants, tels que le répertoire partagé par défaut, le nombre de processeurs (noyaux) à utiliser dans les calculs, etc.  Cet appel est utile, car il obtient les exemples à partir de la bibliothèque appropriée, quelle que soit l’où vous exécutez votre code. Par exemple, essayez d’exécuter la fonction sur SQL Server et sur votre ordinateur de développement, et voyez comment les chemins diffèrent.
  
2. Définir une variable pour stocker les nouvelles données et utiliser la fonction RxTextData pour spécifier la source de données de texte.
  
    ```R
    inTextData <- RxTextData(file = ccFraudCsv,      colClasses = c(
        "custID" = "integer", "gender" = "integer", "state" = "integer",
        "cardholder" = "integer", "balance" = "integer",
        "numTrans" = "integer",
        "numIntlTrans" = "integer", "creditLine" = "integer",
        "fraudRisk" = "integer"))
    ```
  
    L’argument *colClasses* est important. Vous l’utilisez pour indiquer le type de données à affecter à chaque colonne de données chargées à partir du fichier texte. Dans cet exemple, toutes les colonnes sont gérées comme du texte, sauf les colonnes nommées qui sont gérées comme des entiers.
  
3. À ce stade, vous souhaiterez peut-être suspendre un moment et d’afficher votre base de données dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  Actualisez la liste de tables dans la base de données.
  
    Vous constatez que même si les objets de données R ont été créés dans votre espace de travail local, les tables n’ont pas encore été créées dans la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . En outre, aucune donnée n’a été chargée à partir du fichier texte dans la variable de R.
  
4. À présent, appelez la fonction **rxDataStep** pour insérer les données dans la table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    rxDataStep(inData = inTextData, outFile = sqlFraudDS, overwrite = TRUE)
    ```
  
    En supposant que votre chaîne de connexion n’ait rencontré aucun problème, après une courte pause, vous devez voir les résultats suivants :
  
      *Nombre total de lignes écrites : 10000, Durée totale : 0,466*

      *Lignes lues : 10000, Total des lignes traitées : 10000, Durée totale du segment : 0,577 seconde*
  
5. À l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], actualisez la liste de tables. Pour vérifier que chaque variable possède les types de données correct et qu’il a été importé avec succès, vous pouvez cliquer également sur la table dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et sélectionnez **sélectionnez 1000 lignes du haut**.

### <a name="load-data-into-the-scoring-table"></a>Charger des données dans la table calcul de score

1. Vous suivez la même procédure pour charger dans la base de données le jeu de données utilisé pour le calcul de score.
  
    Commencez par fournir le chemin du fichier source.
  
    ```R
    ccScoreCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudScoreSmall.csv")
    ```
  
2. Utilisez la fonction de RxTextData pour obtenir les données et l’enregistrer dans la variable, *inTextData*.
  
    ```R
    inTextData <- RxTextData(file = ccScoreCsv,      colClasses = c(
        "custID" = "integer", "gender" = "integer", "state" = "integer",
        "cardholder" = "integer", "balance" = "integer",
        "numTrans" = "integer",
        "numIntlTrans" = "integer", "creditLine" = "integer"))
    ```
  
3.  Appelez la fonction rxDataStep pour remplacer la table actuelle avec le nouveau schéma et les données.
  
    ```R
    rxDataStep(inData = inTextData, sqlScoreDS, overwrite = TRUE)
    ```
  
    - L’argument *inData* définit la source de données à utiliser.
  
    - L’argument *outFile* spécifie la table de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans laquelle vous voulez enregistrer les données.
  
    - Si la table existe déjà et que vous n’utilisez pas l’option *remplacer* , les résultats sont insérés sans troncation.
  
Là encore, si la connexion a réussi, vous devez voir un message indiquant l’achèvement et le temps qui a été nécessaire à l’écriture des données dans la table :

*Nombre total de lignes écrites : 10000, Durée totale : 0,384*

*Lignes lues : 10000, Total des lignes traitées : 10000, Durée totale du segment : 0,456 seconde*

## <a name="more-about-rxdatastep"></a>En savoir plus sur rxDataStep

Le **rxDataStep** est une fonction puissante qui peut effectuer plusieurs transformations sur une trame de données R, pour convertir les données dans la représentation sous forme de requis par la destination. Dans ce cas, la destination est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Vous pouvez également spécifier des transformations sur les données, à l’aide des fonctions R dans les arguments de rxDataStep. Vous verrez des exemples de ces opérations plus tard.

## <a name="next-step"></a>Étape suivante

[Interroger et modifier les données du serveur SQL](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)

## <a name="previous-step"></a>Étape précédente

[Travailler avec des données SQL Server à l’aide de R](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)

