---
title: 'Didacticiel Python : Locations de ski (régression linéaire)'
description: Dans ce didacticiel, vous allez utiliser Python et la régression linéaire dans SQL Server Machine Learning Services pour prédire le nombre de locations de ski.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/03/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 718487ba55b2b8db8f16b59df5785cf78ff501f1
ms.sourcegitcommit: ecb19d0be87c38a283014dbc330adc2f1819a697
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70242507"
---
# <a name="python-tutorial-predict-ski-rental-with-linear-regression-in-sql-server-machine-learning-services"></a>Didacticiel Python : Prédire la location de ski avec régression linéaire dans SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans cette série de didacticiels en quatre parties, vous allez utiliser Python et la régression linéaire dans [SQL Server machine learning services](../what-is-sql-server-machine-learning.md) pour prédire le nombre de locations de ski. Ce didacticiel utilise un [bloc-notes python dans Azure Data Studio](../../azure-data-studio/sql-notebooks.md), mais vous pouvez également utiliser votre propre environnement de développement intégré Python (IDE).

Imaginez que vous êtes une entreprise de location de ski et que vous souhaitez prédire le nombre de loyers que vous aurez à une date ultérieure. Ces informations vous aideront à préparer votre action, votre personnel et vos installations.

Dans la première partie de cette série, vous allez configurer les composants requis. Dans les deux parties et trois, vous allez développer des scripts Python dans un bloc-notes Jupyter pour préparer vos données et effectuer l’apprentissage d’un modèle de Machine Learning. Ensuite, dans la troisième partie, vous exécuterez ces scripts Python à l’intérieur de SQL Server à l’aide de procédures stockées T-SQL.

Dans cet article, vous allez apprendre à :

> [!div class="checklist"]
> * Importer un exemple de base de données dans SQL Server 

Dans la [deuxième partie](python-ski-rental-linear-regression-prepare-data.md), vous apprendrez à charger les données de SQL Server dans une trame de données python et à préparer les données dans Python.

Dans la [troisième partie](python-ski-rental-linear-regression-train-model.md), vous apprendrez à effectuer l’apprentissage d’un modèle de régression linéaire dans Python.

Dans la [quatrième partie](python-ski-rental-linear-regression-deploy-model.md), vous apprendrez à stocker le modèle dans SQL Server, puis à créer des procédures stockées à partir des scripts Python que vous avez développés dans les deux parties et trois. Les procédures stockées sont exécutées dans SQL Server pour effectuer des prédictions en fonction de nouvelles données.

## <a name="prerequisites"></a>Prérequis

* SQL Server Machine Learning Services-pour savoir comment installer Machine Learning Services, consultez le [Guide d’installation de Windows](../install/sql-machine-learning-services-windows-install.md) ou le [Guide d’installation de Linux](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fadvanced-analytics%2Ftoc.json).

* Environnement de développement intégré (IDE) python : ce didacticiel utilise un bloc-notes python dans [Azure Data Studio](../../azure-data-studio/what-is.md). Pour plus d’informations, consultez [utilisation des blocs-notes dans Azure Data Studio](../../azure-data-studio/sql-notebooks.md). 

    Vous pouvez également utiliser votre propre IDE Python, tel qu’un bloc-notes Jupyter ou [Visual Studio code](https://code.visualstudio.com/docs) avec l' [extension Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) et l' [extension MSSQL](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql). 

* package [revoscalepy](../python/ref-py-revoscalepy.md) : le package **revoscalepy** est inclus dans SQL Server machine learning services. Pour utiliser le package sur un ordinateur client, consultez [configurer un client de science des données pour le développement python](../python/setup-python-client-tools-sql.md) pour les options d’installation de ce package localement.

    Si vous utilisez un bloc-notes python dans Azure Data Studio, suivez ces étapes supplémentaires pour utiliser **revoscalepy**:

    1. Ouvrir Azure Data Studio
    1. Dans le menu **fichier** , sélectionnez **Préférences** , puis **paramètres** .
    1. Développez **Extensions** et sélectionnez **configuration du bloc-notes** .
    1. Sous **chemin d’accès python**, entrez le chemin d’accès de l’emplacement où vous `C:\path-to-python-for-mls`avez installé les bibliothèques (par exemple,).
    1. Vérifier que l’option **utiliser python existant** est cochée
    1. Redémarrer Azure Data Studio

    Si vous utilisez un autre IDE Python, suivez les étapes similaires pour votre IDE.

* Outil de requête SQL : ce didacticiel part du principe que vous utilisez [Azure Data Studio](../../azure-data-studio/what-is.md). Vous pouvez également utiliser [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md) (SSMS).

* Packages python supplémentaires : les exemples de cette série de didacticiels utilisent des packages python que vous pouvez ou non avez installés. Utilisez les commandes **PIP** suivantes pour installer ces packages si nécessaire.

    ```console
    pip install pandas
    pip install sklearn
    pip install pickle
    ```

## <a name="restore-the-sample-database"></a>Restaurer l’exemple de base de données

L’exemple de jeu de données utilisé dans ce didacticiel a été enregistré dans un fichier de sauvegarde de base de données **. bak** que vous pouvez télécharger et utiliser.

1. Téléchargez le fichier [TutorialDB. bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/TutorialDB.bak).

1. Suivez les instructions de la [restauration d’une base de données à partir d’un fichier de sauvegarde](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file) dans Azure Data Studio, en utilisant les informations suivantes :

   * Importer à partir du fichier **TutorialDB. bak** que vous avez téléchargé
   * Nommez la base de données cible « TutorialDB ».

1. Vous pouvez vérifier que le jeu de données existe après la restauration de la base de données en interrogeant la table **dbo. rental_data** :

    ```sql
    USE TutorialDB;
    SELECT * FROM [dbo].[rental_data];
    ```

## <a name="next-steps"></a>Étapes suivantes

Dans la première partie de cette série de didacticiels, vous avez effectué les étapes suivantes :

* Installation des composants requis
* Importer un exemple de base de données dans un SQL Server

Pour préparer les données de la base de données TutorialDB, suivez la deuxième partie de cette série de didacticiels :

> [!div class="nextstepaction"]
> [Didacticiel Python : Préparer les données pour l’apprentissage d’un modèle de régression linéaire](python-ski-rental-linear-regression-prepare-data.md)