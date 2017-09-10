---
title: "Étape 2 : importer des données dans SQL Server à l’aide de PowerShell | Microsoft Docs"
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-server-vnext-ctp2
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 62a06d6c442428132f84b3f8e5a665e872a8d361
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="step-2-import-data-to-sql-server-using-powershell"></a>Étape 2 : importer des données dans SQL Server à l’aide de PowerShell

Dans cette étape, vous allez exécuter un des scripts téléchargés pour créer les objets de base de données nécessaires à la procédure pas à pas. Le script crée également la plupart des procédures stockées que vous allez utiliser et charge les données d’exemple sur une table de la base de données que vous avez spécifiée.

## <a name="create-sql-objects-and-data"></a>Créer des données et des objets SQL

Parmi les fichiers téléchargés, vous devriez voir un script PowerShell. Pour préparer l’environnement à la procédure pas à pas, vous allez exécuter ce script.  Le script effectue les actions suivantes :

- Installe les utilitaires de ligne de commande SQL, SQL Native Client si pas déjà installé. Ces utilitaires sont nécessaires pour le chargement en bloc des données sur la base de données à l’aide de **bcp**.

- Crée une base de données et une table sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance et -insertions en bloc des données dans la table.

- Crée plusieurs fonctions SQL et les procédures stockées.

### <a name="run-the-script"></a>Exécutez le script

1. Ouvrez une invite de commandes PowerShell comme administrateur et exécutez la commande suivante :
  
    ```  
    .\RunSQL_SQL_Walkthrough.ps1  
    ```  

    Vous serez invité à entrer les informations suivantes :
    - Le nom ou l’adresse d’un [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instance où les Services avec Python apprentissage automatique a été installé
    - Les nom d’utilisateur et mot de passe d’un compte sur l’instance. Le compte que vous utilisez doit pouvoir créer des bases de données, des tables et des procédures stockées, et charger des données sur les tables. Si vous ne fournissez pas de nom d’utilisateur et mot de passe, votre identité Windows est utilisée pour se connecter à SQL Server.
    - Le chemin et le nom du fichier de données exemple que vous venez de télécharger. Par exemple, `C:\tempRSQL\nyctaxi1pct.csv`

    > [!NOTE]
    > Assurez-vous que votre fichier xmlrw.dll est dans le même dossier que votre bcp.exe. Si ce n’est pas le cas, copiez-le sur.

2.  Dans le cadre de cette étape, tous les scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] ont été modifiés pour remplacer les espaces réservés par le nom de la base de données et le nom d’utilisateur que vous fournissez comme entrées de script.
  
3. Prenez une minute pour passer en revue les procédures stockées et les fonctions créées par le script.
     
    |**Nom de fichier de script SQL**|**Fonction**|
    |------|------|
    |create-db-tb-upload-data.sql|Crée une base de données et deux tables :<br /><br />nyctaxi_sample : contient le dataset sur les taxis de New York (NYC Taxi). Un index cluster columnstore est ajouté à la table pour améliorer les performances du stockage et des requêtes. L’échantillon de 1 % du dataset NYC Taxi sera inséré dans cette table.<br /><br />nyc_taxi_models : permet de rendre persistant le modèle d’analytique avancée formé.|
    |fnCalculateDistance.sql|Crée une fonction scalaire qui calcule la distance directe entre les lieux de prise en charge et de dépose.|
    |fnEngineerFeatures.sql|Crée une fonction table qui crée des caractéristiques de données pour la formation du modèle.|
    |TrainingTestingSplit.sql|Fractionner les données dans la table nyctaxi_sample en deux parties : nyctaxi_sample_training et nyctaxi_sample_testing.|
    |PredictTipSciKitPy.sql|Crée une procédure stockée qui appelle le modèle formé (scikit-en savoir plus) pour créer des prédictions à l’aide du modèle. La procédure stockée accepte une requête comme paramètre d’entrée et retourne une colonne de valeurs numériques qui contient les scores pour les lignes d’entrée.|
    |PredictTipRxPy.sql|Crée une procédure stockée qui appelle le modèle formé (revoscalepy) pour créer des prédictions à l’aide du modèle. La procédure stockée accepte une requête comme paramètre d’entrée et retourne une colonne de valeurs numériques qui contient les scores pour les lignes d’entrée.|
    |PredictTipSingleModeSciKitPy.sql|Crée une procédure stockée qui appelle le modèle formé (scikit-en savoir plus) pour créer des prédictions à l’aide du modèle. Cette procédure stockée accepte une nouvelle observation comme entrée, avec des valeurs de caractéristiques passées comme paramètres inline, et retourne une valeur qui prédit l’issue de la nouvelle observation.|
    |PredictTipSingleModeRxPy.sql|Crée une procédure stockée qui appelle le modèle formé (revoscalepy) pour créer des prédictions à l’aide du modèle. Cette procédure stockée accepte une nouvelle observation comme entrée, avec des valeurs de caractéristiques passées comme paramètres inline, et retourne une valeur qui prédit l’issue de la nouvelle observation.|
  
4. Vous allez créer des procédures stockées supplémentaires dans la dernière partie de cette procédure pas à pas :
    
    |**Nom de fichier de script SQL**|**Fonction**|
    |------|------|
    |SerializePlots.sql|Crée une procédure stockée pour l’exploration des données. Cette procédure stockée crée un graphique à l’aide de Python et puis sérialiser les objets de graphique.|
    |TrainTipPredictionModelSciKitPy.sql|Crée une procédure stockée qui effectue l’apprentissage d’un modèle de régression logistique (scikit-en savoir plus). Le modèle prédit la valeur de la colonne pourboires et est formé à l’aide d’un sélectionné de façon aléatoire de 60 % des données. La sortie de la procédure stockée représente le modèle formé, qui est enregistré dans la table nyc_taxi_models.|
    |TrainTipPredictionModelRxPy.sql|Crée une procédure stockée qui effectue l’apprentissage d’un modèle de régression logistique (revoscalepy). Le modèle prédit la valeur de la colonne pourboires et est formé à l’aide d’un sélectionné de façon aléatoire de 60 % des données. La sortie de la procédure stockée représente le modèle formé, qui est enregistré dans la table nyc_taxi_models.|
  
3. Connectez-vous à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et du compte de connexion que vous avez spécifié, pour vérifier que vous pouvez voir la base de données, les tables, les fonctions et les procédures stockées qui ont été créées.

    ![Parcourir les tables dans SSMS](media/sqldev-python-browsetables1.png "afficher les tables dans SSMS")

    > [!NOTE]
    > Si les objets de base de données existent déjà, ils ne peuvent pas être recréés. Si la table existe déjà, les données sont ajoutées, pas remplacées. Ainsi, pensez à supprimer tout objet avant d’exécuter le script.
    > Suivez les instructions [ici](https://docs.microsoft.com/en-us/sql/advanced-analytics/r/set-up-sql-server-r-services-in-database#bkmk_enableFeature) pour activer les services de script externe.
    


## <a name="next-step"></a>Étape suivante

[Étape 3 : Explorer et visualiser les données](sqldev-py3-explore-and-visualize-the-data.md)

## <a name="previous-step"></a>Étape précédente

[Étape 1 : Télécharger les exemples de données](sqldev-py1-download-the-sample-data.md)

## <a name="see-also"></a>Voir aussi

[Machine Learning Services avec Python](../python/sql-server-python-services.md)



