---
title: 'Tutoriel Python : Categoriser les utilisateurs'
description: Dans la quatrième partie de cette série de tutoriels, vous allez effectuer un clustering de clients à l’aide de K-moyennes dans une base de données SQL en Python avec SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 12/17/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f5d1254c6b5c478c7bcad63da0902f21f4db70a9
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75306582"
---
# <a name="tutorial-categorizing-customers-using-k-means-clustering-with-sql-server-machine-learning-services"></a>Tutoriel : Catégoriser des clients à l’aide de k-moyennes avec SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans ce tutoriel en quatre parties, vous allez utiliser Python pour développer et déployer un modèle de clustering k-moyennes dans [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) pour clusteriser les données clients.

Dans la première partie de cette série, vous allez configurer les conditions préalables pour le tutoriel, puis restaurer un exemple de jeu de données dans une base de données SQL. Plus loin dans cette série, vous utiliserez ces données pour effectuer l’apprentissage et le déploiement d’un modèle de clustering dans Python avec SQL Server Machine Learning Services.

Dans les parties 2 et 3 de cette série, vous allez développer des scripts Python dans un notebook Azure Data Studio pour analyser et préparer vos données et effectuer l’apprentissage d’un modèle Machine Learning. Ensuite, dans la quatrième partie, vous exécuterez ces scripts Python à l’intérieur d’une base de données SQL à l’aide de procédures stockées.

Le *clustering* permet d’organiser les données dans des groupes dont les membres sont similaires. Pour cette série de tutoriels, imaginez que vous êtes une entreprise de vente au détail. Vous allez utiliser l’algorithme **K-moyennes** pour effectuer le clustering des clients dans un jeu de données d’achats et de retours de produits. Lorsque vous effectuez le clustering de clients, vous pouvez concentrer plus efficacement vos efforts marketing en ciblant des groupes spécifiques.
Le clustering K-myennes est un algorithme *d’apprentissage non supervisé* qui recherche des modèles dans les données en fonction de similarités.

Dans cet article, vous allez apprendre à :

> [!div class="checklist"]
> * Restaurer un exemple de base de données dans une instance SQL Server

Dans la [deuxième partie](python-clustering-model-prepare-data.md), vous allez préparer les données d’une base de données SQL pour effectuer le clustering.

Dans la [troisième partie](python-clustering-model-build.md), vous apprendrez à créer et à effectuer l’apprentissage d’un modèle de clustering dans Python.

Dans la [quatrième partie](python-clustering-model-deploy.md), vous allez créer une procédure stockée dans une base de données SQL capable d’effectuer un clustering en Python sur la base des nouvelles données.

## <a name="prerequisites"></a>Prérequis

* [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) avec option de langage Python. Suivez les instructions d’installation du [Guide d’installation de Windows](../install/sql-machine-learning-services-windows-install.md) ou du [Guide d’installation de Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-machine-learning?toc=%2fsql%2fadvanced-analytics%2ftoc.json&view=sql-server-linux-ver15).

* [Azure Data Studio](../../azure-data-studio/what-is.md) Vous allez utiliser un notebook dans Azure Data Studio pour Python et SQL. Pour plus d’informations sur les notebooks, consultez [Guide pratique pour utiliser des notebooks dans Azure Data Studio](../../azure-data-studio/sql-notebooks.md).

  * Python - Vous pouvez également utiliser votre propre environnement de développement intégré Python, tel qu’un notebook Jupyter ou [Visual Studio Code](https://code.visualstudio.com/docs) avec l’[extension Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) et l’[extension mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql).
  * SQL - Vous pouvez aussi utiliser [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md) (SSMS).

* Packages Python supplémentaires : les exemples de cette série de tutoriel utilisent des packages Python qui peuvent déjà être installés.

  Ouvrez une **invite de commandes** et accédez au chemin d’installation de la version de Python que vous utilisez dans Azure Data Studio. Par exemple : `cd %LocalAppData%\Programs\Python\Python37-32`. Exécutez ensuite les commandes suivantes pour installer les packages qui ne sont pas déjà installés.

  ```console
  pip install matplotlib
  pip install pandas
  pip install pyodbc
  pip install scipy
  pip install sklearn
  ```

## <a name="restore-the-sample-database"></a>Restaurer les exemples de base de données

L’exemple de jeu de données utilisé dans ce tutoriel a été enregistré dans un fichier de sauvegarde de base de données **.bak** que vous pouvez télécharger et utiliser. Ce jeu de données est dérivé du jeu de données [TPCX-BB](http://www.tpc.org/tpcx-bb/default.asp) fourni par le [TPC (Transaction Processing Performance Council)](http://www.tpc.org/default.asp).

1. Téléchargez le fichier [tpcxbb_1gb. bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/tpcxbb_1gb.bak).

1. Suivez les instructions dans [Restaurer une base de données à partir d’un fichier de sauvegarde](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file) dans Azure Data Studio, en utilisant les informations suivantes :

   * Importez à partir du fichier **tpcxbb_1gb.bak** que vous avez téléchargé
   * Nommez la base de données cible « tpcxbb_1gb ».

1. Vous pouvez vérifier que le jeu de données existe après la restauration de la base de données en interrogeant la table **dbo.customer** :

    ```sql
    USE tpcxbb_1gb;
    SELECT * FROM [dbo].[customer];
    ```

## <a name="clean-up-resources"></a>Nettoyer les ressources

Si vous ne poursuivez pas ce tutoriel, supprimez la base de données tpcxbb_1gb de SQL Server.

## <a name="next-steps"></a>Étapes suivantes

Dans la première partie de cette série de tutoriels, vous avez effectué les étapes suivantes :

* Restaurer un exemple de base de données dans une instance SQL Server

Pour préparer les données pour le modèle Machine Learning, suivez la deuxième partie de cette série de tutoriels :

> [!div class="nextstepaction"]
> [Tutoriel : Préparer des données pour effectuer le clustering dans Python avec ](python-clustering-model-prepare-data.md)SQL Server Machine Learning Services
