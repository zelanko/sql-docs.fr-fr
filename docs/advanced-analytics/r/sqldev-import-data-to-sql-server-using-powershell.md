---
title: Environnement de didacticiel de R de préparer la leçon 2 à l’aide de PowerShell (SQL Server Machine Learning) | Documents Microsoft
description: Le didacticiel expliquant comment incorporer R dans SQL Server procédures stockées et fonctions T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 1280d7c82d48c8ed596271cd7a73fa13ec1664c7
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35249742"
---
# <a name="lesson-2-set-up-the-tutorial-environment-using-powershell"></a>Leçon 2 : Configurer l’environnement de didacticiel à l’aide de PowerShell
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article fait partie d’un didacticiel pour les développeurs SQL sur la façon d’utiliser R dans SQL Server.

Dans cette étape, vous allez exécuter un script PowerShell pour créer les objets de base de données requis pour la procédure pas à pas. Le script crée et charge une base de données à l’aide des exemples de données obtenus à l’étape précédente. Il crée également des fonctions et procédures stockées utilisées dans le didacticiel.

## <a name="create-and-load-database-objects"></a>Créer et charger des objets de base de données

Parmi les fichiers téléchargés, vous devez voir un script PowerShell (`RunSQL_SQL_Walkthrough.ps1`) qui prépare l’environnement pour la procédure pas à pas. Les actions effectuées par le script sont les suivantes :

- Installez les utilitaires de ligne de commande SQL, SQL Native Client si pas déjà installé. Ces utilitaires sont nécessaires pour le chargement en bloc des données sur la base de données à l’aide de **bcp**.

- Créer une base de données et les tables sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l’instance et l’insertion en bloc les données provenant d’un fichier .csv.

- Créer plusieurs fonctions SQL et les procédures stockées.

### <a name="modify-the-script-to-use-a-trusted-windows-identity"></a>Modifiez le script pour utiliser une identité Windows approuvée

Par défaut, le script suppose une connexion utilisateur de base de données SQL Server et le mot de passe. Si vous êtes db_owner sous votre compte d’utilisateur Windows, vous pouvez utiliser votre identité Windows pour créer les objets. Pour ce faire, ouvrez `RunSQL_SQL_Walkthrough.ps1` dans un éditeur de code et ajoutez **`-T`** insertion de commande (ligne 238) à l’utilitaire bcp en bloc :

```text
bcp $db_tb in $csvfilepath -t ',' -S $server -f taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -U $u -P $p -T
```

### <a name="run-the-script-to-create-objects"></a>Exécutez le script pour créer des objets

Ouvrez une invite de commandes PowerShell comme administrateur et exécutez la commande suivante :
  
```ps
.\RunSQL_SQL_Walkthrough.ps1
```
Vous êtes invité à entrer les informations suivantes :

- Instance de serveur où [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] a été installé. Sur une instance par défaut, cela peut être aussi simple que le nom de l’ordinateur.

- Nom de la base de données. Pour ce didacticiel, les scripts supposent `TaxiNYC_Sample`.

- Nom d’utilisateur et mot de passe utilisateur. Entrez une connexion de base de données SQL Server pour ces valeurs. Ou bien, si vous avez modifié le script pour accepter une identité Windows approuvée, appuyez sur ENTRÉE pour laisser ces valeurs vide. Votre identité Windows est utilisée sur la connexion.

- Nom de fichier qualifié complet pour les exemples de données téléchargées dans la leçon précédente. Par exemple : `C:\tempRSQL\nyctaxi1pct.csv`

