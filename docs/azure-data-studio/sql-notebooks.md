---
title: Comment utiliser les notebooks SQL dans Azure Data Studio
titleSuffix: Azure Data Studio
description: Découvrez comment utiliser les notebooks SQL dans Azure Data Studio
ms.custom: seodec18
ms.date: 06/28/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: achatter; alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 9af2e04a3973eddfcd714c7968c35e544302aba9
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959263"
---
# <a name="how-to-use-notebooks-in-azure-data-studio"></a>Comment utiliser les notebooks dans Azure Data Studio

Cet article explique comment lancer l’expérience de notebook dans Azure Data Studio et comment commencer à créer vos propres notebooks. Il montre également comment écrire des notebooks à l’aide de différents noyaux.


## <a name="connect-to-sql-server"></a>Se connecter à SQL Server

Vous pouvez vous connecter au type de connexion Microsoft SQL Server dans Azure Data Studio.
Dans Azure Data Studio, vous pouvez également appuyer sur F1, puis cliquer sur **Nouvelle connexion**  et vous connecter à votre SQL Server.

![image1](media/sql-notebooks/connection-info.png)

## <a name="launch-notebooks"></a>Lancer des notebooks

Il existe plusieurs façons de lancer un nouveau notebook.

1. Accédez au **menu Fichier** dans Azure Data Studio, puis cliquez sur **Nouveau notebook**.

    ![image3](media/sql-notebooks/file-new-notebook.png)

3. Cliquez avec le bouton droit sur la connexion **SQL Server**, puis lancez **Nouveau notebook**. 
    ![image3](media/sql-notebooks/server-new-notebook.png)

4. Ouvrez la palette de commandes (**Ctrl+Maj+P**), puis saisissez **Nouveau notebook**. Un nouveau fichier nommé `Notebook-1.ipynb` s’ouvre.

## <a name="supported-kernels-and-attach-to-context"></a>Noyaux pris en charge et attachement au contexte

L’installation du notebook dans Azure Data Studio prend en charge un noyau SQL nativement. Si vous êtes un développeur SQL et souhaitez utiliser des notebooks, il s’agit du noyau que vous avez choisi. 

Le noyau SQL peut également être utilisé pour se connecter à des instances de serveur PostgreSQL. Si vous êtes un développeur PostgreSQL et que vous souhaitez vous connecter à votre serveur PostgreSQL, téléchargez [**l’extension PostgreSQL**](postgres-extension.md) sur le marketplace d’extensions Azure Data Studio.

![image7](media/sql-notebooks/sql-kernel-dropdown.png)

### <a name="sql-kernel"></a>Noyau SQL

Dans les cellules de code du notebook, comme dans notre éditeur de requête, nous prenons en charge l’expérience de codage SQL moderne qui facilite vos tâches quotidiennes grâce à des fonctionnalités intégrées, telles qu’un éditeur SQL riche, IntelliSense et des extraits de code intégrés. Les extraits de code vous permettent de générer la syntaxe SQL appropriée pour créer des bases de données, des tables, des vues, des procédures stockées, etc., ainsi que pour mettre à jour des objets de base de données existants. Utilisez les extraits de code pour créer rapidement des copies de votre base de données à des fins de développement ou de test, et pour générer et exécuter des scripts.

Cliquez sur **Exécuter** pour exécuter chaque cellule.

Noyau SQL pour la connexion à l'instance SQL Server

![image7](media/sql-notebooks/intellisense-code-cell.png)

Résultats de requête

![image19](media/sql-notebooks/sql-cell-results.png)

Noyau SQL pour se connecter à l’instance PostgreSQL Server 

![image18](media/sql-notebooks/pgsql-code-cell.png)

Résultats de requête

![image20](media/sql-notebooks/pgsql-cell-results.png)

### <a name="configure-python-for-notebooks"></a>Configurer Python pour les notebooks

Lorsque vous sélectionnez un noyau hors SQL dans la liste déroulante de noyaux, vous êtes invité à **Configurer Python pour les notebooks**. Les dépendances du notebook sont installées à un emplacement spécifié, mais vous pouvez décider de définir ou non l’emplacement d’installation. Cette installation peut prendre un certain temps et il est recommandé de ne pas fermer l’application tant que l’installation n’est pas terminée. Une fois l’installation terminée, vous pouvez commencer à écrire du code dans la langue prise en charge.

![image21](media/sql-notebooks/configure-python.png)

