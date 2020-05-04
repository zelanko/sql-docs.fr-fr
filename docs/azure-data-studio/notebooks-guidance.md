---
title: Utiliser des notebooks Jupyter dans Azure Data Studio avec SQL Server
description: Découvrez comment bien démarrer avec des notebooks dans Azure Data Studio.
author: yualan
ms.author: alayu
ms.reviewer: achatter, maghan, mikeray
ms.topic: conceptual
ms.prod: sql
ms.technology: azure-data-studio
ms.custom: seo-lt-2019
ms.date: 03/30/2020
ms.openlocfilehash: 480b5df927adddd38b8f9f2ea13fa25c3f653606
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82178620"
---
# <a name="notebooks-with-sql-server-in-azure-data-studio"></a>Notebooks avec SQL Server dans Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Jupyter Notebook est une application web open source qui vous permet de créer et de partager des documents contenant du code en temps réel, des équations, des visualisations et du texte narratif. L’utilisation inclut le nettoyage des données et la transformation, la simulation numérique, la modélisation statistique, la visualisation des données et le machine learning.

Cet article explique comment lancer l’expérience de notebook dans la dernière version [**d’Azure Data Studio**](../azure-data-studio/download.md) et comment commencer à créer vos propres notebooks. Il montre également comment écrire des notebooks à l’aide de différents noyaux.

Regardez cette vidéo de 5 minutes pour une présentation des notebooks dans Azure Data Studio :

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introduction-to-Azure-Data-Studio-Notebooks/player?WT.mc_id=dataexposed-c9-niner]

## <a name="connect-to-sql-server"></a>Se connecter à SQL Server

Vous pouvez vous connecter au type de connexion Microsoft SQL Server dans Azure Data Studio.
Dans Azure Data Studio, vous pouvez également appuyer sur F1, puis sélectionner **Nouvelle connexion** et vous connecter à votre serveur SQL Server.

![Informations de connexion](media/notebooks-guidance/connection-info.png)

## <a name="launch-notebooks"></a>Lancer des notebooks

Il existe plusieurs façons de lancer un nouveau notebook.

- Accédez au **menu Fichier** dans Azure Data Studio, puis sélectionnez **Nouveau notebook**.

    ![Nouveau notebook](media/notebooks-guidance/file-new-notebook.png)

- Cliquez avec le bouton droit sur la connexion **SQL Server**, puis lancez **Nouveau notebook**.

    ![Nouveau notebook](media/notebooks-guidance/server-new-notebook.png)

- Ouvrez la palette de commandes (**Ctrl+Maj+P**), puis saisissez **Nouveau notebook**. Un nouveau fichier nommé `Notebook-1.ipynb` s’ouvre.

## <a name="supported-kernels-and-attach-to-context"></a>Noyaux pris en charge et attachement au contexte

L’installation du notebook dans Azure Data Studio prend en charge un noyau SQL nativement. Si vous êtes développeur SQL et que voulez utiliser des notebooks, le noyau SQL est votre noyau.

Le noyau SQL peut également être utilisé pour se connecter à des instances de serveur PostgreSQL. Si vous êtes développeur PostgreSQL et que vous souhaitez connecter les notebooks à votre serveur PostgreSQL, téléchargez l’[**extension PostgreSQL**](../azure-data-studio/postgres-extension.md) dans la Place de marché d’extensions Azure Data Studio, puis lancez **Nouveau notebook** pour ouvrir une instance de notebook et vous connecter au serveur PostgreSQL.

![Connexion PostgreSQL](media/notebooks-guidance/sql-kernel-dropdown.png)

### <a name="sql-kernel"></a>Noyau SQL

Dans les cellules de code du notebook, comme dans notre éditeur de requête, nous prenons en charge l’expérience de codage SQL moderne qui facilite vos tâches quotidiennes grâce à des fonctionnalités intégrées, telles qu’un éditeur SQL riche, IntelliSense et des extraits de code intégrés. Les extraits de code vous permettent de générer la syntaxe SQL appropriée pour créer des bases de données, des tables, des vues et des procédures stockées ainsi que pour mettre à jour des objets de base de données existants. Utilisez les extraits de code pour créer rapidement des copies de votre base de données à des fins de développement ou de test, et pour générer et exécuter des scripts.

