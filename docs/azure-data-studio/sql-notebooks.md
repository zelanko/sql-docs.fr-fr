---
title: Comment utiliser des blocs-notes de SQL dans Azure Data Studio
titleSuffix: Azure Data Studio
description: Découvrez comment utiliser des blocs-notes de SQL dans Azure Data Studio
ms.custom: seodec18
ms.date: 06/28/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: achatter; alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 9af2e04a3973eddfcd714c7968c35e544302aba9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959263"
---
# <a name="how-to-use-notebooks-in-azure-data-studio"></a>Comment utiliser des blocs-notes dans Azure Data Studio

Cet article décrit comment lancer l’expérience de bloc-notes dans Azure Data Studio et comment commencer à créer vos propres blocs-notes. Il montre également comment écrire à l’aide de différents noyaux de blocs-notes.


## <a name="connect-to-sql-server"></a>Se connecter à SQL Server

Vous pouvez vous connecter au type de connexion Microsoft SQL Server dans Azure Data Studio.
Dans Azure Data Studio, vous pouvez également appuyer sur F1, puis cliquez sur **nouvelle connexion** et connectez-vous à votre serveur SQL Server.

![Image1](media/sql-notebooks/connection-info.png)

## <a name="launch-notebooks"></a>Lancer des ordinateurs portables

Il existe plusieurs façons de lancer un nouveau bloc-notes.

1. Accédez à la **Menu fichier** dans Azure Data Studio, puis cliquez sur **nouveau bloc-notes**.

    ![Image3](media/sql-notebooks/file-new-notebook.png)

3. Cliquez avec le bouton droit sur le **SQL Server** connexion et lancement puis **nouveau bloc-notes**. 
    ![image3](media/sql-notebooks/server-new-notebook.png)

4. Ouvrez la palette de commandes (**Ctrl + Maj + P**)), puis tapez **nouveau bloc-notes**. Un nouveau fichier nommé `Notebook-1.ipynb` s’ouvre.

## <a name="supported-kernels-and-attach-to-context"></a>Prise en charge les noyaux et d’attachement au contexte

L’Installation du bloc-notes dans Azure Data Studio en mode natif prend en charge que le noyau de SQL. Si vous êtes un développeur SQL et que vous souhaitez utiliser des blocs-notes, puis il s’agirait choisi noyau. 

Le noyau de SQL peut également servir à se connecter aux instances de serveur PostgreSQL. Si vous êtes un développeur de PostgreSQL et que vous souhaitez vous connecter à votre serveur PostgreSQL, puis téléchargez le [ **PostgreSQL extension** ](postgres-extension.md) dans la place de marché Azure Data Studio extension.

![image7](media/sql-notebooks/sql-kernel-dropdown.png)

### <a name="sql-kernel"></a>Noyau SQL

Dans les cellules de code dans le bloc-notes, similaire à notre éditeur de requête, nous prenons en charge SQL moderne expérience qui facilite vos tâches quotidiennes avec des fonctionnalités intégrées comme un éditeur SQL riche, IntelliSense et extraits de code intégrés de codage. Extraits de code permettent de générer la syntaxe SQL appropriée pour créer des bases de données, tables, vues, procédures stockées, etc. et mettre à jour les objets de base de données existants. Utiliser des extraits de code pour créer rapidement des copies de votre base de données pour le développement ou à des fins de tests et pour générer et exécuter des scripts.

Cliquez sur **exécuter** pour exécuter chaque cellule.

Noyau de SQL pour vous connecter à une instance de SQL Server

![image7](media/sql-notebooks/intellisense-code-cell.png)

Résultats de requête

![Image19](media/sql-notebooks/sql-cell-results.png)

Noyau de SQL pour vous connecter à l’instance de serveur PostgreSQL 

![Image18](media/sql-notebooks/pgsql-code-cell.png)

Résultats de requête

![Image20](media/sql-notebooks/pgsql-cell-results.png)

### <a name="configure-python-for-notebooks"></a>Configuration de Python pour les blocs-notes

Lorsque vous sélectionnez un des autres noyaux en dehors de SQL dans la liste déroulante du noyau, il vous invite à **Python de configurer des blocs-notes**. Les dépendances de bloc-notes sont installées dans un emplacement spécifié, mais vous pouvez décider s’il faut définir l’emplacement d’installation. Cette installation peut prendre un certain temps et il est recommandé pour ne pas fermer l’application jusqu'à ce que l’installation est terminée. Une fois l’installation terminée, vous pouvez commencer à écrire de code dans le langage pris en charge.

![image21](media/sql-notebooks/configure-python.png)

Une fois l’installation terminée, vous trouverez une notification dans l’historique des tâches ainsi que l’emplacement du serveur principal Jupyter en cours d’exécution dans le Terminal de sortie.

![Image22](media/sql-notebooks/jupyter-backend.png)

|Noyau|Description
|:-----|:-----
| Noyau SQL | Écrire du Code SQL ciblé sur votre base de données relationnelle.
|PySpark3 et le noyau PySpark| Écrire du code Python à l’aide de calcul Spark à partir du cluster.
|Noyau Spark|Écrire du code Scala et R à l’aide de calcul Spark à partir du cluster.
|Noyau Python|Écrire du code Python pour un développement local.

