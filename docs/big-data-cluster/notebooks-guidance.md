---
title: 'Exécuter des notebooks : Azure Data Studio'
titleSuffix: SQL Server Big Data Clusters
description: Cet article explique comment exécuter des Jupyter Notebooks dans Azure Data Studio avec une connexion à un cluster Big Data SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ff3f569761b7ba95a64f693f1726df589ce7e579
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75244101"
---
# <a name="how-to-use-notebooks-in-sql-server"></a>Guide pratique pour utiliser des notebooks dans SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment lancer l’expérience de notebook dans la dernière version [**d’Azure Data Studio**](../azure-data-studio/download.md) et comment commencer à créer vos propres notebooks. Il montre également comment écrire des notebooks à l’aide de différents noyaux.

Regardez cette vidéo de 5 minutes pour une présentation des notebooks dans Azure Data Studio :

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introduction-to-Azure-Data-Studio-Notebooks/player?WT.mc_id=dataexposed-c9-niner]


## <a name="connect-to-sql-server"></a>Se connecter à SQL Server

Vous pouvez vous connecter au type de connexion Microsoft SQL Server dans Azure Data Studio.
Dans Azure Data Studio, vous pouvez également appuyer sur F1, puis cliquer sur **Nouvelle connexion**  et vous connecter à votre SQL Server.

![Informations de connexion](media/notebooks-guidance/connection-info.png)

## <a name="launch-notebooks"></a>Lancer des notebooks

Il existe plusieurs façons de lancer un nouveau notebook.

- Accédez au **menu Fichier** dans Azure Data Studio, puis cliquez sur **Nouveau notebook**.

    ![Nouveau notebook](media/notebooks-guidance/file-new-notebook.png)

- Cliquez avec le bouton droit sur la connexion **SQL Server**, puis lancez **Nouveau notebook**.

    ![Nouveau notebook](media/notebooks-guidance/server-new-notebook.png)

- Ouvrez la palette de commandes (**Ctrl+Maj+P**), puis saisissez **Nouveau notebook**. Un nouveau fichier nommé `Notebook-1.ipynb` s’ouvre.

## <a name="supported-kernels-and-attach-to-context"></a>Noyaux pris en charge et attachement au contexte

L’installation du notebook dans Azure Data Studio prend en charge un noyau SQL nativement. Si vous êtes un développeur SQL et souhaitez utiliser des notebooks, il s’agit du noyau que vous avez choisi. 

Le noyau SQL peut également être utilisé pour se connecter à des instances de serveur PostgreSQL. Si vous êtes un développeur PostgreSQL et que vous souhaitez connecter les notebooks à votre serveur PostgreSQL, téléchargez [**l’extension PostgreSQL**](../azure-data-studio/postgres-extension.md) sur le marketplace d’extensions Azure Data Studio, puis lancez **Nouveau notebook** pour ouvrir une instance de notebook et vous connecter au serveur PostgreSQL.

![Connexion PostgreSQL](media/notebooks-guidance/sql-kernel-dropdown.png)

### <a name="sql-kernel"></a>Noyau SQL

Dans les cellules de code du notebook, comme dans notre éditeur de requête, nous prenons en charge l’expérience de codage SQL moderne qui facilite vos tâches quotidiennes grâce à des fonctionnalités intégrées, telles qu’un éditeur SQL riche, IntelliSense et des extraits de code intégrés. Les extraits de code vous permettent de générer la syntaxe SQL appropriée pour créer des bases de données, des tables, des vues, des procédures stockées, etc., ainsi que pour mettre à jour des objets de base de données existants. Utilisez les extraits de code pour créer rapidement des copies de votre base de données à des fins de développement ou de test, et pour générer et exécuter des scripts.

Cliquez sur **Exécuter** pour exécuter chaque cellule.

Noyau SQL pour la connexion à l'instance SQL Server

![Noyau SQL](media/notebooks-guidance/intellisense-code-cell.png)

Résultats de requête

![Résultats de la requête](media/notebooks-guidance/sql-cell-results.png)

Noyau SQL pour se connecter à l’instance PostgreSQL Server 

![Connexion PostgreSQL](media/notebooks-guidance/pgsql-code-cell.png)

Résultats de requête

![Résultats de la requête](media/notebooks-guidance/pgsql-cell-results.png)

Si vous souhaitez ajouter des cellules de texte à votre notebook existant attaché au noyau SQL, cliquez sur la commande **+ Texte** dans la barre d’outils.

![Barre d’outils du notebook](media/notebooks-guidance/notebook-toolbar.png)

La cellule passe en mode édition. Saisissez du Markdown et vous verrez l’aperçu en même temps

![Cellule Markdown](media/notebooks-guidance/notebook-markdown-cell.png)

Si vous cliquez en dehors de la cellule de texte, le texte Markdown apparaît.

![Texte Markdown](media/notebooks-guidance/notebook-markdown-preview.png)


### <a name="configure-python-for-notebooks"></a>Configurer Python pour les notebooks

Lorsque vous sélectionnez un noyau hors SQL dans la liste déroulante de noyaux, vous êtes invité à **Configurer Python pour les notebooks**. Les dépendances du notebook sont installées à un emplacement spécifié, mais vous pouvez décider de définir ou non l’emplacement d’installation. Cette installation peut prendre un certain temps et il est recommandé de ne pas fermer l’application tant que l’installation n’est pas terminée. Une fois l’installation terminée, vous pouvez commencer à écrire du code dans la langue prise en charge.

![Configurer Python](media/notebooks-guidance/configure-python.png)

