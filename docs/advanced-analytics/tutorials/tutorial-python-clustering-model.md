---
title: 'Tutoriel : Effectuer un clustering dans python'
description: Dans cette série de didacticiels en quatre parties, vous allez effectuer un clustering de clients dans une base de données SQL à l’aide de Python avec SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/30/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: abcd13b5db24f7ffd44a21b4690f14d97645cdd5
ms.sourcegitcommit: 3de1fb410de2515e5a00a5dbf6dd442d888713ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2019
ms.locfileid: "70211923"
---
# <a name="tutorial-perform-clustering-in-python-with-sql-server-machine-learning-services"></a>Tutoriel : Exécuter le clustering dans Python avec SQL Server Machine Learning Services

Dans cette série de didacticiels en quatre parties, vous utiliserez Python pour développer et déployer un modèle de clustering K-signifiant dans [SQL Server machine learning services](../what-is-sql-server-machine-learning.md) pour mettre en cluster les données client.

Dans la première partie de cette série, vous allez configurer les composants requis pour le didacticiel, puis importer un exemple de jeu de données dans une base de données SQL. Plus loin dans cette série, vous utiliserez ces données pour effectuer l’apprentissage et le déploiement d’un modèle de clustering dans Python avec SQL Server Machine Learning Services.

Dans les deux parties et trois de cette série, vous allez développer des scripts Python dans un bloc-notes Azure Data Studio pour analyser et préparer vos données et former un modèle de Machine Learning. Ensuite, dans la quatrième partie, vous exécuterez ces scripts Python à l’intérieur d’une base de données SQL à l’aide de procédures stockées.

Le clustering peut être expliqué en organisant des données dans des groupes où les membres d’un groupe sont similaires d’une manière ou d’une autre. Pour cette série de didacticiels, imaginez que vous êtes une entreprise de vente au détail. Vous utiliserez l’algorithme **K-signifiant** pour effectuer le clustering des clients dans un jeu de données d’achats de produits et de retours. En mettant en cluster les clients, vous pouvez concentrer vos efforts marketing plus efficacement en ciblant des groupes spécifiques.
Le clustering K-signifiant est un algorithme d' *apprentissage non supervisé* qui recherche des modèles dans les données en fonction de similarités.

Dans cet article, vous allez apprendre à:

> [!div class="checklist"]
> * Importer un exemple de base de données dans une instance de SQL Server

Dans la [deuxième partie](tutorial-python-clustering-model-prepare-data.md), vous apprendrez à préparer les données à partir d’une base de données SQL pour effectuer le clustering.

Dans la [troisième partie](tutorial-python-clustering-model-build.md), vous apprendrez à créer et à former un modèle de clustering K-means dans Python.

Dans la [quatrième partie](tutorial-python-clustering-model-deploy.md), vous apprendrez à créer une procédure stockée dans une base de données SQL qui peut effectuer un clustering dans Python en fonction de nouvelles données.

## <a name="prerequisites"></a>Prérequis

* [SQL Server machine learning services](../what-is-sql-server-machine-learning.md) avec l’option de langage Python-suivez les instructions d’installation du [Guide](../install/sql-machine-learning-services-windows-install.md) d’installation de Windows ou du Guide d' [installation de Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-machine-learning?toc=%2fsql%2fadvanced-analytics%2ftoc.json&view=sql-server-linux-ver15).

* Environnement de développement intégré (IDE) python: ce didacticiel utilise un bloc-notes python dans [Azure Data Studio](../../azure-data-studio/what-is.md). Pour plus d’informations, consultez [utilisation des blocs-notes dans Azure Data Studio](../../azure-data-studio/sql-notebooks.md). Vous pouvez également utiliser votre propre IDE Python, tel qu’un bloc-notes Jupyter ou [Visual Studio code](https://code.visualstudio.com/docs) avec l' [extension Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) et l' [extension MSSQL](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql).

* package [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) : le package **revoscalepy** est inclus dans SQL Server machine learning services. Pour utiliser le package sur un ordinateur client, consultez [configurer un client de science des données pour le développement python](../python/setup-python-client-tools-sql.md) pour les options d’installation de ce package localement.

  Si vous utilisez un bloc-notes python dans Azure Data Studio, suivez ces étapes supplémentaires pour utiliser **revoscalepy**:

  1. Ouvrir Azure Data Studio
  1. Dans le menu **fichier** , sélectionnez **Préférences** , puis **paramètres** .
  1. Développez **Extensions** et sélectionnez **configuration du bloc-notes** .
  1. Sous **chemin d’accès python**, entrez le chemin d’accès de l’emplacement où vous `C:\path-to-python-for-mls`avez installé les bibliothèques (par exemple,).
  1. Vérifier que l’option **utiliser python existant** est cochée
  1. Redémarrer Azure Data Studio

  Si vous utilisez un autre IDE Python, suivez les étapes similaires pour votre IDE.

* Outil de requête SQL: ce didacticiel part du principe que vous utilisez [Azure Data Studio](../../azure-data-studio/what-is.md). Vous pouvez également utiliser [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md) (SSMS).

* Packages python supplémentaires: les exemples de cette série de didacticiels utilisent des packages python que vous pouvez ou non avez installés. Utilisez les commandes **PIP** suivantes pour installer ces packages si nécessaire.

  ```console
  pip install matplotlib
  pip install scipy
  pip install sklearn
  ```

## <a name="import-the-sample-database"></a>Importer l’exemple de base de données

L’exemple de jeu de données utilisé dans ce didacticiel a été enregistré dans un fichier de sauvegarde de base de données **. bak** que vous pouvez télécharger et utiliser. Ce jeu de données est dérivé du jeu de données [TPCX-BB](http://www.tpc.org/tpcx-bb/default.asp) fourni par le [TPC (Transaction Processing Performance Council)](http://www.tpc.org/default.asp).

1. Téléchargez le fichier [tpcxbb_1gb. bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/tpcxbb_1gb.bak) dans le dossier de sauvegarde SQL Server. Pour l’instance de base de données par défaut, le dossier est:

   `C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\MSSQL\Backup\`

1. Ouvrez Azure Data Studio, connectez-vous à votre instance SQL Server et ouvrez une nouvelle fenêtre de requête.

1. Exécutez les commandes suivantes pour restaurer la base de données.

   ```sql
   USE master;
   GO

   RESTORE DATABASE tpcxbb_1gb
   FROM DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\MSSQL\Backup\tpcxbb_1gb.bak'
   WITH MOVE 'tpcxbb_1gb' TO 'C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\MSSQL\DATA\tpcxbb_1gb.mdf'
      , MOVE 'tpcxbb_1gb_log' TO 'C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\MSSQL\DATA\tpcxbb_1gb.ldf';
   GO
   ```

## <a name="clean-up-resources"></a>Supprimer des ressources

Si vous n’allez pas poursuivre ce didacticiel, supprimez la base de données tpcxbb_1gb de SQL Server.

## <a name="next-steps"></a>Étapes suivantes

Dans la première partie de cette série de didacticiels, vous avez effectué les étapes suivantes:

* Importer un exemple de base de données dans une instance de SQL Server

Pour préparer les données pour le modèle de Machine Learning, suivez la deuxième partie de cette série de didacticiels:

> [!div class="nextstepaction"]
> [Tutoriel : Préparer les données pour effectuer le clustering dans Python avec SQL Server Machine Learning Services](tutorial-python-clustering-model-prepare-data.md)
