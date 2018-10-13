---
title: Comment utiliser des blocs-notes en version préliminaire de SQL Server 2019 | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/05/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 137da00959f6f8d3498bb3d063ceb21337266aef
ms.sourcegitcommit: ce4b39bf88c9a423ff240a7e3ac840a532c6fcae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48878012"
---
# <a name="how-to-use-notebooks-in-sql-server-2019-preview"></a>Comment utiliser des blocs-notes en version préliminaire de SQL Server 2019

Cet article explique comment lancer les blocs-notes sur un cluster de données volumineux de SQL Server 2019. Il montre également comment commencer à créer vos propres blocs-notes et comment envoyer des travaux sur le cluster.

## <a name="prerequisites"></a>Prérequis

Pour utiliser des blocs-notes, vous devez installer les conditions préalables suivantes :

- [Un cluster de données volumineux de SQL Server 2019](deployment-guidance.md)
- [Studio de données Azure](../azure-data-studio/what-is.md)
- [L’extension de SQL Server 2019 (version préliminaire)](../azure-data-studio/sql-server-2019-extension.md).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="connect-to-the-sql-server-big-data-cluster-end-point"></a>Se connecter pour le point de terminaison du cluster volumineuses de données SQL Server

Vous pouvez vous connecter à différents points de terminaison dans le cluster. Vous pouvez vous connecter pour le type de connexion de Microsoft SQL Server ou pour le point de terminaison du cluster volumineuses de données SQL Server.

Dans Azure Data Studio (version préliminaire), tapez **F1** > **nouvelle connexion**et vous connecter à votre point de terminaison du cluster volumineuses de données SQL Server.

![Image1](media/notebooks-guidance/image1.png)

## <a name="browse-hdfs"></a>Parcourir le HDFS
Une fois que vous vous connectez, vous serez en mesure de parcourir votre dossier HDFS. WebHDFS démarre lorsque le déploiement terminé, et vous pourrez **Actualiser**, ajouter **nouveau répertoire**, **télécharger** fichiers, et **supprimer**.

![Image2](media/notebooks-guidance/image2.png)

Ces opérations simples vous permettent d’importer vos propres données dans HDFS.

## <a name="launch-new-notebooks"></a>Lancer de nouveaux ordinateurs portables

Il existe plusieurs façons de lancer un nouveau bloc-notes.

1. À partir du tableau de bord de gestion. Sur la création d’une nouvelle connexion, vous verrez un tableau de bord. Cliquez sur la tâche nouveau bloc-notes à partir du tableau de bord.

  ![Image3](media/notebooks-guidance/image3.png)

1. Cliquez avec le bouton droit sur la connexion HDFS/Spark et que vous avez un nouveau bloc-notes dans le menu contextuel

![image4](media/notebooks-guidance/image4.png)

Fournissez un nom de votre bloc-notes (exemple : *Test.ipynb*) et cliquez sur **enregistrer**.

![image5](media/notebooks-guidance/image5.png)

## <a name="supported-kernels-and-attach-to-context"></a>Prise en charge les noyaux et d’attachement au contexte

Dans notre Installation Notebook, nous prenons en charge les noyaux PySpark et Spark, Spark Magic qui permettent aux utilisateurs d’écrire du code Python et Scala à l’aide de Spark. Nous permettent également aux utilisateurs de choisir les Python pour leurs à des fins de développement local.

![image6](media/notebooks-guidance/image6.png)

Lorsque vous sélectionnez une de ces noyaux, nous allons installer ce noyau dans l’environnement virtuel et vous pouvez commencer à écrire de code dans le langage pris en charge.

| Noyau | Description
|---- |----
|Noyau PySpark| Pour l’écriture de code Python à l’aide de Spark, de calcul à partir du cluster.
|Noyau Spark|Pour l’écriture de code Scala à l’aide de Spark, de calcul à partir du cluster.
|Noyau Python|Pour l’écriture de code Python pour un développement local.

La sélection pour attacher fournit le contexte pour le noyau à attacher. Lorsque vous êtes connecté pour le point de terminaison du cluster volumineuses de données SQL Server, la sélection par défaut à attacher sera ce point de terminaison du cluster.

![image7](media/notebooks-guidance/image7.png)