`Attach to` fournit le contexte pour le noyau à attacher. Si vous utilisez le noyau de SQL, vous pouvez `Attach to` un de vos instances de SQL Server.

Si vous utilisez le noyau de Python3 le `Attach to` est `localhost`. Vous pouvez utiliser ce noyau pour votre développement Python local.

Lorsque vous êtes connecté à SQL Server 2019 cluster de données volumineux, la valeur par défaut `Attach to` est ce point de terminaison du cluster et vous permettent de soumettre le code Python, Scala et R à l’aide du cluster de calcul Spark.

### <a name="code-cells-and-markdown-cells"></a>Les cellules de code et Markdown

Ajoutez une nouvelle cellule de code en cliquant sur le **+ Code** commande dans la barre d’outils.

Ajoutez une nouvelle cellule de texte en cliquant sur le **+ texte** commande dans la barre d’outils.

![image8](media/sql-notebooks/notebook-toolbar.png)

La cellule est modifiée en mode édition et tapez maintenant markdown et vous verrez la version préliminaire en même temps

![image9](media/sql-notebooks/notebook-markdown-cell.png)

Cliquez en dehors de la cellule de texte pour afficher le texte markdown.

![Image10](media/sql-notebooks/notebook-markdown-preview.png)

### <a name="trusted-and-non-trusted"></a>Approuvés et Non approuvés

Blocs-notes ouvrir dans Studio de données Azure sont par défaut **approuvé**.

Si vous ouvrez un bloc-notes à partir d’une autre source, il s’ouvre dans **Non sécurisés** mode et que vous pouvez les rendre **approuvé**.

### <a name="save"></a>Enregistrer 

Vous pouvez enregistrer le bloc-notes par **Ctrl + S** ou en cliquant sur le **l’enregistrement du fichier**, **fichier Enregistrer sous...**  et **Enregistrer tout fichier** commandes dans le menu fichier et **fichier : Enregistrer** commandes entrées dans la palette de commandes.

### <a name="pyspark3pyspark-kernel"></a>Noyau Pyspark3/PySpark

Choisissez le `PySpark Kernel` et dans le type de cellule dans le code suivant.

Cliquez sur **Exécuter**.

L’Application Spark est démarrée et renvoie le résultat suivant :

![Image12](media/sql-notebooks/pyspark.png)

### <a name="spark-kernel--scala-language"></a>Noyau Spark | Langage de Scala

Choisissez le `Spark|Scala Kernel` et dans le type de cellule dans le code suivant.

![Image13](media/sql-notebooks/spark-scala.png)

Vous pouvez également afficher les Options « cellule » lorsque vous cliquez sur l’icône des options ci-dessous :

![Image14](media/sql-notebooks/scala-cell-options.png)

### <a name="spark-kernel--r-language"></a>Noyau Spark | Langage R

Choisissez le Spark | R dans la liste déroulante pour les noyaux. Dans la cellule, tapez ou collez le code. Cliquez sur **exécuter** pour afficher la sortie suivante.

![Image15](media/sql-notebooks/spark-r.png)

### <a name="local-python-kernel"></a>Noyau Python local

Choisissez le noyau Python local et dans le type de cellule :

![Image16](media/sql-notebooks/local-python.png)

## <a name="manage-packages"></a>Gérer les Packages
Une des choses que nous avons optimisé pour le développement Python local était d’incluent la possibilité d’installer des packages qui les clients devraient pour leurs scénarios. Par défaut, nous incluons les packages courants tels que `pandas`, `numpy` etc., mais si vous attendez un package qui n’est pas inclus ensuite écrire le code suivant dans la cellule du bloc-notes : 

```python
import <package-name>
```

Lorsque vous exécutez cette commande, `Module not found` est retournée. Si votre package existe, puis vous pas obtiendrez l’erreur.

Si elle retourne un `Module not Found` erreur, puis cliquez sur **gérer les Packages** pour lancer l’expérience de l’Assistant. 

![Image17](media/sql-notebooks/manage-packages.png)

Dans cet Assistant, vous serez en mesure de voir les **installé** packages. Vous pouvez parcourir la liste et la version associée de chacun de ces packages. Si vous avez besoin pour **désinstaller** aucune de ces packages, puis vous pouvez cliquer sur un des packages, puis cliquez sur le **désinstaller des packages sélectionnés** option.

Vous serez également en mesure de cliquer sur **Ajouter nouveau** des packages vers **recherche** pour un package particulier, choisissez la version associée, puis cliquez sur **installer**. Par défaut, nous sélectionnons la dernière version du package recherché. 

Une fois que le package est installé, vous devez pouvoir dans la cellule du bloc-notes, tapez la commande suivante :

```python
import <package-name>
```

Si vous avez besoin pour **désinstaller** aucune de ces packages, puis vous pouvez cliquer sur un ou plusieurs packages, puis cliquez sur le **désinstaller des packages sélectionnés** option.

## <a name="next-steps"></a>Étapes suivantes

Pour savoir comment utiliser un bloc-notes existant, consultez [comment gérer des ordinateurs portables dans Azure Data Studio](https://docs.microsoft.com/sql/big-data-cluster/notebooks-how-to-manage?view=sqlallproducts-allversions).