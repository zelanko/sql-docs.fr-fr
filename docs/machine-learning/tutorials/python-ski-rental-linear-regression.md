---
title: 'Tutoriel Python : Locations de ski'
description: Dans la troisième partie de cette série de didacticiels en quatre parties, vous allez créer un modèle de régression en Python afin de prédire les locations de ski dans SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/02/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8f07c056e903f1036bfba15398f7cf54a1985f2d
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "81116412"
---
# <a name="python-tutorial-predict-ski-rental-with-linear-regression-in-sql-server-machine-learning-services"></a>Tutoriel Python : Prédire la location de ski avec régression linéaire dans SQL Server Machine Learning Services
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

## <a name="prerequisites"></a>Prérequis

* SQL Server Machine Learning Services - Pour savoir comment installer Machine Learning Services, consultez le [Guide d’installation Windows](../install/sql-machine-learning-services-windows-install.md) ou le [Guide d’installation Linux](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fmachine-learning%2Ftoc.json).

* Environnement de développement intégré (IDE) Python : ce didacticiel utilise un notebook Python dans [Azure Data Studio](../../azure-data-studio/what-is.md). Pour en savoir plus, consultez [Comment utiliser les notebooks dans Azure Data Studio](../../azure-data-studio/sql-notebooks.md). 

    Vous pouvez également utiliser votre propre environnement de développement intégré Python, tel qu’un notebook Jupyter ou [Visual Studio Code](https://code.visualstudio.com/docs) avec l’[extension Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) et l’[extension mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql). 

* Outil de requête SQL : ce didacticiel part du principe que vous utilisez [Azure Data Studio](../../azure-data-studio/what-is.md). Vous pouvez aussi utiliser [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md) (SSMS).

* Packages Python supplémentaires : les exemples de cette série de tutoriel utilisent les packages Python suivants, qui peuvent ne pas être installés par défaut :

  * pandas
  * pyodbc
  * sklearn

  Pour installer ces packages :
  1. Dans Azure Data Studio, sélectionnez **Gérer les packages**.
  2. Dans le volet **Gérer les packages**, sélectionnez l’onglet **Ajouter nouveau**.
  3. Pour chacun des packages suivants, entrez le nom du package, cliquez sur **Rechercher**, puis cliquez sur **Installer**.

  Vous pouvez également ouvrir une **invite de commandes**, modifier le chemin d’installation de la version de Python que vous utilisez dans Azure Data Studio (par exemple, `cd %LocalAppData%\Programs\Python\Python37-32`), puis exécuter `pip install` pour chaque package.

## <a name="restore-the-sample-database"></a>Restaurer les exemples de base de données

L’exemple de base de données utilisé dans ce tutoriel a été enregistré dans un fichier de sauvegarde de base de données **.bak** que vous pouvez télécharger et utiliser.

1. Téléchargez le fichier [TutorialDB.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/TutorialDB.bak).

1. Suivez les instructions dans [Restaurer une base de données à partir d’un fichier de sauvegarde](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file) dans Azure Data Studio, en utilisant les informations suivantes :

   * Importer à partir du fichier **TutorialDB.bak** que vous avez téléchargé
   * Nommez la base de données cible « TutorialDB ».

1. Vous pouvez vérifier que la base de données restaurée existe en interrogeant la table **dbo.rental_data** :

   ```sql
   USE TutorialDB;
   SELECT * FROM [dbo].[rental_data];
   ```

Activez les scripts externes en exécutant les commandes SQL suivantes :

  ```sql
  sp_configure 'external scripts enabled', 1;
  RECONFIGURE WITH override;
  ```

## <a name="next-steps"></a>Étapes suivantes

Dans la première partie de cette série de tutoriels, vous avez effectué les étapes suivantes :

* Installer les prérequis
* Importer un exemple de base de données dans SQL Server

Pour préparer les données de la base de données TutorialDB, suivez la deuxième partie de cette série de tutoriels :

> [!div class="nextstepaction"]
> [Tutoriel Python : Préparer les données pour la formation d’un modèle de régression linéaire](python-ski-rental-linear-regression-prepare-data.md)