> [!NOTE]
> Par défaut, l’application Spark est configurée avec le 1 pilote et 3 exécuteurs qui prendront environ 8,5 Go de mémoire. La configuration recommandée pour exécuter plusieurs sessions de spark est pour chaque serveur dans le cluster pour avoir au moins 32 Go de mémoire (par exemple, dans un environnement AKS utiliser **Standard_D8_v3** tailles de machines virtuelles, qui ont de 32 Go de mémoire).

## <a name="hello-world-in-the-different-contexts"></a>Hello world dans les différents contextes

### <a name="pyspark-kernel"></a>Noyau Pyspark

Choisissez le noyau PySpark et dans le type de cellule dans le code suivant :

![image8](media/notebooks-guidance/image8.png)

Cliquez sur l’exécution et que vous devez voir l’Application Spark en cours de démarrage et vous verrez la sortie suivante :

![image9](media/notebooks-guidance/image9.png)

Le résultat doit ressembler à quelque chose de similaire à l’image suivante.

![Image10](media/notebooks-guidance/image10.png)

### <a name="spark-kernel"></a>Noyau Spark
Ajoutez une nouvelle cellule de code en cliquant sur le + Code de commande dans la barre d’outils.

![Image11](media/notebooks-guidance/image11.png)

Choisissez le noyau Spark dans la liste déroulante pour les noyaux et dans le type de cellule/coller dans 

![Image12](media/notebooks-guidance/image12.png)

Cliquez sur **exécuter** vous devez voir l’Application Spark en cours de démarrage et cela créera la session Spark **spark** et définira le **HelloWorld** objet.

Le bloc-notes doit ressembler à l’image suivante.

![Image13](media/notebooks-guidance/image13.png)

Une fois que vous définissez l’objet de puis dans le type de cellule bloc-notes suivant dans le code suivant :

![Image14](media/notebooks-guidance/image14.png)

Cliquez sur **exécuter** dans le bloc-notes menu doit s’afficher « Hello, world ! » dans la sortie.

![Image15](media/notebooks-guidance/image15.png)

### <a name="local-python-kernel"></a>Noyau python local
Choisissez le noyau Python local et dans le type de cellule dans **

![Image16](media/notebooks-guidance/image16.png)

Vous devez voir la sortie suivante :

![Image17](media/notebooks-guidance/image17.png)

### <a name="markdown-text"></a>Texte markdown
Ajoutez une nouvelle cellule de texte en cliquant sur le + commande de texte dans la barre d’outils.

![Image18](media/notebooks-guidance/image18.png)

Cliquez sur l’icône d’aperçu pour ajouter votre markdown

![Image19](media/notebooks-guidance/image19.png)

Cliquez sur l’icône d’aperçu pour activer/désactiver le consultez simplement la syntaxe markdown

![Image20](media/notebooks-guidance/image20.png)

## <a name="manage-packages"></a>Gérer les Packages
Une des choses que nous avons optimisé pour le développement Python local était d’incluent la possibilité d’installer des packages qui les clients devraient pour leurs scénarios. Par défaut, nous incluons les packages courants tels que pandas, numpy, etc., mais si vous attendez un package qui n’est pas inclus puis écrire le code suivant dans la cellule du bloc-notes

```python
import <package-name>
```

Lorsque vous exécutez cette commande, vous obtiendrez un `Module not found` erreur. Si votre package existe, puis vous pas obtiendrez l’erreur.

Si vous trouvez un `Module not Found` erreur, puis cliquez sur le **gérer les Packages** pour lancer le terminal avec le chemin d’accès pour votre Virtualenv identifié. Vous pouvez désormais installer les packages localement. Utilisez la commande suivante pour installer les packages :

```
./pip install <package-name>
```

Une fois que le package est installé, vous devez pouvoir dans la cellule du bloc-notes, tapez la commande suivante :

```python
import <package-name>
```

Maintenant lorsque vous exécutez la cellule, vous devez obtenir n’est plus le `Module not found` erreur.

Si vous souhaitez désinstaller un package, utilisez la commande suivante à partir de votre terminal :

```
./pip uninstall <package-name>
```

## <a name="next-steps"></a>Étapes suivantes

Pour savoir comment utiliser un bloc-notes existant, consultez [comment gérer des ordinateurs portables dans Azure Data Studio](notebooks-how-to-manage.md).