Après avoir fourni ces valeurs, le script s’exécute immédiatement. Pendant l’exécution du script, tous les noms d’espace réservé dans la [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts sont mis à jour pour utiliser les entrées que vous fournissez.

## <a name="review-database-objects"></a>Passez en revue les objets de base de données
   
L’exécution du script terminée, confirmez que les objets de base de données existent sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de l’instance [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vous devez voir la base de données, les tables, les fonctions et les procédures stockées.
  
   ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")

> [!NOTE]
> Si les objets de base de données existent déjà, ils ne peuvent pas être recréés.
>   
> Si la table existe déjà, les données sont ajoutées, pas remplacées. Ainsi, pensez à supprimer tout objet avant d’exécuter le script.

## <a name="objects-used-in-this-tutorial"></a>Objets utilisés dans ce didacticiel

Le tableau suivant récapitule les objets créés dans cette leçon. Bien que vous n’exécuter un script PowerShell (`RunSQL_SQL_Walkthrough.ps1`), ce script appelle les autres scripts SQL pour créer les objets dans votre base de données. Scripts utilisés pour créer chaque objet sont mentionnés dans la description.

|**Nom de l'objet**|**Type d'objet**|**Description**|
|----------|------------------------|---------------|
|**TaxiNYC_Sample** | base de données |Créé par le script data.sql du téléchargement to create db. Crée une base de données et deux tables :<br /><br />table de dbo.nyctaxi_sample : contient le jeu de données NYC Taxi principal. Un index cluster columnstore est ajouté à la table pour améliorer les performances du stockage et des requêtes. L’exemple de 1 % du jeu de données NYC Taxi est insérée dans cette table.<br /><br />table de dbo.nyc_taxi_models : permet de rendre le modèle formé analytique avancée.|
|**fnCalculateDistance** |fonction scalaire | Créé par le script fnCalculateDistance.sql. Calcule la distance directe entre les emplacements collecte et cette chute. Cette fonction est utilisée dans [créent des fonctionnalités de données](../tutorials/sqldev-create-data-features-using-t-sql.md), [Train et enregistrez un modèle](sqldev-train-and-save-a-model-using-t-sql.md) et [Opérationnaliser du modèle R](../tutorials/sqldev-operationalize-the-model.md).|
|**fnEngineerFeatures** |fonction table | Créé par le script fnEngineerFeatures.sql. Crée de nouvelles fonctionnalités de données pour l’apprentissage du modèle. Cette fonction est utilisée dans [créent des fonctionnalités de données](../tutorials/sqldev-create-data-features-using-t-sql.md) et [Opérationnaliser du modèle R](../tutorials/sqldev-operationalize-the-model.md).|
|**PlotHistogram** |procédure stockée | Créé par le script PlotHistogram.sql. Appelle une fonction R pour tracer l’histogramme d’une variable, puis retourne le tracé en tant qu’objet binaire. Cette procédure stockée est utilisée dans [Explorer et visualiser les données](../tutorials/sqldev-explore-and-visualize-the-data.md).|
|**PlotInOutputFiles** |procédure stockée| Créé par le script PlotInOutputFiles.sql. Crée un graphique à l’aide d’une fonction R, puis enregistre la sortie en tant que fichier PDF local. Cette procédure stockée est utilisée dans [Explorer et visualiser les données](../tutorials/sqldev-explore-and-visualize-the-data.md).|
|**PersistModel** |procédure stockée | Créé par le script PersistModel.sql. Prend un modèle qui a été sérialisé dans un type de données varbinary et l’écrit dans la table spécifiée. |
|**PredictTip**  |procédure stockée |Créé par le script PredictTip.sql. Appelle le modèle formé pour créer des prédictions à l’aide du modèle. La procédure stockée accepte une requête comme paramètre d’entrée et retourne une colonne de valeurs numériques qui contient les scores pour les lignes d’entrée. Cette procédure stockée est utilisée dans [Opérationnaliser du modèle R](../tutorials/sqldev-operationalize-the-model.md).|
|**PredictTipSingleMode**  |procédure stockée| Créé par le script PredictTipSingleMode.sql. Appelle le modèle formé pour créer des prédictions à l’aide du modèle. Cette procédure stockée accepte une nouvelle observation comme entrée, avec des valeurs de caractéristiques passées comme paramètres inline, et retourne une valeur qui prédit l’issue de la nouvelle observation. Cette procédure stockée est utilisée dans [Opérationnaliser du modèle R](../tutorials/sqldev-operationalize-the-model.md).|
|**TrainTipPredictionModel**  |procédure stockée|Créé par le script TrainTipPredictionModel.sql. Effectue l’apprentissage d’un modèle de régression logistique en appelant un package R. Le modèle prédit la valeur de la colonne tipped et est formé à l’aide d’un échantillon de 70 % des données sélectionné de façon aléatoire. La sortie de la procédure stockée représente le modèle formé, qui est enregistré dans la table nyc_taxi_models. Cette procédure stockée est utilisée dans [Train et enregistrez un modèle](sqldev-train-and-save-a-model-using-t-sql.md).|

## <a name="next-lesson"></a>Leçon suivante

[Leçon 3 : Explorer et visualiser les données](../tutorials/sqldev-explore-and-visualize-the-data.md)

## <a name="previous-lesson"></a>Leçon précédente

[Leçon 1 : Télécharger les exemples de données](../tutorials/sqldev-download-the-sample-data.md)