Sélectionnez **Exécuter** pour exécuter chaque cellule.

Noyau SQL pour la connexion à l'instance SQL Server

![Noyau SQL](media/notebooks-guidance/intellisense-code-cell.png)

Résultats de requête

![Résultats de la requête](media/notebooks-guidance/sql-cell-results.png)

Noyau SQL pour se connecter à l’instance PostgreSQL Server

![Connexion PostgreSQL](media/notebooks-guidance/pgsql-code-cell.png)

Résultats de requête

![Résultats de la requête](media/notebooks-guidance/pgsql-cell-results.png)

Si vous souhaitez ajouter des cellules de texte à votre notebook existant attaché au noyau SQL, sélectionnez la commande **+ Texte** dans la barre d’outils.

![Barre d’outils du notebook](media/notebooks-guidance/notebook-toolbar.png)

La cellule passe en mode édition. Entrez maintenant du code Markdown : vous voyez l’aperçu en même temps.

![Cellule Markdown](media/notebooks-guidance/notebook-markdown-cell.png)

Si vous sélectionnez un élément en dehors de la cellule de texte, le texte Markdown apparaît.

![Texte Markdown](media/notebooks-guidance/notebook-markdown-preview.png)

### <a name="configure-python-for-notebooks"></a>Configurer Python pour les notebooks

Quand vous sélectionnez un noyau hors SQL dans la liste déroulante de noyaux, vous êtes invité à **Configurer Python pour Notebooks**. Les dépendances du notebook sont installées à un emplacement spécifié, mais vous pouvez décider de définir ou non l’emplacement d’installation. Cette installation peut prendre un certain temps et il est recommandé de ne pas fermer l’application tant que l’installation n’est pas terminée. Une fois l’installation terminée, vous pouvez commencer à écrire du code dans la langue prise en charge.

![Configurer Python](media/notebooks-guidance/configure-python.png)

Une fois l’installation réussie, vous voyez une notification dans l’historique des tâches, ainsi que l’emplacement du serveur back-end Jupyter en cours d’exécution dans le terminal de sortie.

![Backend Jupyter](media/notebooks-guidance/jupyter-backend.png)

|Noyau|Description
|:-----|:-----
| Noyau SQL | Écrivez du code SQL ciblé sur votre base de données relationnelle.
|Noyau PySpark3 et PySpark| Écrivez du code Python à l’aide du calcul Spark à partir du cluster.
|Noyau Spark|Écrivez du code Scala et R à l’aide du calcul Spark à partir du cluster.
|Noyau Python|Écrivez du code Python pour le développement local.

`Attach to` fournit le contexte pour le noyau à attacher. Si vous utilisez le noyau SQL, vous pouvez effectuer l’action `Attach to` à une de vos instances SQL Server.

Si vous utilisez le noyau Python3, `Attach to` est `localhost`. Vous pouvez utiliser ce noyau pour votre développement Python local.

Quand vous êtes connecté à un cluster Big Data SQL Server 2019, la valeur par défaut de `Attach to` est ce point de terminaison du cluster et vous permet d’envoyer du code Python, Scala et R avec le calcul Spark du cluster.

### <a name="code-cells-and-markdown-cells"></a>Cellules de code et cellules Markdown

Ajoutez une nouvelle cellule de code en sélectionnant la commande **+ Code** dans la barre d’outils.

Ajoutez une nouvelle cellule de texte en sélectionnant la commande **+ Texte** dans la barre d’outils.

![Barre d’outils du notebook](media/notebooks-guidance/notebook-toolbar.png)

La cellule passe en mode édition. Entrez maintenant du code Markdown : vous voyez l’aperçu en même temps.

![Cellule Markdown](media/notebooks-guidance/notebook-markdown-cell.png)

Si vous sélectionnez un élément en dehors de la cellule de texte, le texte Markdown apparaît.

![Texte Markdown](media/notebooks-guidance/notebook-markdown-preview.png)

### <a name="trusted-and-non-trusted"></a>Approuvé et non approuvé

Les notebooks ouverts dans Azure Data Studio sont **approuvés** par défaut.

Si vous ouvrez un notebook à partir d’une autre source, il est ouvert en mode **non approuvé**. Vous pouvez ensuite le rendre **approuvé**.

