---
title: 'Gérer : Notebooks Azure Data Studio'
titleSuffix: SQL Server Big Data Clusters
description: Utilisez un notebook d’Azure Data Studio pour gérer et dépanner un cluster Big Data.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d2a051e297b48ed8d813fce0e0e8ffa748a84d16
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75252015"
---
# <a name="manage-sql-server-big-data-clusters-with-azure-data-studio-notebooks"></a>Gérer des clusters Big Data SQL Server avec des notebooks Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] fournit une extension pour Azure Data Studio qui inclut des notebooks. Un notebook fournit de la documentation et du code que vous pouvez utiliser dans Azure Data Studio pour gérer des clusters Big Data SQL Server 2019.

Initialement implémentés en tant que projet open source, les [notebooks](notebooks-guidance.md) ont été incorporés dans [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download). Vous pouvez utiliser un marquage Markdown pour le texte des cellules de texte et un des noyaux disponibles pour écrire du code dans les cellules de code.

Vous pouvez utiliser des notebooks pour déployer des clusters Big Data pour [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

En plus des notebooks, vous pouvez voir une collection de notebooks, qui est appelée « book Jupyter ». Un book Jupyter fournit une table des matières pour vous aider à naviguer dans une collection de notebooks : vous pouvez ainsi trouver facilement le notebook dont vous avez besoin si vous voulez résoudre un problème SQL Server ou voir l’état du cluster.

## <a name="prerequisites"></a>Conditions préalables requises

Vous avez besoin de ces prérequis pour ouvrir un notebook :

* La version la plus récente de la [build Azure Data Studio Insiders](https://aka.ms/azuredatastudio-rc)
* L’extension [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] installée dans Azure Data Studio

En plus de ces prérequis, pour déployer des clusters Big Data SQL Server 2019, vous avez aussi besoin de :

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="access-troubleshooting-notebooks"></a>Accéder aux notebooks de résolution des problèmes
Il existe trois façons d’accéder aux notebooks de résolution des problèmes.

### <a name="command-palette"></a>Palette de commandes
1. Sélectionnez **Afficher** > **Palette de commandes**.
2. Entrez **Books Jupyter : Guide SQL Server 2019**.

La viewlet Jupyter Books avec le book Jupyter qui contient les notebooks de résolution des problèmes liés à des clusters Big Data SQL Server s’ouvre.

### <a name="sql-master-dashboard"></a>Tableau de bord principal SQL
1. Après avoir installé Azure Data Studio Insiders, connectez-vous à une instance de cluster Big Data SQL Server.
2. Une fois que vous êtes connecté à l’instance, cliquez avec le bouton droit sur le nom de votre serveur, sous **CONNEXIONS** et sélectionnez **Gérer**.
3. Dans le tableau de bord, sélectionnez **Cluster Big Data SQL Server**. Sélectionnez **Guide SQL Server 2019** pour ouvrir le book Jupyter contenant les notebooks dont vous avez besoin.
    ![Notebooks Jupyter dans le tableau de bord](media/manage-notebooks/jupyter-book-button.png)

1. Sélectionnez le notebook pour la tâche que vous devez effectuer.

### <a name="controller-dashboard"></a>Tableau de bord du contrôleur
1. Dans la vue **Connexions**, développez **Clusters Big Data SQL Server**.
2. Ajoutez les informations du point de terminaison du contrôleur.
3. Une fois que vous êtes connecté au contrôleur, cliquez avec le bouton droit sur le point de terminaison, puis sélectionnez **Gérer**.
4. Une fois le tableau de bord chargé, sélectionnez **résoudre les problèmes** pour ouvrir les guides de résolution des problèmes du book Jupyter.

## <a name="use-troubleshooting-notebooks"></a>Utiliser les notebooks de résolution des problèmes
1. Recherchez le guide de résolution des problèmes dont vous avez besoin dans la table des matières du book Jupyter.
1. Les notebooks étant optimisés, vous devez simplement sélectionner **Run Cells** (Exécuter les cellules). Cette action exécute chaque cellule du notebook individuellement jusqu’à ce que le notebook soit terminé.
1. Si une erreur est détectée, le book Jupyter suggère un notebook que vous pouvez exécuter pour corriger l’erreur. Suivez les étapes recommandées, puis réexécutez le notebook.

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur les notebooks dans Azure Data Studio, consultez [Guide pratique pour utiliser des notebooks dans SQL Server](notebooks-guidance.md).
