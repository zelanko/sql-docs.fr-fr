---
title: 'Tutoriel Python : Locations de ski'
description: Dans ce didacticiel, vous allez utiliser Python et la régression linéaire dans SQL Server Machine Learning Services pour prédire le nombre de locations de ski.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/03/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 927816988be8882d4149115f6d4aee38dd3a8f3f
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727035"
---
# <a name="python-tutorial-predict-ski-rental-with-linear-regression-in-sql-server-machine-learning-services"></a>Tutoriel Python : Prédire la location de ski avec régression linéaire dans SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans ce tutoriel en quatre parties, vous allez utiliser Python et la régression linéaire dans [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) pour prédire le nombre de locations de ski. Ce didacticiel utilise un [notebook Python dans Azure Data Studio](../../azure-data-studio/sql-notebooks.md), mais vous pouvez également utiliser votre propre environnement de développement intégré (IDE) Python.

Imaginez que vous êtes une entreprise de location de ski et que vous souhaitez prédire le nombre de locations à une date ultérieure. Ces informations vous aideront à préparer votre inventaire, votre personnel et vos installations.

Dans la première partie de ce tutoriel, vous allez configurer les composants requis. Dans les parties 2 et 3, vous allez développer des scripts Python dans un notebook Jupyter pour préparer vos données et effectuer la formation d’un modèle Machine Learning. Ensuite, dans la troisième partie, vous exécuterez ces scripts Python à l’intérieur de SQL Server à l’aide de procédures stockées T-SQL.

Dans cet article, vous allez apprendre à :

> [!div class="checklist"]
> * Importer un exemple de base de données dans SQL Server 

Dans la [deuxième partie](python-ski-rental-linear-regression-prepare-data.md), vous apprendrez à charger les données de SQL Server dans une trame de données Python et à préparer les données dans Python.

Dans la [troisième partie](python-ski-rental-linear-regression-train-model.md), vous apprendrez à effectuer la formation d’un modèle de régression linéaire dans Python.

Dans la [quatrième partie](python-ski-rental-linear-regression-deploy-model.md), vous apprendrez à stocker le modèle dans SQL Server, puis à créer des procédures stockées à partir des scripts Python que vous avez développés dans les parties 2 et 3. Les procédures stockées sont exécutées dans SQL Server pour effectuer des prédictions en fonction de nouvelles données.

## <a name="prerequisites"></a>Conditions préalables requises

* SQL Server Machine Learning Services - Pour savoir comment installer Machine Learning Services, consultez le [Guide d’installation Windows](../install/sql-machine-learning-services-windows-install.md) ou le [Guide d’installation Linux](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fadvanced-analytics%2Ftoc.json).

* Environnement de développement intégré (IDE) Python : ce didacticiel utilise un notebook Python dans [Azure Data Studio](../../azure-data-studio/what-is.md). Pour en savoir plus, consultez [Comment utiliser les notebooks dans Azure Data Studio](../../azure-data-studio/sql-notebooks.md). 

    Vous pouvez également utiliser votre propre environnement de développement intégré Python, tel qu’un notebook Jupyter ou [Visual Studio Code](https://code.visualstudio.com/docs) avec l’[extension Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) et l’[extension mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql). 

* Package [revoscalepy](../python/ref-py-revoscalepy.md) : le package de **revoscalepy** est inclus dans SQL Server Machine Learning Services. Pour utiliser le package sur un ordinateur client, consultez [Configurer un client de science des données pour le développement Python](../python/setup-python-client-tools-sql.md) pour connaître les options d’installation de ce package localement.

    Si vous utilisez un notebook Python dans Azure Data Studio, suivez ces étapes supplémentaires pour utiliser **revoscalepy** :

    1. Ouvrir Azure Data Studio
    1. Dans le menu **Fichier** , sélectionnez **Préférences**, puis **Paramètres**.
    1. Développez **Extensions** et sélectionnez **Configuration du notebook**
    1. Sous **Chemin Python**, entrez le chemin vers l’emplacement où vous avez installé les bibliothèques (par exemple, `C:\path-to-python-for-mls`)
    1. Vérifiez que la case **Utiliser Python existant** est cochée
    1. Redémarrez Azure Data Studio.

    Si vous utilisez un environnement de développement intégré Python différent, suivez les étapes similaires pour votre environnement.

* Outil de requête SQL : ce didacticiel part du principe que vous utilisez [Azure Data Studio](../../azure-data-studio/what-is.md). Vous pouvez aussi utiliser [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md) (SSMS).

* Packages Python supplémentaires : les exemples de cette série de tutoriel utilisent des packages Python qui peuvent déjà être installés. Utilisez les commandes **pip** suivantes pour installer ces packages si nécessaire.

    ```console
    pip install pandas
    pip install sklearn
    pip install pickle
    ```

## <a name="restore-the-sample-database"></a>Restaurer les exemples de base de données

L’exemple de jeu de données utilisé dans ce tutoriel a été enregistré dans un fichier de sauvegarde de base de données **.bak** que vous pouvez télécharger et utiliser.

1. Téléchargez le fichier [TutorialDB.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/TutorialDB.bak).

1. Suivez les instructions dans [Restaurer une base de données à partir d'un fichier de sauvegarde](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file) dans Azure Data Studio, en utilisant les informations suivantes :

   * Importer à partir du fichier **TutorialDB.bak** que vous avez téléchargé
   * Nommez la base de données cible « TutorialDB ».

1. Vous pouvez vérifier que le jeu de données existe après la restauration de la base de données en interrogeant la table **dbo.rental_data** :

    ```sql
    USE TutorialDB;
    SELECT * FROM [dbo].[rental_data];
    ```

## <a name="next-steps"></a>Étapes suivantes

Dans la première partie de cette série de tutoriels, vous avez effectué les étapes suivantes :

* Installer les prérequis
* Importer un exemple de base de données dans SQL Server

Pour préparer les données de la base de données TutorialDB, suivez la deuxième partie de cette série de tutoriels :

> [!div class="nextstepaction"]
> [Tutoriel Python : Préparer les données pour la formation d’un modèle de régression linéaire](python-ski-rental-linear-regression-prepare-data.md)