---
title: Comment utiliser des blocs-notes en version préliminaire de SQL Server 2019 | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 9f9db16431cd6c3befbb32383725ec008f5a9081
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221635"
---
# <a name="how-to-use-notebooks-in-sql-server-2019-preview"></a>Comment utiliser des blocs-notes en version préliminaire de SQL Server 2019

Cet article décrit comment lancer des blocs-notes Jupyter sur le cluster et commencer à créer vos propres blocs-notes. Il montre également comment envoyer des travaux sur le cluster.

## <a name="prerequisites"></a>Prérequis

Pour utiliser des blocs-notes, vous devez installer les conditions préalables suivantes :

- [Un cluster de données volumineux de SQL Server 2019](deployment-guidance.md)
- [Azure Data Studio](../azure-data-studio/what-is.md)
- [L’extension de SQL Server 2019 (version préliminaire)](../azure-data-studio/sql-server-2019-extension.md).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="connect-to-the-hadoop-gateway-knox-end-point"></a>Se connecter au point de terminaison Hadoop passerelle Knox

Vous pouvez vous connecter à différents points de terminaison dans le cluster. Vous pouvez vous connecter au type de connexion Microsoft SQL Server ou au point de terminaison de passerelle HDFS/Spark.
Dans Azure Data Studio (version préliminaire), appuyez sur F1, puis cliquez sur **nouvelle connexion** et vous pouvez vous connecter à votre point de terminaison de passerelle HDFS/Spark.

![Image1](media/notebooks-guidance/image1.png)

## <a name="browse-hdfs"></a>Parcourir le HDFS

Une fois que vous vous connectez, vous serez en mesure de parcourir votre dossier HDFS. WebHDFS démarre lorsque le déploiement terminé, et vous pourrez **Actualiser**, ajouter **nouveau répertoire**, **télécharger** fichiers, et **supprimer**.

![Image2](media/notebooks-guidance/image2.png)

Ces opérations simples vous permettent d’importer vos propres données dans HDFS.

## <a name="launch-new-notebooks"></a>Lancer de nouveaux ordinateurs portables

>[!NOTE]
>Si vous avez plusieurs processus Python en cours d’exécution dans votre environnement, vous devez tout d’abord supprimer la `.scaleoutdata` dossier sous votre répertoire installé. Il doit déclencher le `Reinstall Notebook dependencies` tâche dans Azure Data Studio. Il prendra quelques minutes pour toutes les dépendances à installer.

S’il existe des problèmes pour installer les dépendances du bloc-notes, cliquez sur Ctrl + Maj + P ou pour Macintosh Cmd + Maj + P, puis tapez `Reinstall Notebook dependencies` dans la palette de commandes.

![Image3](media/notebooks-guidance/image3.png)

Il existe plusieurs façons de lancer un nouveau bloc-notes.

1. À partir de la **gérer le tableau de bord**. Après avoir établi une connexion, vous verrez un tableau de bord. Cliquez sur **nouveau bloc-notes** tâche du tableau de bord.

  ![image4](media/notebooks-guidance/image4.png)

1. Avec le bouton droit de la connexion HDFS/Spark et cliquez sur **nouveau bloc-notes** dans le menu contextuel.

  ![image5](media/notebooks-guidance/image5.png)

  Fournissez un nom de votre ordinateur portable, par exemple, `Test.ipynb`. Cliquez sur **Enregistrer**.

![image6](media/notebooks-guidance/image6.png)

## <a name="supported-kernels-and-attach-to-context"></a>Prise en charge les noyaux et d’attachement au contexte

L’Installation de l’ordinateur portable prend en charge les noyaux PySpark et Spark, Spark Magic, ce qui vous permet d’écrire du code Python et Scala à l’aide de Spark. Si vous le souhaitez, vous pouvez choisir de Python à des fins de développement local.

![image7](media/notebooks-guidance/image7.png)

Lorsque vous sélectionnez une de ces noyaux, nous allons installer ce noyau dans l’environnement virtuel et vous pouvez commencer à écrire de code dans le langage pris en charge.

|Noyau|Description
|:-----|:-----
|Noyau PySpark|Pour l’écriture de code Python à l’aide de calcul Spark à partir du cluster.
|Noyau Spark|Pour l’écriture de code Scala à l’aide de calcul Spark à partir du cluster.
|Noyau Python|Pour l’écriture de code Python pour un développement local.

