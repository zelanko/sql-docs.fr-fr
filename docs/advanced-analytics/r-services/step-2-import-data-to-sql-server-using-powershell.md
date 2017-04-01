---
title: "&#201;tape 2 : Importer des donn&#233;es dans SQL Server &#224; l’aide de PowerShell (Didacticiel sur l’analytique avanc&#233;e en base de donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "08/05/2016"
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
  - "TSQL"
ms.assetid: 3c5b5145-fa57-455a-b153-0400fc062dc0
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# &#201;tape 2 : Importer des donn&#233;es dans SQL Server &#224; l’aide de PowerShell (Didacticiel sur l’analytique avanc&#233;e en base de donn&#233;es)
Dans cette étape, vous allez exécuter un des scripts téléchargés pour créer les objets de base de données nécessaires à la procédure pas à pas. Le script crée également la plupart des procédures stockées que vous allez utiliser et charge les données d’exemple sur une table de la base de données que vous avez spécifiée.  
  
## Exécuter les scripts pour créer des objets SQL  
Parmi les fichiers téléchargés, vous devriez voir un script PowerShell. Pour préparer l’environnement à la procédure pas à pas, vous allez exécuter ce script.  
  
Les actions effectuées par le script sont les suivantes :  
  
-   Installation des utilitaires en ligne de commande SQL et SQL Native Client, si ce n’est déjà fait. Ces utilitaires sont nécessaires pour le chargement en bloc des données sur la base de données à l’aide de **bcp**.  
  
-   Création d’une base de données et d’une table sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et insertion en bloc des données dans la table.  
  
-   Création de plusieurs procédures stockées et fonctions SQL.  
  
#### Pour exécuter le script  
1.  Ouvrez une invite de commandes PowerShell comme administrateur et exécutez la commande suivante :  
  
    ```  
    .\RunSQL_SQL_Walkthrough.ps1  
    ```  
  
    Vous serez invité à entrer les informations suivantes :  
  
    -   Le nom ou l’adresse d’une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] où [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] a été installé.  
  
    -   Les nom d’utilisateur et mot de passe d’un compte sur l’instance. Le compte que vous utilisez doit pouvoir créer des bases de données, des tables et des procédures stockées, et charger des données sur les tables.  
  
    -   Le chemin et le nom du fichier de données exemple que vous venez de télécharger. Par exemple :  
  
        `C:\tempRSQL\nyctaxi1pct.csv`  
  
2.  Dans le cadre de cette étape, tous les scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] ont été modifiés pour remplacer les espaces réservés par le nom de la base de données et le nom d’utilisateur que vous fournissez comme entrées de script.  
  
    Prenez une minute pour passer en revue les procédures stockées et les fonctions créées par le script.  
  
    |||  
    |-|-|  
    |**Nom de fichier de script SQL**|**Fonction**|  
    |create-db-tb-upload-data.sql|Crée une base de données et deux tables :<br /><br />nyctaxi_sample : contient le dataset sur les taxis de New York (NYC Taxi). Un index cluster columnstore est ajouté à la table pour améliorer les performances du stockage et des requêtes. L’échantillon de 1 % du dataset NYC Taxi sera inséré dans cette table.<br /><br />nyc_taxi_models : permet de rendre persistant le modèle d’analytique avancée formé.|  
    |fnCalculateDistance.sql|Crée une fonction scalaire qui calcule la distance directe entre les lieux de prise en charge et de dépose.|  
    |fnEngineerFeatures.sql|Crée une fonction table qui crée des caractéristiques de données pour la formation du modèle.|  
    |PersistModel.sql|Crée une procédure stockée qui peut être appelée pour enregistrer un modèle. La procédure stockée prend un modèle qui a été sérialisé dans un type de données varbinary et l’écrit dans la table spécifiée.|  
    |PredictTipBatchMode.sql|Crée une procédure stockée qui appelle le modèle formé pour créer des prédictions à l’aide du modèle. La procédure stockée accepte une requête comme paramètre d’entrée et retourne une colonne de valeurs numériques qui contient les scores pour les lignes d’entrée.|  
    |PredictTipSingleMode.sql|Crée une procédure stockée qui appelle le modèle formé pour créer des prédictions à l’aide du modèle. Cette procédure stockée accepte une nouvelle observation comme entrée, avec des valeurs de caractéristiques passées comme paramètres inline, et retourne une valeur qui prédit l’issue de la nouvelle observation.|  
  
    Vous allez créer des procédures stockées supplémentaires dans la dernière partie de cette procédure pas à pas :  
  
    |||  
    |-|-|  
    |**Nom de fichier de script SQL**|**Fonction**|  
    |PlotHistogram.sql|Crée une procédure stockée pour l’exploration des données. Cette procédure stockée appelle une fonction R pour tracer l’histogramme d’une variable, puis retourne le traçage sous forme d’objet binaire.|  
    |PlotInOutputFiles.sql|Crée une procédure stockée pour l’exploration des données. Cette procédure stockée crée un graphique à l’aide d’une fonction R, puis enregistre la sortie dans un fichier PDF local.|  
    |TrainTipPredictionModel.sql|Crée une procédure stockée qui forme un modèle de régression logistique en appelant un package R. Le modèle prédit la valeur de la colonne tipped et est formé à l’aide d’un échantillon de 70 % des données sélectionné de façon aléatoire. La sortie de la procédure stockée représente le modèle formé, qui est enregistré dans la table nyc_taxi_models.|  
  
3.  Connectez-vous à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et du compte de connexion que vous avez spécifié, pour vérifier que vous pouvez voir la base de données, les tables, les fonctions et les procédures stockées qui ont été créées.  
  
    ![rsql_devtut_BrowseTables](../../advanced-analytics/r-services/media/rsql-devtut-browsetables.PNG "rsql_devtut_BrowseTables")  
  
    > [!NOTE]  
    > Si les objets de base de données existent déjà, ils ne peuvent pas être recréés.  
    >   
    > Si la table existe déjà, les données sont ajoutées, pas remplacées. Ainsi, pensez à supprimer tout objet avant d’exécuter le script.  
  
## Étape suivante  
[Étape 3 : Explorer et visualiser les données](../../advanced-analytics/r-services/step-3-explore-and-visualize-the-data-in-database-advanced-analytics-tutorial.md)  
  
## Étape précédente  
[Étape 1 : Télécharger les exemples de données](../../advanced-analytics/r-services/step-1-download-the-sample-data-in-database-advanced-analytics-tutorial.md)  
  
## Voir aussi  
[Analytique avancée en base de données pour les développeurs SQL &#40;Didacticiel&#41;](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[Didacticiels pour SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
