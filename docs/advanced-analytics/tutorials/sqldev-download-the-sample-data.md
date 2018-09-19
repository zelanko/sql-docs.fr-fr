---
title: Télécharger des données de démonstration NYC Taxi et de scripts pour embedded R et Python (SQL Server Machine Learning) | Microsoft Docs
description: Instructions de téléchargement des exemples de données New York City taxi et de création d’une base de données. Données sont utilisées dans les didacticiels de SQL Server montrant comment incorporer R et Python dans SQL Server des procédures stockées et fonctions T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/22/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7420476b20cef612c45227f66497ae554def7b1d
ms.sourcegitcommit: 9d0ff4f3e40db48fc01788684d34719065d159b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44724333"
---
# <a name="nyc-taxi-demo-data-for-sql-server"></a>Données de démonstration NYC Taxi pour SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article vous prépare votre système pour des didacticiels sur l’utilisation de R et Python pour l’analytique en base de données dans SQL Server.

Dans cet exercice, vous allez télécharger les exemples de données, un script PowerShell pour la préparation de l’environnement, et [!INCLUDE[tsql](../../includes/tsql-md.md)] fichiers de script utilisés dans plusieurs didacticiels. Lorsque vous avez terminé, un **NYCTaxi_Sample** base de données est disponible sur votre instance locale, en fournissant des données de démonstration pratique. 

## <a name="prerequisites"></a>Prérequis

Vous avez besoin une connexion internet, PowerShell et les droits d’administrateur local sur l’ordinateur. Vous devez avoir [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) ou un autre outil pour vérifier la création d’objets.

## <a name="download-nyc-taxi-demo-data-and-scripts-from-github"></a>Télécharger des données de démonstration NYC Taxi et les scripts à partir de Github

1.  Ouvrez une console de commande Windows PowerShell.
  
    Utilisez le **exécuter en tant qu’administrateur** option pour créer le répertoire de destination ou pour écrire des fichiers vers la destination spécifiée.
  
2.  Exécutez les commandes PowerShell suivantes, en définissant la valeur du paramètre *DestDir* sur un répertoire local. La valeur par défaut que nous avons utilisée ici est **TempRSQL**.
  
    ```ps
    $source = ‘https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/RSQL/Download_Scripts_SQL_Walkthrough.ps1’  
    $ps1_dest = “$pwd\Download_Scripts_SQL_Walkthrough.ps1”
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir ‘C:\tempRSQL’
    ```
  
    Si le dossier que vous spécifiez dans *DestDir* n’existe pas, il est créé par le script PowerShell.
  
    > [!TIP]
    > Si vous obtenez une erreur, vous pouvez temporairement définir la stratégie d’exécution des scripts PowerShell à **sans restriction** uniquement pour cette procédure pas à pas à l’aide de l’argument Bypass et les modifications apportées à la session active de portée.
    >   
    >````
    > Set\-ExecutionPolicy Bypass \-Scope Process
    >````
    > L’exécution de cette commande n’a pas d’incidence sur la configuration.
  
    Selon votre connexion Internet, le téléchargement peut prendre un certain temps.
  
3.  Lorsque tous les fichiers ont été téléchargées, le script PowerShell s’ouvre à la *DestDir* dossier. Dans l’invite de commandes PowerShell, exécutez la commande suivante et examinez les fichiers qui ont été téléchargés.
  
    ```
    ls
    ```
  
    **Résultats :**
  
    ![liste des fichiers téléchargés par le script PowerShell](media/rsql-devtut-filelist.png "liste des fichiers téléchargés par le script PowerShell")

## <a name="create-nyctaxisample-database"></a>Créer la base de données NYCTaxi_Sample

Parmi les fichiers téléchargés, vous devez voir un script PowerShell (**RunSQL_SQL_Walkthrough.ps1**) qui crée une base de données et de chargement en masse des données. Les actions effectuées par le script sont les suivantes :

+ Installe les utilitaires de ligne de commande SQL, SQL Native Client si pas déjà installé. Ces utilitaires sont nécessaires pour le chargement en bloc des données sur la base de données à l’aide de **bcp**.

+ Créer une base de données et les tables sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’instance et l’insérer en bloc des données provenance d’un fichier .csv.

+ Créer plusieurs fonctions SQL et les procédures stockées utilisées dans plusieurs didacticiels.

### <a name="modify-the-script-to-use-a-trusted-windows-identity"></a>Modifiez le script pour utiliser une identité Windows approuvée

Par défaut, le script suppose une connexion utilisateur de base de données SQL Server et le mot de passe. Si vous êtes db_owner sous votre compte d’utilisateur Windows, vous pouvez utiliser votre identité Windows pour créer les objets. Pour ce faire, ouvrez `RunSQL_SQL_Walkthrough.ps1` dans un éditeur de code et ajoutez **`-T`** insertion de commande (ligne 238) à l’utilitaire bcp en bloc :

```text
bcp $db_tb in $csvfilepath -t ',' -S $server -f taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -U $u -P $p -T
```

### <a name="run-the-script-to-create-objects"></a>Exécutez le script pour créer des objets

À l’aide d’une invite de commandes administrateur PowerShell à C:\tempRSQL, exécutez la commande suivante.
  
```ps
.\RunSQL_SQL_Walkthrough.ps1
```
Vous êtes invité à entrer les informations suivantes :

- Instance de serveur où [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] a été installé. Sur une instance par défaut, cela peut être aussi simple que le nom de l’ordinateur.

- Nom de la base de données. Pour ce didacticiel, les scripts supposent `NYCTaxi_Sample`.

