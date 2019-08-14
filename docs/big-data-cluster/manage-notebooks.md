---
title: Gérer un cluster Big Data SQL Server avec des notebooks Azure Data Studio
titleSuffix: Manage SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Utilisez un notebook d’Azure Data Studio pour gérer et dépanner un cluster Big Data.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1a6156dad127ea2a86e8a6f4dfbdd6f692fd8f6e
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893652"
---
# <a name="manage-big-data-clusters-for-sql-server-with-azure-data-studio-notebooks"></a>Gérer des clusters Big Data pour SQL Server avec des notebooks Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] fournit une extension pour Azure Data Studio qui inclut des notebooks. Un notebook comprend la documentation et le code que vous pouvez utiliser dans Azure Data Studio pour gérer des clusters Big Data pour SQL Server.

Initialement implémentés en tant que projet open source, les [notebooks](notebooks-guidance.md) ont été implémentés dans [Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download). Vous pouvez utiliser un marquage Markdown pour le texte des cellules de texte et un des noyaux disponibles pour écrire du code dans les cellules de code.

Vous pouvez utiliser des notebooks pour déployer des clusters Big Data pour [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

Outre les blocs-notes, les utilisateurs peuvent afficher un ensemble de blocs-notes, appelés livres Jupyter. Un book Jupyter fournit une table des matières pour naviguer dans une collection de notebooks et permettre à l’utilisateur de trouver facilement le notebook dont il a besoin, s’il faut dépanner SQL Server ou voir l’état du cluster.

## <a name="prerequisites"></a>Prérequis

Les prérequis suivants sont nécessaires pour pouvoir lancer le notebook :

* Version la plus récente de la [build Azure Data Studio Insiders](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master)
* Extension [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] installée dans Azure Data Studio

En plus de ce qui précède, le déploiement d’un cluster Big Data SQL Server 2019 nécessite également :

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="accessing-troubleshooting-notebooks"></a>Accès aux notebooks de dépannage

1. Après l’installation d’Azure Data Studio Insiders, connectez-vous à une instance de cluster Big Data SQL Server.
2. Une fois la connexion établie, cliquez avec le bouton droit sur le nom de votre serveur dans la viewlet Connexions, puis cliquez sur **Gérer**.
3. Dans le tableau de bord, cliquez sur **Cluster Big Data SQL Server**. Cliquez sur **Guide SQL Server 2019** pour ouvrir le book Jupyter avec les notebooks dont vous avez besoin.
    ![bouton](media/manage-notebooks/jupyter-book-button.png)

1. Dans la fenêtre du sélecteur de dossiers, choisissez un emplacement où enregistrer votre book Jupyter.
2. Cliquez sur **Recharger** pour recharger Azure Data Studio et voir votre book Jupyter. Cliquez sur **Ouvrir une nouvelle instance** pour ouvrir une nouvelle instance d’Azure Data Studio avec le book Jupyter.
3. Dans la vue Explorateur, vous devez voir une section appelée **Books**. Si elle n’est pas développée, cliquez dessus pour voir les notebooks.
4. Cliquez sur le notebook pour la tâche que vous devez effectuer.

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur l’utilisation des notebooks dans Azure Data Studio, consultez [Guide pratique pour utiliser des notebooks dans SQL Server 2019 (préversion)](notebooks-guidance.md).