Une fois l’installation réussie, vous trouverez une notification dans l’historique des tâches, ainsi que l’emplacement du serveur principal Jupyter en cours d’exécution dans le terminal de sortie.

![Backend Jupyter](media/notebooks-guidance/jupyter-backend.png)

|Noyau|Description
|:-----|:-----
| Noyau SQL | Écrivez du code SQL ciblé sur votre base de données relationnelle.
|Noyau PySpark3 et PySpark| Écrivez du code Python à l’aide du calcul Spark à partir du cluster.
|Noyau Spark|Écrivez du code Scala et R à l’aide du calcul Spark à partir du cluster.
|Noyau Python|Écrivez du code Python pour le développement local.

`Attach to` fournit le contexte pour le noyau à attacher. Si vous utilisez le noyau SQL, vous pouvez `Attach to` une de vos instances de SQL Server.

Si vous utilisez le noyau Python3, `Attach to` est `localhost`. Vous pouvez utiliser ce noyau pour votre développement Python local.

Lorsque vous êtes connecté à un cluster Big Data SQL Server 2019, la valeur par défaut `Attach to` est ce point de terminaison du cluster et vous permet d’envoyer du code Python, Scala et R à l’aide du calcul Spark du cluster.

### <a name="code-cells-and-markdown-cells"></a>Cellules de code et cellules Markdown

Ajoutez une nouvelle cellule de code en cliquant sur la commande **+ Code** dans la barre d’outils.

Ajoutez une nouvelle cellule de texte en cliquant sur la commande **+ Texte** dans la barre d’outils.

![Barre d’outils du notebook](media/notebooks-guidance/notebook-toolbar.png)

La cellule passe en mode édition. Saisissez du Markdown et vous verrez l’aperçu en même temps

![Cellule Markdown](media/notebooks-guidance/notebook-markdown-cell.png)

Si vous cliquez en dehors de la cellule de texte, le texte Markdown apparaît.

![Texte Markdown](media/notebooks-guidance/notebook-markdown-preview.png)

### <a name="trusted-and-non-trusted"></a>Approuvé et non approuvé

Les notebooks ouverts dans Azure Data Studio sont **approuvés** par défaut.

Si vous ouvrez un notebook à partir d’une autre source, il est ouvert en mode **non approuvé**. Vous pouvez ensuite le rendre **approuvé**.

### <a name="run-cells"></a>Exécuter des cellules
Si vous souhaitez exécuter toutes les cellules du notebook, cliquez sur le bouton **Exécuter les cellules** dans la barre d’outils.

![Texte Markdown](media/notebooks-guidance/run-cell.png)


### <a name="clear-results"></a>Effacer les résultats

Si vous souhaitez effacer les résultats de toutes les cellules exécutées dans le notebook, vous pouvez cliquer sur le bouton **Effacer les résultats** dans la barre d’outils.

![Texte Markdown](media/notebooks-guidance/clear-results.png)

### <a name="save"></a>Enregistrer

Pour enregistrer le notebook, effectuez une des opérations suivantes.

- Sélectionner Ctrl+S
- Cliquez sur **Fichier** > **Enregistrer**
- Cliquez sur **Fichier** > **Enregistrer sous**
- Click **Fichier** > **Enregistrer tout** 
- Dans la palette de commandes, entrez **Fichier : Enregistrer** 

### <a name="pyspark3pyspark-kernel"></a>Noyau Pyspark3/PySpark

Choisissez `PySpark Kernel` et précisez le type de cellule dans le code suivant.

Cliquez sur **Exécuter**.

L’application Spark est démarrée et renvoie la sortie suivante :

![Application Spark](media/notebooks-guidance/pyspark.png)

### <a name="spark-kernel--scala-language"></a>Noyau Spark | Langage Scala

Choisissez `Spark|Scala Kernel` et précisez le type de cellule dans le code suivant.

![Spark Scala](media/notebooks-guidance/spark-scala.png)

Vous pouvez également afficher les « Options de cellule » lorsque vous cliquez sur l’icône Options ci-dessous –

![Options des cellules](media/notebooks-guidance/scala-cell-options.png)

### <a name="spark-kernel--r-language"></a>Noyau Spark | Langage R

Choisissez Spark | R dans la liste déroulante de noyaux. Dans la cellule, saisissez ou collez le code. Cliquez sur **Exécuter** pour voir la sortie suivante.

![Spark R](media/notebooks-guidance/spark-r.png)

### <a name="local-python-kernel"></a>Noyau Python local

Choisissez le noyau Python local et précisez le type de cellule -

![Python local](media/notebooks-guidance/local-python.png)

## <a name="manage-packages"></a>Gérer les packages

L’une des choses que nous avons optimisées pour le développement Python est l’inclusion de la possibilité d’installer les packages dont les clients ont besoin pour leurs scénarios. Par défaut, nous incluons les packages courants, tels que `pandas`, `numpy`, etc., mais si vous attendez un package qui n’est pas inclus, écrivez le code suivant dans la cellule du notebook : 

```python
import <package-name>
```

Lorsque vous exécutez cette commande, `Module not found` est retourné. Si votre package existe, vous n’obtiendrez pas l’erreur.

S’il retourne une erreur `Module not Found`, cliquez sur **Gérer les packages** pour lancer le terminal. Vous pouvez maintenant installer des packages localement. Utilisez les commandes suivantes pour installer les packages :

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

Pour savoir comment utiliser un notebook existant, consultez [Comment gérer des notebooks dans Azure Data Studio](notebooks-how-to-manage.md).