Une fois l’installation réussie, vous trouverez une notification dans l’historique des tâches, ainsi que l’emplacement du serveur principal Jupyter en cours d’exécution dans le terminal de sortie.

![image22](media/sql-notebooks/jupyter-backend.png)

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

![image8](media/sql-notebooks/notebook-toolbar.png)

La cellule passe en mode édition. Saisissez du Markdown et vous verrez l’aperçu en même temps

![image9](media/sql-notebooks/notebook-markdown-cell.png)

Si vous cliquez en dehors de la cellule de texte, le texte Markdown apparaît.

![image10](media/sql-notebooks/notebook-markdown-preview.png)

### <a name="trusted-and-non-trusted"></a>Approuvé et non approuvé

Les notebooks ouverts dans Azure Data Studio sont **approuvés** par défaut.

Si vous ouvrez un notebook à partir d’une autre source, il est ouvert en mode **non approuvé**. Vous pouvez ensuite le rendre **approuvé**.

### <a name="save"></a>Enregistrer 

Vous pouvez enregistrer le notebook en appuyant sur **Ctrl + S** ou en cliquant sur les commandes **Enregistrer le fichier**, **Enregistrer sous...** et **Enregistrer tous les fichiers** à partir du menu Fichier et **Fichier : Enregistrer** dans la palette de commandes.

### <a name="pyspark3pyspark-kernel"></a>Noyau Pyspark3/PySpark

Choisissez `PySpark Kernel` et précisez le type de cellule dans le code suivant.

Cliquez sur **Exécuter**.

L’application Spark est démarrée et renvoie la sortie suivante :

![image12](media/sql-notebooks/pyspark.png)

### <a name="spark-kernel--scala-language"></a>Noyau Spark | Langage Scala

Choisissez `Spark|Scala Kernel` et précisez le type de cellule dans le code suivant.

![image13](media/sql-notebooks/spark-scala.png)

Vous pouvez également afficher les « Options de cellule » lorsque vous cliquez sur l’icône Options ci-dessous –

![image14](media/sql-notebooks/scala-cell-options.png)

### <a name="spark-kernel--r-language"></a>Noyau Spark | Langage R

Choisissez Spark | R dans la liste déroulante de noyaux. Dans la cellule, saisissez ou collez le code. Cliquez sur **Exécuter** pour voir la sortie suivante.

![image15](media/sql-notebooks/spark-r.png)

### <a name="local-python-kernel"></a>Noyau Python local

Choisissez le noyau Python local et précisez le type de cellule -

![image16](media/sql-notebooks/local-python.png)

## <a name="manage-packages"></a>Gérer les packages
L’une des choses que nous avons optimisées pour le développement Python est l’inclusion de la possibilité d’installer les packages dont les clients ont besoin pour leurs scénarios. Par défaut, nous incluons les packages courants, tels que `pandas`, `numpy`, etc., mais si vous attendez un package qui n’est pas inclus, écrivez le code suivant dans la cellule du notebook : 

```python
import <package-name>
```

Lorsque vous exécutez cette commande, `Module not found` est retourné. Si votre package existe, vous n’obtiendrez pas l’erreur.

S’il retourne une erreur `Module not Found`, cliquez sur **Gérer les packages** pour lancer l’assistant. 

![image17](media/sql-notebooks/manage-packages.png)

Dans cet assistant, vous pourrez voir les packages **Installés**. Vous pouvez effectuer une recherche dans la liste et utiliser la version associée de chacun de ces packages. Si vous avez besoin de **désinstaller** un de ces packages, vous pouvez cliquer sur l’un des packages, puis sur l’option **Désinstaller les packages sélectionnés**.

Vous pouvez également cliquer sur **Ajouter** de nouveaux packages à **Rechercher** pour un package particulier. Choisissez la version associée et cliquer sur **Installer**. Par défaut, nous sélectionnons la version la plus récente du package recherché. 

Une fois le package installé, vous devez pouvoir accéder à la cellule du notebook et saisir la commande suivante :

```python
import <package-name>
```

Si vous avez besoin de **désinstaller** un de ces packages, vous pouvez cliquer sur un ou plusieurs des packages, puis sur l’option **Désinstaller les packages sélectionnés**.

## <a name="next-steps"></a>Étapes suivantes

Pour savoir comment utiliser un notebook existant, consultez [Comment gérer des notebooks dans Azure Data Studio](https://docs.microsoft.com/sql/big-data-cluster/notebooks-how-to-manage?view=sqlallproducts-allversions).