- Nom d’utilisateur et mot de passe utilisateur. Entrez une connexion de base de données SQL Server pour ces valeurs. Ou bien, si vous avez modifié le script pour qu’il accepte une identité Windows approuvés, appuyez sur ENTRÉE pour laisser ces valeurs vide. Votre identité Windows est utilisée sur la connexion.

- Nom de fichier qualifié complet pour les exemples de données téléchargées dans la leçon précédente. Par exemple : `C:\tempRSQL\nyctaxi1pct.csv`

Une fois que vous fournissez ces valeurs, le script s’exécute immédiatement. Pendant l’exécution du script, tous les noms d’espace réservé dans le [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts sont mis à jour pour utiliser les entrées que vous fournissez.

## <a name="review-database-objects"></a>Passez en revue les objets de base de données
   
Lorsque l’exécution du script est terminée, vérifiez les objets de base de données existent sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de l’instance [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vous devez voir la base de données, les tables, les fonctions et les procédures stockées.
  
   ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")

> [!NOTE]
> Si les objets de base de données existent déjà, ils ne peuvent pas être recréés.
>   
> Si la table existe déjà, les données sont ajoutées, pas remplacées. Ainsi, pensez à supprimer tout objet avant d’exécuter le script.

### <a name="objects-in-nyctaxisample-database"></a>Objets de base de données NYCTaxi_Sample

Le tableau suivant récapitule les objets créés dans la base de données de démonstration NYC Taxi. Bien que vous exécutez uniquement un script PowerShell (`RunSQL_SQL_Walkthrough.ps1`), ce script appelle les autres scripts SQL pour créer les objets dans votre base de données. Les scripts utilisés pour créer chaque objet sont mentionnées dans la description.

|**Nom de l'objet**|**Type d'objet**|**Description**|
|----------|------------------------|---------------|
|**NYCTaxi_Sample** | base de données |Créé par le script create-db-to-upload-data.sql. Crée une base de données et deux tables :<br /><br />table de dbo.nyctaxi_sample : contient le jeu de données NYC Taxi principal. Un index cluster columnstore est ajouté à la table pour améliorer les performances du stockage et des requêtes. L’exemple de 1 % du jeu de données NYC Taxi est insérée dans cette table.<br /><br />table de dbo.nyc_taxi_models : utilisée pour conserver le modèle d’analytique avancée formé.|
|**fnCalculateDistance** |fonction scalaire | Créé par le script fnCalculateDistance.sql. Calcule la distance directe entre les emplacements de départ et d’arrivée. Cette fonction est utilisée dans [créer des caractéristiques de données](sqldev-create-data-features-using-t-sql.md), [former et enregistrer un modèle](../r/sqldev-train-and-save-a-model-using-t-sql.md) et [Opérationnaliser le modèle R](sqldev-operationalize-the-model.md).|
|**fnEngineerFeatures** |fonction table | Créé par le script fnEngineerFeatures.sql. Crée de nouvelles fonctionnalités de données d’apprentissage du modèle. Cette fonction est utilisée dans [créer des caractéristiques de données](sqldev-create-data-features-using-t-sql.md) et [Opérationnaliser le modèle R](sqldev-operationalize-the-model.md).|
|**PlotHistogram** |procédure stockée | Créé par le script PlotHistogram.sql. Appelle une fonction R pour tracer l’histogramme d’une variable, puis retourne le tracé en tant qu’objet binaire. Cette procédure stockée est utilisée dans [Explorer et visualiser les données](sqldev-explore-and-visualize-the-data.md).|
|**PlotInOutputFiles** |procédure stockée| Créé par le script PlotInOutputFiles.sql. Crée un graphique à l’aide d’une fonction R, puis enregistre la sortie dans un fichier PDF local. Cette procédure stockée est utilisée dans [Explorer et visualiser les données](sqldev-explore-and-visualize-the-data.md).|
|**PersistModel** |procédure stockée | Créé par le script PersistModel.sql. Prend un modèle qui a été sérialisé dans un type de données varbinary et l’écrit dans la table spécifiée. |
|**PredictTip**  |procédure stockée |Créé par le script PredictTip.sql. Appelle le modèle formé pour créer des prédictions à l’aide du modèle. La procédure stockée accepte une requête comme paramètre d’entrée et retourne une colonne de valeurs numériques qui contient les scores pour les lignes d’entrée. Cette procédure stockée est utilisée dans [Opérationnaliser le modèle R](sqldev-operationalize-the-model.md).|
|**PredictTipSingleMode**  |procédure stockée| Créé par le script PredictTipSingleMode.sql. Appelle le modèle formé pour créer des prédictions à l’aide du modèle. Cette procédure stockée accepte une nouvelle observation comme entrée, avec des valeurs de caractéristiques passées comme paramètres inline, et retourne une valeur qui prédit l’issue de la nouvelle observation. Cette procédure stockée est utilisée dans [Opérationnaliser le modèle R](sqldev-operationalize-the-model.md).|
|**TrainTipPredictionModel**  |procédure stockée|Créé par le script TrainTipPredictionModel.sql. Effectue l’apprentissage d’un modèle de régression logistique en appelant un package R. Le modèle prédit la valeur de la colonne tipped et est formé à l’aide d’un échantillon de 70 % des données sélectionné de façon aléatoire. La sortie de la procédure stockée représente le modèle formé, qui est enregistré dans la table nyc_taxi_models. Cette procédure stockée est utilisée dans [former et enregistrer un modèle](../r/sqldev-train-and-save-a-model-using-t-sql.md).|

## <a name="next-steps"></a>Étapes suivantes

Exemples de données NYC Taxi sont désormais disponibles pour une formation pratique.

+ [Découvrez l’analytique en base de données à l’aide de R dans SQL Server](sqldev-in-database-r-for-sql-developers.md)