Le `Attach to` fournit le contexte pour le noyau à attacher. Lorsque vous êtes connecté à la fin de la passerelle HDFS/Spark (Knox) point de la valeur par défaut `Attach to` est ce point de terminaison du cluster.

![image8](media/notebooks-guidance/image8.png)

## <a name="hello-world-in-different-contexts"></a>Hello world dans différents contextes

### <a name="pyspark-kernel"></a>Noyau Pyspark

Choisissez le noyau PySpark et dans le type de cellule dans le code suivant :

![image9](media/notebooks-guidance/image9.png)

Cliquez sur l’exécution et que vous devez voir l’Application Spark en cours de démarrage et vous verrez la sortie suivante :

![Image10](media/notebooks-guidance/image10.png)

Le résultat doit ressembler à quelque chose de similaire à l’image suivante.

![Image11](media/notebooks-guidance/image11.png)

### <a name="spark-kernel"></a>Noyau Spark
Ajoutez une nouvelle cellule de code en cliquant sur le **+ Code** commande dans la barre d’outils.

![Image12](media/notebooks-guidance/image12.png)

Vous pouvez également afficher les Options « cellule » lorsque vous cliquez sur l’icône des options ci-dessous :

![Image13](media/notebooks-guidance/image13.png)

Voici les options pour chaque cellule :

![Image14](media/notebooks-guidance/image14.png)-

Maintenant, choisissez le noyau Spark dans la liste déroulante pour les noyaux et dans le type de cellule/coller dans :

![Image15](media/notebooks-guidance/image15.png)

Cliquez sur **exécuter** et vous devez voir l’Application Spark en cours de démarrage et que cette opération crée la session Spark en tant que **spark** et définira le **HelloWorld** objet.

Le bloc-notes doit ressembler à l’image suivante.

![Image16](media/notebooks-guidance/image16.png)

Une fois que vous définissez l’objet puis dans la prochaine cellule du bloc-notes, tapez le code suivant :

![Image17](media/notebooks-guidance/image17.png)

Cliquez sur **exécuter** dans le bloc-notes menu doit s’afficher « Hello, world ! » dans la sortie.

![Image18](media/notebooks-guidance/image18.png)

### <a name="local-python-kernel"></a>Noyau python local
Choisissez le noyau Python local et dans le type de cellule :

![Image19](media/notebooks-guidance/image19.png)

Vous devez voir la sortie suivante :

![Image20](media/notebooks-guidance/image20.png)

### <a name="markdown-text"></a>Texte markdown
Ajoutez une nouvelle cellule de texte en cliquant sur le **+ texte** commande dans la barre d’outils.

![Image21](media/notebooks-guidance/image21.png)

Cliquez sur l’icône d’aperçu pour ajouter votre markdown

![Image22](media/notebooks-guidance/image22.png)

Cliquez sur l’icône d’aperçu pour activer/désactiver le consultez simplement la syntaxe markdown

![Image23](media/notebooks-guidance/image23.png)

## <a name="manage-packages"></a>Gérer les Packages
Une des choses que nous avons optimisé pour le développement Python local était d’incluent la possibilité d’installer des packages qui les clients devraient pour leurs scénarios. Par défaut, nous incluons les packages courants tels que pandas, numpy, etc., mais si vous attendez un package qui n’est pas inclus puis écrire le code suivant dans la cellule du bloc-notes : 

```python
import <package-name>
```

Lorsque vous exécutez cette commande, vous obtiendrez un `Module not found` erreur. Si votre package existe, puis vous pas obtiendrez l’erreur.

Si vous trouvez un `Module not Found` erreur, puis cliquez sur **gérer les Packages** pour lancer le terminal avec le chemin d’accès pour votre Virtualenv identifié. Vous pouvez désormais installer les packages localement. Utilisez les commandes suivantes pour installer les packages :

```bash
./pip install <package-name>
```

Une fois que le package est installé, vous devez pouvoir dans la cellule du bloc-notes, tapez la commande suivante :

```python
import <package-name>
```

Maintenant lorsque vous exécutez la cellule, vous devez obtenir n’est plus le `Module not found` erreur.

Pour désinstaller un package, utilisez la commande suivante à partir de votre terminal :

```bash
./pip uninstall <package-name>
```

## <a name="next-steps"></a>Étapes suivantes

Pour savoir comment utiliser un bloc-notes existant, consultez [comment gérer des ordinateurs portables dans Azure Data Studio](notebooks-how-to-manage.md).