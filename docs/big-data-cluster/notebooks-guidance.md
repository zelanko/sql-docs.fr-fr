---
title: Exécuter les notebooks dans Azure Data Studio
titleSuffix: SQL Server big data clusters
description: Cet article explique comment exécuter les blocs-notes Jupyter dans Azure Data Studio connecté à un cluster de données volumineux de SQL Server 2019.
author: achatter
ms.author: jroth
manager: jroth
ms.date: 05/08/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: e4b24b70a427e7ac3e3f058b1db332b899729034
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802814"
---
# <a name="how-to-use-notebooks-in-sql-server-2019-preview"></a>Comment utiliser des blocs-notes en version préliminaire de SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit comment lancer l’expérience de bloc-notes dans la dernière version de [ **Azure Data Studio** ](../azure-data-studio/download.md) et comment commencer à créer vos propres blocs-notes. Il montre également comment écrire à l’aide de différents noyaux de blocs-notes.

## <a name="connect-to-sql-server"></a>Se connecter à SQL Server

Vous pouvez vous connecter au type de connexion Microsoft SQL Server dans Azure Data Studio.
Dans Azure Data Studio, vous pouvez également appuyer sur F1, puis cliquez sur **nouvelle connexion** et connectez-vous à votre serveur SQL Server.

![Informations de connexion](media/notebooks-guidance/connection-info.png)

## <a name="launch-notebooks"></a>Lancer des ordinateurs portables

Il existe plusieurs façons de lancer un nouveau bloc-notes.

- Accédez à la **Menu fichier** dans Azure Data Studio, puis cliquez sur **nouveau bloc-notes**.

    ![Nouveau bloc-notes](media/notebooks-guidance/file-new-notebook.png)

- Cliquez avec le bouton droit sur le **SQL Server** connexion et lancement puis **nouveau bloc-notes**.

    ![Nouveau bloc-notes](media/notebooks-guidance/server-new-notebook.png)

- Ouvrez la palette de commandes (**Ctrl + Maj + P**)), puis tapez **nouveau bloc-notes**. Un nouveau fichier nommé `Notebook-1.ipynb` s’ouvre.

## <a name="supported-kernels-and-attach-to-context"></a>Prise en charge les noyaux et d’attachement au contexte

L’Installation du bloc-notes dans Azure Data Studio en mode natif prend en charge que le noyau de SQL. Si vous êtes un développeur SQL et que vous souhaitez utiliser des blocs-notes, puis il s’agirait choisi noyau. 

Le noyau de SQL peut également servir à se connecter aux instances de serveur PostgreSQL. Si vous êtes un développeur de PostgreSQL et que vous souhaitez vous connecter les ordinateurs portables à votre serveur PostgreSQL, puis téléchargez le [ **PostgreSQL extension** ](../azure-data-studio/postgres-extension.md) dans la place de marché Azure Data Studio extension, puis Lancez **nouveau bloc-notes** pour ouvrir une instance de bloc-notes pour vous connecter au serveur PostgreSQL.

![Connexion de PostgreSQL](media/notebooks-guidance/sql-kernel-dropdown.png)

### <a name="sql-kernel"></a>Noyau SQL

Dans les cellules de code dans le bloc-notes, similaire à notre éditeur de requête, nous prenons en charge SQL moderne expérience qui facilite vos tâches quotidiennes avec des fonctionnalités intégrées comme un éditeur SQL riche, IntelliSense et extraits de code intégrés de codage. Extraits de code permettent de générer la syntaxe SQL appropriée pour créer des bases de données, tables, vues, procédures stockées, etc. et mettre à jour les objets de base de données existants. Utiliser des extraits de code pour créer rapidement des copies de votre base de données pour le développement ou à des fins de tests et pour générer et exécuter des scripts.

Cliquez sur **exécuter** pour exécuter chaque cellule.

Noyau de SQL pour vous connecter à une instance de SQL Server

