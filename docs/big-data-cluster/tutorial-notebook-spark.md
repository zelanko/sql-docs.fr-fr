---
title: Exécuter un exemple de notebook | Microsoft Docs
titleSuffix: SQL Server big data clusters
description: Ce didacticiel montre comment vous pouvez charger une exécution d’un exemple de notebook Spark sur un cluster de données volumineuses de SQL Server 2019 (version préliminaire).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 274f33590282f36454e6cdb6041dac3484b9bcc4
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860180"
---
# <a name="tutorial-run-a-sample-notebook-on-a-sql-server-big-data-cluster"></a>Tutoriel : Exécuter un exemple de notebook sur un cluster de données volumineuses de SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Ce didacticiel montre comment charger et exécuter un notebook dans Azure Data Studio sur un cluster de données volumineuses de SQL Server 2019 (version préliminaire). Ainsi, les scientifiques des données et les ingénieurs de données exécuter du code Python, R ou Scala sur le cluster.

> [!TIP]
> Si vous préférez, vous pouvez télécharger et exécuter un script pour les commandes de ce didacticiel. Pour obtenir des instructions, consultez le [Spark exemples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark) sur GitHub.

## <a id="prereqs"></a> Conditions préalables

- [Outils de données volumineuses](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Extension de SQL Server 2019**
- [Charger des exemples de données dans votre cluster de données volumineux](tutorial-load-sample-data.md)

## <a name="download-the-sample-notebook-file"></a>Télécharger l’exemple de fichier de bloc-notes

Utilisez les instructions suivantes pour charger l’exemple de fichier de bloc-notes **spark-sql.ipynb** dans Azure Data Studio.

1. Ouvrez une invite de commandes bash (Linux) ou de Windows PowerShell.

1. Accédez au répertoire où vous souhaitez télécharger l’exemple de fichier de bloc-notes pour.

1. Exécutez la commande suivante **curl** commande pour télécharger le fichier de bloc-notes à partir de GitHub :

   ```bash
   curl 'https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/spark-sql.ipynb' -o spark-sql.ipynb
   ```

## <a name="open-the-notebook"></a>Ouvrir le bloc-notes

Les étapes suivantes montrent comment ouvrir le fichier de bloc-notes dans Azure Data Studio :

1. Dans Azure Data Studio, connectez-vous à la passerelle HDFS/Spark de votre cluster big data. Pour plus d’informations, consultez [se connecter à la passerelle HDFS/Spark](connect-to-big-data-cluster.md#hdfs).

1. Double-cliquez sur la connexion de passerelle HDFS/Spark dans le **serveurs** fenêtre. Puis sélectionnez **ouvrir le bloc-notes**.

   ![Ouvrir le bloc-notes](media/tutorial-notebook-spark/azure-data-studio-open-notebook.png)

1. Attendez que le **noyau** et le contexte cible (**attacher à**) à remplir. Définir le **noyau** à **PySpark3**et définissez **attacher à** à l’adresse IP de votre point de terminaison de cluster de données volumineuses.

   ![Définir le noyau et l’attacher à](media/tutorial-notebook-spark/set-kernel-and-attach-to.png)

## <a name="run-the-notebook-cells"></a>Exécution des cellules de bloc-notes

Vous pouvez exécuter chaque cellule du bloc-notes en appuyant sur le bouton de lecture vers la gauche de la cellule. Les résultats sont affichés dans le bloc-notes après la fin de la cellule.

![Exécution de cellule du bloc-notes](media/tutorial-notebook-spark/run-notebook-cell.png)

Exécuter chacune des cellules dans l’exemple de notebook successivement. Pour plus d’informations sur l’utilisation de blocs-notes avec les clusters de données volumineuses de SQL Server, consultez les ressources suivantes :

- [Comment utiliser des blocs-notes en version préliminaire de SQL Server 2019](notebooks-guidance.md)
- [Comment gérer des ordinateurs portables dans Azure Data Studio](notebooks-how-to-manage.md)

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur les ordinateurs portables :
> [!div class="nextstepaction"]
> [En savoir plus sur les ordinateurs portables](notebooks-guidance.md)