---
title: Gérer des clusters de SQL Server Big Data avec des blocs-notes Azure Data Studio
titleSuffix: Manage SQL Server Big Data Clusters with Azure Data Studio notebooks
description: Utilisez un notebook d’Azure Data Studio pour gérer et dépanner un cluster Big Data.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 09/09/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e22b16cf8658e53e6bdc5db0fcd82692f3730fc7
ms.sourcegitcommit: c7a202af70fd16467a498688d59637d7d0b3d1f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72313680"
---
# <a name="manage-sql-server-big-data-clusters-with-azure-data-studio-notebooks"></a>Gérer des clusters de SQL Server Big Data avec des blocs-notes Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] fournit une extension pour Azure Data Studio qui inclut des notebooks. Un bloc-notes fournit la documentation et le code que vous pouvez utiliser dans Azure Data Studio pour gérer les clusters Big Data SQL Server 2019.

Initialement implémentée en tant que projet open source, les [blocs-notes](notebooks-guidance.md) ont été incorporés dans [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download). Vous pouvez utiliser un marquage Markdown pour le texte des cellules de texte et un des noyaux disponibles pour écrire du code dans les cellules de code.

Vous pouvez utiliser des notebooks pour déployer des clusters Big Data pour [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

Outre les blocs-notes, vous pouvez afficher un ensemble de blocs-notes, appelé Jupyter. Un Jupyter Book fournit une table des matières pour vous aider à naviguer dans une collection de blocs-notes pour vous permettre de trouver facilement le bloc-notes dont vous avez besoin, si vous souhaitez dépanner SQL Server ou afficher l’état du cluster.

## <a name="prerequisites"></a>Prérequis

Vous avez besoin de ces conditions préalables pour ouvrir un bloc-notes :

* Version la plus récente de [Azure Data Studio builds Insider](https://aka.ms/azuredatastudio-rc)
* L’extension [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], installée dans Azure Data Studio

En plus de ces conditions préalables, vous avez également besoin de déployer des clusters Big Data SQL Server 2019 :

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="access-troubleshooting-notebooks"></a>Accéder aux blocs-notes de résolution des problèmes
Il existe trois façons d’accéder aux blocs-notes de dépannage.

### <a name="command-palette"></a>Palette de commandes
1. Sélectionnez **afficher** > **palette de commandes**.
2. Entrez @no__t 0Jupyter : SQL Server Guide de 2019 @ no__t-0.

Les livres Jupyter Viewlet avec le livre Jupyter qui contient les blocs-notes de résolution des problèmes liés à SQL Server Clusters Big Data s’ouvrent.

### <a name="sql-master-dashboard"></a>Tableau de bord SQL principal
1. Une fois que vous avez installé Azure Data Studio Insider, connectez-vous à une instance SQL Server Big Data.
2. Une fois que vous êtes connecté à l’instance, cliquez avec le bouton droit sur le nom de votre serveur sous **connexions** , puis sélectionnez **gérer**.
3. Dans le tableau de bord, sélectionnez **SQL Server Cluster Big Data**. Sélectionnez **SQL Server Guide de 2019** pour ouvrir le livre Jupyter contenant les blocs-notes dont vous avez besoin.
    blocs-notes @no__t 0Jupyter dans le tableau de bord @ no__t-1

1. Sélectionnez le bloc-notes pour la tâche que vous devez effectuer.

### <a name="controller-dashboard"></a>Tableau de bord du contrôleur
1. Dans la vue **connexions** , développez **SQL Server Clusters Big Data**.
2. Ajoutez les détails du point de terminaison du contrôleur.
3. Une fois que vous êtes connecté au contrôleur, cliquez avec le bouton droit sur le point de terminaison et sélectionnez **gérer**.
4. Une fois le tableau de bord chargé, sélectionnez **résoudre les problèmes** pour ouvrir les guides de dépannage du livre Jupyter.

## <a name="use-troubleshooting-notebooks"></a>Utiliser les blocs-notes de résolution des problèmes
1. Recherchez le Guide de résolution des problèmes dont vous avez besoin dans la table des matières du livre Jupyter.
1. Les blocs-notes étant optimisés, vous devez simplement sélectionner **exécuter les cellules**. Cette action exécute chaque cellule du bloc-notes individuellement jusqu’à ce que le bloc-notes soit terminé.
1. Si une erreur est détectée, le livre Jupyter suggère un bloc-notes que vous pouvez exécuter pour corriger l’erreur. Suivez les étapes recommandées, puis réexécutez le bloc-notes.

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur l’utilisation des notebooks dans Azure Data Studio, consultez [Guide pratique pour utiliser des notebooks dans SQL Server 2019 (préversion)](notebooks-guidance.md).
