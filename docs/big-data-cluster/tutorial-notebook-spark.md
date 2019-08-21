---
title: Exécuter un exemple de notebook | Microsoft Docs
titleSuffix: SQL Server big data clusters
description: Ce didacticiel vous montre comment charger un exemple de bloc-notes Spark sur un [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 18e182a251e0f93127ffc376648a29c3e2d9cd02
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653268"
---
# <a name="tutorial-run-a-sample-notebook-on-a-sql-server-big-data-cluster"></a>Tutoriel : Exécuter un exemple de notebook sur un cluster Big Data SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Ce didacticiel montre comment charger et exécuter un bloc-notes dans Azure Data Studio sur [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]un. Cela permet aux scientifiques des données et aux ingénieurs de données d’exécuter du code Python, R ou Scala sur le cluster.

> [!TIP]
> Si vous préférez, vous pouvez télécharger et exécuter un script pour les commandes de ce tutoriel. Pour obtenir des instructions, consultez les [exemples Spark](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark) sur GitHub.

## <a id="prereqs"></a> Conditions préalables

- [Outils Big Data](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Extension SQL Server 2019**
- [Charger des exemples de données dans votre cluster Big Data](tutorial-load-sample-data.md)

## <a name="download-the-sample-notebook-file"></a>Télécharger l’exemple de fichier de notebook

Utilisez les instructions suivantes pour charger l’exemple de fichier de notebook **spark-sql.ipynb** dans Azure Data Studio.

1. Ouvrez une invite de commandes bash (Linux) ou Windows PowerShell.

1. Accédez au répertoire dans lequel vous souhaitez télécharger l’exemple de fichier de notebook.

1. Exécutez la commande **curl** suivante pour télécharger le fichier de notebook à partir de GitHub :

   ```bash
   curl 'https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/data-loading/transform-csv-files.ipynb' -o transform-csv-files.ipynb
   ```

## <a name="open-the-notebook"></a>Ouvrir le notebook

Les étapes suivantes montrent comment ouvrir le fichier de notebook dans Azure Data Studio :

1. Dans Azure Data Studio, connectez-vous à l’instance maître de votre cluster Big Data. Pour plus d’informations, consultez [Se connecter à un cluster Big Data](connect-to-big-data-cluster.md).

1. Double-cliquez sur la connexion de passerelle HDFS/Spark dans la fenêtre **Serveurs**. Sélectionnez ensuite **Open Notebook** (Ouvrir un notebook).

   ![Ouvrir un notebook](media/tutorial-notebook-spark/azure-data-studio-open-notebook.png)

1. Attendez que **Noyau** et le contexte cible (**Attacher à**) soient remplis. Affectez à **Noyau** la valeur **PySpark3** et à **Attacher à** l’adresse IP de votre point de terminaison de cluster Big Data.

   ![Définir Noyau et Attacher à](media/tutorial-notebook-spark/set-kernel-and-attach-to.png)

## <a name="run-the-notebook-cells"></a>Exécuter les cellules de notebook

Vous pouvez exécuter chaque cellule de notebook en appuyant sur le bouton de lecture situé à gauche de la cellule. Les résultats sont affichés dans le notebook après la fin de l’exécution de la cellule.

![Exécuter la cellule de notebook](media/tutorial-notebook-spark/run-notebook-cell.png)

Exécutez chaque cellule de l’exemple de notebook l’une après l’autre. Pour plus d’informations sur l’utilisation des [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]blocs-notes avec, consultez les ressources suivantes:

- [Guide pratique pour utiliser des notebooks dans la préversion de SQL Server 2019](notebooks-guidance.md)
- [Comment gérer des notebooks dans Azure Data Studio](notebooks-how-to-manage.md)

## <a name="next-steps"></a>Étapes suivantes

Découvrez-en plus sur les notebooks :
> [!div class="nextstepaction"]
> [En savoir plus sur les notebooks](notebooks-guidance.md)
