---
title: Exécuter les notebooks dans Azure Data Studio
titleSuffix: SQL Server 2019 big data clusters
description: Cet article explique comment exécuter les blocs-notes Jupyter dans Azure Data Studio conneected vers un cluster de données volumineuses de SQL Server 2019.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/12/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 44ba203fcd7445add8fce00dd64913f85bcf4cc1
ms.sourcegitcommit: 11ab8a241a6d884b113b3cf475b2b9ed61ff00e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58161656"
---
# <a name="how-to-use-notebooks-in-sql-server-2019-preview"></a>Comment utiliser des blocs-notes en version préliminaire de SQL Server 2019

Cet article décrit comment lancer les blocs-notes Jupyter sur un cluster big data et comment commencer à créer vos propres blocs-notes. Il montre également comment envoyer des travaux sur le cluster.

## <a name="prerequisites"></a>Prérequis

Pour utiliser des blocs-notes, vous devez installer les conditions préalables suivantes :

- [Un cluster de données volumineux de SQL Server 2019](deployment-guidance.md)
- [Outils de données volumineuses de SQL Server 2019](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **Extension de SQL Server 2019**
   - **kubectl**

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="connect-to-the-sql-server-big-data-cluster-end-point"></a>Se connecter au point de terminaison du cluster SQL Server big data

Vous pouvez vous connecter à différents points de terminaison dans le cluster. Vous pouvez vous connecter pour le type de connexion de Microsoft SQL Server ou pour le point de terminaison de cluster de données SQL Server.
Dans Azure Data Studio, appuyez sur F1, puis cliquez sur **nouvelle connexion** et vous pouvez vous connecter à votre point de terminaison de cluster de données SQL Server.

![image1](media/notebooks-guidance/image1.png)

## <a name="browse-hdfs"></a>Browse HDFS

Une fois que vous vous connectez, vous serez en mesure de parcourir votre dossier HDFS. SQL Server démarre WebHDFS est démarré lorsque le déploiement est terminé. Avec WebHDFS, vous pouvez **Actualiser**, ajouter **nouveau répertoire**, **télécharger** fichiers, et **supprimer**.

![image2](media/notebooks-guidance/image2.png)

Ces opérations simples vous permettent d’importer vos propres données dans HDFS.

## <a name="launch-new-notebooks"></a>Lancer de nouveaux ordinateurs portables

>[!NOTE]
>Si vous avez plusieurs processus Python en cours d’exécution dans votre environnement, vous devez tout d’abord supprimer la `.scaleoutdata` dossier sous votre répertoire installé. Il doit déclencher le `Reinstall Notebook dependencies` tâche dans Azure Data Studio. Il prendra quelques minutes pour toutes les dépendances à installer.

S’il existe des problèmes pour installer les dépendances du bloc-notes, cliquez sur Ctrl + Maj + P ou pour Macintosh Cmd + Maj + P, puis tapez `Reinstall Notebook dependencies` dans la palette de commandes.

![image3](media/notebooks-guidance/image3.png)

Il existe plusieurs façons de lancer un nouveau bloc-notes.

1. À partir de la **gérer le tableau de bord**. Après avoir établi une connexion, vous verrez un tableau de bord. Cliquez sur **nouveau bloc-notes** tâche du tableau de bord.
  
    ![image4](media/notebooks-guidance/image4.png)

1. Avec le bouton droit de la connexion HDFS/Spark et cliquez sur **nouveau bloc-notes** dans le menu contextuel.

    ![image5](media/notebooks-guidance/image5.png)

    Un nouveau fichier nommé `Notebook-0.ipynb` s’ouvre.

    ![image6](media/notebooks-guidance/image6.png)

Lorsque vous ouvrez le bloc-notes à partir de la palette de commandes, le bloc-notes s’ouvre en tant que `Untitled-0.ipynb`.

## <a name="supported-kernels-and-attach-to-context"></a>Prise en charge les noyaux et d’attachement au contexte

L’Installation de l’ordinateur portable prend en charge les noyaux PySpark et Spark, Spark Magic, ce qui vous permet d’écrire du code Python et Scala à l’aide de Spark. Si vous le souhaitez, vous pouvez choisir de Python à des fins de développement local.

![image7](media/notebooks-guidance/image7.png)

Lorsque vous sélectionnez une de ces noyaux, l’installation configure ce noyau dans l’environnement virtuel et vous pouvez commencer à écrire de code dans le langage pris en charge.

|Noyau|Description
|:-----|:-----
|PySpark3 et le noyau PySpark| Écrire du code Python à l’aide de calcul Spark à partir du cluster.
|Noyau Spark|Écrire du code Scala et R à l’aide de calcul Spark à partir du cluster.
|Python Kernel|Écrire du code Python pour un développement local.

`Attach to` fournit le contexte pour le noyau à attacher. Lorsque vous êtes connecté à SQL Server des données big cluster point de terminaison, la valeur par défaut `Attach to` est ce point de terminaison du cluster.

Lorsque vous n’êtes pas connecté au point de terminaison du cluster SQL Server des données volumineuses, la valeur par défaut du noyau est Python et `Attach to` est `localhost`.

## <a name="hello-world-in-different-contexts"></a>Hello world dans différents contextes

### <a name="pyspark3pyspark-kernel"></a>Noyau Pyspark3/PySpark

Choisissez le noyau PySpark et dans le type de cellule dans le code suivant.

Cliquez sur **Exécuter**.

L’Application Spark est démarrée et renvoie le résultat suivant :

![image8](media/notebooks-guidance/image8.png)

### <a name="spark-kernel--scala-language"></a>Noyau Spark | Langage de Scala

Choisissez le Spark | Noyau de Scala et dans le type de cellule dans le code suivant.

![image9](media/notebooks-guidance/image9.png)

Ajoutez une nouvelle cellule de code en cliquant sur le **+ Code** commande dans la barre d’outils.

Maintenant, choisissez le Spark | Scala dans la liste déroulante pour les noyaux et dans le type de cellule/coller dans :

![image10](media/notebooks-guidance/image10.png)

Vous pouvez également afficher les Options « cellule » lorsque vous cliquez sur l’icône des options ci-dessous :

![image11](media/notebooks-guidance/image11.png)

### <a name="spark-kernel--r-language"></a>Noyau Spark | Langage R

Choisissez le Spark | R dans la liste déroulante pour les noyaux. Dans la cellule, tapez ou collez le code. Cliquez sur **exécuter** pour afficher la sortie suivante.

![image13](media/notebooks-guidance/image13.png)

### <a name="local-python-kernel"></a>Noyau Python local

Choisissez le noyau Python local et dans le type de cellule :

![image14](media/notebooks-guidance/image14.png)

### <a name="markdown-text"></a>Markdown text

Ajoutez une nouvelle cellule de texte en cliquant sur le **+ texte** commande dans la barre d’outils.

![image15](media/notebooks-guidance/image15.png)

Double-cliquez dans la cellule de texte à modifier pour modifier la vue 

![image16](media/notebooks-guidance/image16.png)

La cellule est modifiée en mode édition

![image17](media/notebooks-guidance/image17.png)

Markdown de type et que vous voyez à présent la version préliminaire en même temps

![image18](media/notebooks-guidance/image18.png)

Cliquez sur **Exécuter**. Démarrage de l’application Spark crée la session Spark en tant que **spark** et définit le **HelloWorld** objet.

Le bloc-notes doit ressembler à l’image suivante.

Cliquez en dehors de la cellule de texte change en mode Aperçu et masque le code markdown.

![image19](media/notebooks-guidance/image19.png)


## <a name="manage-packages"></a>Gérer les Packages
Une des choses que nous avons optimisé pour le développement Python local était d’incluent la possibilité d’installer des packages qui les clients devraient pour leurs scénarios. Par défaut, nous incluons les packages courants tels que `pandas`, `numpy` etc., mais si vous attendez un package qui n’est pas inclus ensuite écrire le code suivant dans la cellule du bloc-notes : 

```python
import <package-name>
```

Lorsque vous exécutez cette commande, `Module not found` est retournée. Si votre package existe, puis vous pas obtiendrez l’erreur.

Si elle retourne un `Module not Found` erreur, puis cliquez sur **gérer les Packages** pour lancer le terminal avec le chemin d’accès pour votre Virtualenv identifié. Vous pouvez désormais installer les packages localement. Utilisez les commandes suivantes pour installer les packages :

```bash
./pip install <package-name>
```

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