### <a name="run-cells"></a>Exécuter des cellules

Si vous souhaitez exécuter toutes les cellules du notebook, sélectionnez le bouton **Exécuter les cellules** dans la barre d’outils.

### <a name="clear-results"></a>Effacer les résultats

Si vous souhaitez effacer les résultats de toutes les cellules exécutées dans le notebook, vous pouvez sélectionner le bouton **Effacer les résultats** dans la barre d’outils.

### <a name="save"></a>Enregistrer

Pour enregistrer le notebook, effectuez l’une des opérations suivantes.

- Sélectionner Ctrl+S
- Sélectionner **Fichier** > **Enregistrer**
- Sélectionner **Fichier** > **Enregistrer sous...**
- Sélectionner **Fichier** > **Enregistrer tout**
- Dans la palette de commandes, entrez **Fichier : Enregistrer**

### <a name="pyspark3pyspark-kernel"></a>Noyau Pyspark3/PySpark

Choisissez `PySpark Kernel` et précisez le type de cellule dans le code suivant.

Sélectionnez **Exécuter**.

L’application Spark est démarrée et renvoie la sortie suivante :

![Application Spark](media/notebooks-guidance/pyspark.png)

### <a name="spark-kernel--scala-language"></a>Noyau Spark | Langage Scala

Choisissez `Spark|Scala Kernel` et précisez le type de cellule dans le code suivant.

![Spark Scala](media/notebooks-guidance/spark-scala.png)

Vous pouvez également afficher les « Options de cellule » quand vous sélectionnez l’icône des options ci-dessous :

![Options des cellules](media/notebooks-guidance/scala-cell-options.png)

### <a name="spark-kernel--r-language"></a>Noyau Spark | Langage R

Choisissez Spark | R dans la liste déroulante de noyaux. Dans la cellule, saisissez ou collez le code. Sélectionnez **Exécuter** pour voir la sortie suivante.

![Spark R](media/notebooks-guidance/spark-r.png)

### <a name="local-python-kernel"></a>Noyau Python local

Choisissez le noyau Python local et précisez le type de cellule -

![Python local](media/notebooks-guidance/local-python.png)

## <a name="manage-packages"></a>Gérer les packages

L’une des choses que nous avons optimisées pour le développement Python est l’inclusion de la possibilité d’installer les packages dont les clients ont besoin pour leurs scénarios. Par défaut, nous incluons les packages courants, comme `pandas`, `numpy`, etc., mais si vous attendez un package qui n’est pas inclus, écrivez le code suivant dans la cellule du notebook :

```python
import <package-name>
```

Lorsque vous exécutez cette commande, `Module not found` est retourné. Si votre package existe, il n’y a aucune erreur.

S’il retourne une erreur `Module not Found`, sélectionnez alors **Gérer les packages** pour lancer le terminal. Vous pouvez maintenant installer des packages localement. Utilisez les commandes suivantes pour installer les packages :

```bash
./pip install <package-name>
```

   > [!Tip]
   > Sur Mac, suivez les instructions de la fenêtre de terminal pour l’installation des packages.

Une fois le package installé, vous devez pouvoir accéder à la cellule du notebook et saisir la commande suivante :

```python
import <package-name>
```

Pour désinstaller un package, utilisez la commande suivante à partir de votre terminal :

```bash
./pip uninstall <package-name>
```

## <a name="next-steps"></a>Étapes suivantes

- [Guide pratique pour gérer des notebooks dans Azure Data Studio](notebooks-manage-sql-server.md).
- [Créer et exécuter un notebook SQL Server](notebooks-tutorial-sql-kernel.md).
- [Déployer un cluster Big Data SQL Server avec un notebook Azure Data Studio](../big-data-cluster/notebooks-deploy.md).
- [Gérer des clusters Big Data SQL Server avec des notebooks Azure Data Studio](../big-data-cluster/notebooks-manage-bdc.md).
- [Exécuter un exemple de notebook avec Spark](../big-data-cluster/notebooks-tutorial-spark.md).
- [Exécuter des scripts Python et R dans des notebooks Azure Data Studio avec SQL Server Machine Learning Services](../machine-learning/install/sql-machine-learning-azure-data-studio.md).
