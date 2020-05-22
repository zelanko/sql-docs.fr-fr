---
title: 'Tutoriel Python : Locations de ski'
titleSuffix: SQL machine learning
description: Dans cette série de tutoriels en quatre parties, vous allez générer un modèle de régression linéaire dans Python afin de prédire les locations de skis avec le Machine Learning SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b34687440763f2c514016989542ae3f2d7c0e6ed
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606913"
---
# <a name="python-tutorial-predict-ski-rental-with-linear-regression-with-sql-machine-learning"></a>Tutoriel Python : Prédire la location de skis avec la régression linéaire et le Machine Learning SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Dans cette série de tutoriels en quatre parties, vous allez utiliser Python et la régression linéaire dans [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) ou sur des [clusters Big Data](../../big-data-cluster/machine-learning-services.md) pour prédire le nombre de locations de skis. Le tutoriel utilise un [notebook Python dans Azure Data Studio](../../azure-data-studio/sql-notebooks.md).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Dans ce tutoriel en quatre parties, vous allez utiliser Python et la régression linéaire dans [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) pour prédire le nombre de locations de ski. Le tutoriel utilise un [notebook Python dans Azure Data Studio](../../azure-data-studio/sql-notebooks.md).
::: moniker-end

Imaginez que vous êtes une entreprise de location de ski et que vous souhaitez prédire le nombre de locations à une date ultérieure. Ces informations vous aideront à préparer votre inventaire, votre personnel et vos installations.

Dans la première partie de ce tutoriel, vous allez configurer les composants requis. Dans les parties 2 et 3, vous allez développer des scripts Python dans un notebook pour préparer vos données et effectuer l’apprentissage d’un modèle Machine Learning. Ensuite, dans la troisième partie, vous exécuterez ces scripts Python à l’intérieur de SQL Server à l’aide de procédures stockées T-SQL.

Dans cet article, vous allez apprendre à :

> [!div class="checklist"]
> * Importer un exemple de base de données dans SQL Server 

Dans la [deuxième partie](python-ski-rental-linear-regression-prepare-data.md), vous allez apprendre à charger les données à partir d’une base de données dans une trame de données Python et à préparer les données dans Python.

Dans la [troisième partie](python-ski-rental-linear-regression-train-model.md), vous apprendrez à effectuer la formation d’un modèle de régression linéaire dans Python.

Dans la [quatrième partie](python-ski-rental-linear-regression-deploy-model.md), vous allez apprendre à stocker le modèle dans une base de données, puis à créer des procédures stockées à partir des scripts Python que vous avez développés dans les parties 2 et 3. Les procédures stockées sont exécutées sur le serveur pour effectuer des prédictions en fonction de nouvelles données.

## <a name="prerequisites"></a>Prérequis

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
* SQL Server Machine Learning Services - Pour savoir comment installer Machine Learning Services, consultez le [Guide d’installation Windows](../install/sql-machine-learning-services-windows-install.md) ou le [Guide d’installation Linux](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fmachine-learning%2Ftoc.json). Vous pouvez également [activer Machine Learning Services sur des clusters Big Data SQL Server](../../big-data-cluster/machine-learning-services.md).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
* SQL Server Machine Learning Services - Pour savoir comment installer Machine Learning Services, consultez le [Guide d’installation Windows](../install/sql-machine-learning-services-windows-install.md). 
::: moniker-end

* Environnement de développement intégré (IDE) Python : ce didacticiel utilise un notebook Python dans [Azure Data Studio](../../azure-data-studio/what-is.md). Pour en savoir plus, consultez [Comment utiliser les notebooks dans Azure Data Studio](../../azure-data-studio/sql-notebooks.md).

* Outil de requête SQL : ce didacticiel part du principe que vous utilisez [Azure Data Studio](../../azure-data-studio/what-is.md).

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

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
> [!NOTE]
> Si vous utilisez Machine Learning Services sur des clusters Big Data, consultez [Restaurer une base de données dans l’instance principale du cluster Big Data SQL Server](../../big-data-cluster/data-ingestion-restore-database.md).
::: moniker-end

1. Téléchargez le fichier [TutorialDB.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/TutorialDB.bak).

1. Suivez les instructions dans [Restaurer une base de données à partir d’un fichier de sauvegarde](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file) dans Azure Data Studio, en utilisant les informations suivantes :

   * Importer à partir du fichier **TutorialDB.bak** que vous avez téléchargé
   * Nommez la base de données cible « TutorialDB ».

1. Vous pouvez vérifier que la base de données restaurée existe en interrogeant la table **dbo.rental_data** :

   ```sql
   USE TutorialDB;
   SELECT * FROM [dbo].[rental_data];
   ```

1. Activez les scripts externes en exécutant les commandes SQL suivantes :

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