![Noyau SQL](media/notebooks-guidance/intellisense-code-cell.png)

Résultats de requête

![Résultats de la requête](media/notebooks-guidance/sql-cell-results.png)

Noyau de SQL pour vous connecter à l’instance de serveur PostgreSQL 

![Connexion de PostgreSQL](media/notebooks-guidance/pgsql-code-cell.png)

Résultats de requête

![Résultats de la requête](media/notebooks-guidance/pgsql-cell-results.png)

Si vous souhaitez ajouter des cellules de texte à votre ordinateur portable attaché au noyau de SQL, cliquez sur le **+ texte** commande dans la barre d’outils.

![Barre d’outils du bloc-notes](media/notebooks-guidance/notebook-toolbar.png)

La cellule est modifiée en mode édition et tapez maintenant markdown et vous verrez la version préliminaire en même temps

![Cellule de markdown](media/notebooks-guidance/notebook-markdown-cell.png)

Cliquez en dehors de la cellule de texte pour afficher le texte markdown.

![Markdown text](media/notebooks-guidance/notebook-markdown-preview.png)


### <a name="configure-python-for-notebooks"></a>Configuration de Python pour les blocs-notes

Lorsque vous sélectionnez un des autres noyaux en dehors de SQL dans la liste déroulante du noyau, il vous invite à **Python de configurer des blocs-notes**. Les dépendances de bloc-notes sont installées dans un emplacement spécifié, mais vous pouvez décider s’il faut définir l’emplacement d’installation. Cette installation peut prendre un certain temps et il est recommandé pour ne pas fermer l’application jusqu'à ce que l’installation est terminée. Une fois l’installation terminée, vous pouvez commencer à écrire de code dans le langage pris en charge.

![Configurer python](media/notebooks-guidance/configure-python.png)

Une fois l’installation terminée, vous trouverez une notification dans l’historique des tâches ainsi que l’emplacement du serveur principal Jupyter en cours d’exécution dans le Terminal de sortie.

![Serveur principal de Jupyter](media/notebooks-guidance/jupyter-backend.png)

|Noyau|Description
|:-----|:-----
| Noyau SQL | Écrire du Code SQL ciblé sur votre base de données relationnelle.
|PySpark3 et le noyau PySpark| Écrire du code Python à l’aide de calcul Spark à partir du cluster.
|Noyau Spark|Écrire du code Scala et R à l’aide de calcul Spark à partir du cluster.
|Python Kernel|Écrire du code Python pour un développement local.

`Attach to` fournit le contexte pour le noyau à attacher. Si vous utilisez le noyau de SQL, vous pouvez `Attach to` un de vos instances de SQL Server.

Si vous utilisez le noyau de Python3 le `Attach to` est `localhost`. Vous pouvez utiliser ce noyau pour votre développement Python local.

Lorsque vous êtes connecté à SQL Server 2019 cluster de données volumineux, la valeur par défaut `Attach to` est ce point de terminaison du cluster et vous permettent de soumettre le code Python, Scala et R à l’aide du cluster de calcul Spark.

### <a name="code-cells-and-markdown-cells"></a>Les cellules de code et Markdown

Ajoutez une nouvelle cellule de code en cliquant sur le **+ Code** commande dans la barre d’outils.

Ajoutez une nouvelle cellule de texte en cliquant sur le **+ texte** commande dans la barre d’outils.

![Barre d’outils du bloc-notes](media/notebooks-guidance/notebook-toolbar.png)

La cellule est modifiée en mode édition et tapez maintenant markdown et vous verrez la version préliminaire en même temps

![Cellule de markdown](media/notebooks-guidance/notebook-markdown-cell.png)

Cliquez en dehors de la cellule de texte pour afficher le texte markdown.

![Markdown text](media/notebooks-guidance/notebook-markdown-preview.png)

### <a name="trusted-and-non-trusted"></a>Approuvés et Non approuvés

Blocs-notes ouvrir dans Studio de données Azure sont par défaut **approuvé**.

