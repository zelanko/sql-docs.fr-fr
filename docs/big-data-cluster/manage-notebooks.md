---
title: Gérer un cluster Big Data SQL Server avec des notebooks Azure Data Studio
titleSuffix: Manage SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Utilisez un notebook d’Azure Data Studio pour gérer et dépanner un cluster Big Data.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 09/09/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cb2fcaf7431b5d79698af009b533ee49254777fe
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70846649"
---
# <a name="manage-big-data-clusters-for-sql-server-with-azure-data-studio-notebooks"></a>Gérer des clusters Big Data pour SQL Server avec des notebooks Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] fournit une extension pour Azure Data Studio qui inclut des notebooks. Un notebook comprend la documentation et le code que vous pouvez utiliser dans Azure Data Studio pour gérer des clusters Big Data pour SQL Server.

Initialement implémentés en tant que projet open source, les [notebooks](notebooks-guidance.md) ont été implémentés dans [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download). Vous pouvez utiliser un marquage Markdown pour le texte des cellules de texte et un des noyaux disponibles pour écrire du code dans les cellules de code.

Vous pouvez utiliser des notebooks pour déployer des clusters Big Data pour [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

Outre les blocs-notes, les utilisateurs peuvent afficher un ensemble de blocs-notes, appelés livres Jupyter. Un book Jupyter fournit une table des matières pour naviguer dans une collection de notebooks et permettre à l’utilisateur de trouver facilement le notebook dont il a besoin, s’il faut dépanner SQL Server ou voir l’état du cluster.

## <a name="prerequisites"></a>Prérequis

Les prérequis suivants sont nécessaires pour pouvoir lancer le notebook :

* Version la plus récente de la [build Azure Data Studio Insiders](https://aka.ms/azuredatastudio-rc)
* Extension [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] installée dans Azure Data Studio

En plus de ce qui précède, le déploiement d’un cluster Big Data SQL Server 2019 nécessite également :

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="accessing-troubleshooting-notebooks"></a>Accès aux notebooks de dépannage
Il existe trois façons d’accéder aux blocs-notes de dépannage.

### <a name="command-palette"></a>Palette de commandes
1. Cliquez sur **Afficher** , puis sur **palette de commandes**
2. Tapez «Jupyter Books : SQL Server Guide de 2019»
3. Cette opération ouvre les Jupyter Books Viewlet avec le livre Jupyter contenant les données du TSG relatives à SQL Server Clusters Big Data.

### <a name="sql-master-dashboard"></a>Tableau de bord SQL principal
1. Après l’installation d’Azure Data Studio Insiders, connectez-vous à une instance de cluster Big Data SQL Server.
2. Une fois la connexion établie, cliquez avec le bouton droit sur le nom de votre serveur dans la viewlet Connexions, puis cliquez sur **Gérer**.
3. Dans le tableau de bord, cliquez sur **Cluster Big Data SQL Server**. Cliquez sur **Guide SQL Server 2019** pour ouvrir le book Jupyter avec les notebooks dont vous avez besoin.
    ![button](media/manage-notebooks/jupyter-book-button.png)

1. Cette opération ouvre le Jupyter Books Viewlet avec le livre TSG Jupyter déjà ouvert.
4. Cliquez sur le notebook pour la tâche que vous devez effectuer.

### <a name="controller-dashboard"></a>Tableau de bord du contrôleur
1. Dans la vue **connexions** , développez **SQL Server Clusters Big Data.**
2. Ajoutez les détails du point de terminaison du contrôleur.
3. Une fois la connexion au contrôleur terminée, cliquez avec le bouton droit sur le point de terminaison, puis cliquez sur **gérer.**
4. Après le chargement du tableau de bord, cliquez sur dépanner pour lancer le Jupyter Book TSG.

## <a name="how-to-use-troubleshooting-notebooks"></a>Comment utiliser les blocs-notes de résolution des problèmes
1. Examinez la table des matières du livre Jupyter existante jusqu’à ce que vous trouviez le TSG dont vous avez besoin.
1. Tous les blocs-notes sont optimisés là où l’utilisateur doit cliquer uniquement sur **exécuter les cellules.** Cette opération exécute chaque cellule du bloc-notes individuellement jusqu’à ce qu’elle soit terminée.
1. Si vous rencontrez une erreur, le livre Jupyter suggère un bloc-notes que vous pouvez exécuter pour corriger l’erreur. Suivez les étapes, puis réexécutez le bloc-notes.

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur l’utilisation des notebooks dans Azure Data Studio, consultez [Guide pratique pour utiliser des notebooks dans SQL Server 2019 (préversion)](notebooks-guidance.md).