Si vous ouvrez un bloc-notes à partir d’une autre source, il s’ouvre dans **Non sécurisés** mode et que vous pouvez les rendre **approuvé**.

### <a name="run-cells"></a>Exécution des cellules
Si vous souhaitez exécuter toutes les cellules dans le bloc-notes, puis cliquez sur le **cellules exécuter** bouton dans la barre d’outils.

![Markdown text](media/notebooks-guidance/run-cell.png)


### <a name="clear-results"></a>Effacer les résultats

Si vous souhaitez effacer les résultats de toutes les cellules exécutées dans le bloc-notes, vous pouvez cliquer sur le **effacer les résultats** bouton dans la barre d’outils.

![Markdown text](media/notebooks-guidance/clear-results.png)

### <a name="save"></a>Enregistrer

Pour enregistrer le bloc-notes effectuez l’une des opérations suivantes.

- Sélectionnez Ctrl + S
- Cliquez sur **fichier** > **enregistrer**
- Cliquez sur **fichier** > **enregistrer en tant que...**
- Cliquez sur **fichier** > **Enregistrer tout** 
- Dans la palette de commandes, entrez **fichier : Enregistrer** 

### <a name="pyspark3pyspark-kernel"></a>Noyau Pyspark3/PySpark

Choisissez le `PySpark Kernel` et dans le type de cellule dans le code suivant.

Cliquez sur **Exécuter**.

L’Application Spark est démarrée et renvoie le résultat suivant :

![Application Spark](media/notebooks-guidance/pyspark.png)

### <a name="spark-kernel--scala-language"></a>Noyau Spark | Langage de Scala

Choisissez le `Spark|Scala Kernel` et dans le type de cellule dans le code suivant.

![Spark Scala](media/notebooks-guidance/spark-scala.png)

Vous pouvez également afficher les Options « cellule » lorsque vous cliquez sur l’icône des options ci-dessous :

![Options de cellule](media/notebooks-guidance/scala-cell-options.png)

### <a name="spark-kernel--r-language"></a>Noyau Spark | Langage R

Choisissez le Spark | R dans la liste déroulante pour les noyaux. Dans la cellule, tapez ou collez le code. Cliquez sur **exécuter** pour afficher la sortie suivante.

![Spark R](media/notebooks-guidance/spark-r.png)

### <a name="local-python-kernel"></a>Noyau Python local

Choisissez le noyau Python local et dans le type de cellule :

![Python local](media/notebooks-guidance/local-python.png)

## <a name="manage-packages"></a>Gérer les Packages

Une des choses que nous avons optimisé pour le développement Python local était d’incluent la possibilité d’installer des packages qui les clients devraient pour leurs scénarios. Par défaut, nous incluons les packages courants tels que `pandas`, `numpy` etc., mais si vous attendez un package qui n’est pas inclus ensuite écrire le code suivant dans la cellule du bloc-notes : 

```python
import <package-name>
```

Lorsque vous exécutez cette commande, `Module not found` est retournée. Si votre package existe, puis vous pas obtiendrez l’erreur.

Si elle retourne un `Module not Found` erreur, puis cliquez sur **gérer les Packages** pour lancer le terminal. Vous pouvez désormais installer les packages localement. Utilisez les commandes suivantes pour installer les packages :

```bash
./pip install <package-name>
```

   > [!Tip]
   > Sur Mac, suivez les instructions dans la fenêtre de Terminal pour installer des packages. 

Une fois que le package est installé, vous devez pouvoir dans la cellule du bloc-notes, tapez la commande suivante :

```python
import <package-name>
```

Pour désinstaller un package, utilisez la commande suivante à partir de votre terminal :

```bash
./pip uninstall <package-name>
```

## <a name="next-steps"></a>Étapes suivantes

Pour savoir comment utiliser un bloc-notes existant, consultez [comment gérer des ordinateurs portables dans Azure Data Studio](notebooks-how-to-manage.md).