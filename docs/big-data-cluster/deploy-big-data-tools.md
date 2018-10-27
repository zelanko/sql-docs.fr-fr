---
title: Se connecter à SQL Server cluster big data avec Azure Data Studio | Microsoft Docs
description: Découvrez comment vous connecter à un cluster de données volumineuses de SQL Server 2019 avec Azure Data Studio.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/05/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 18df937cfed15d7302a58267eb392a1933d73052
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49643787"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Se connecter à un cluster SQL Server de données volumineux avec Azure Data Studio

Cet article décrit comment installer Azure Data Studio, l’extension de SQL Server 2019 (version préliminaire) et ensuite vous connecter à un cluster de données volumineux. La nouvelle extension de SQL Server 2019 inclut la prise en charge de la version préliminaire de [clusters de données volumineuses de SQL Server 2019](big-data-cluster-overview.md), intégré [expérience de bloc-notes](notebooks-guidance.md)et un PolyBase [Assistant Create External Table](../relational-databases/polybase/data-virtualization.md?toc=%2fsql%2fbig-data-cluster%2ftoc.json).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="install-azure-data-studio"></a>Installer Azure Data Studio

Pour installer Azure Data Studio, consultez [télécharger et installer la dernière version d’Azure Data Studio](../azure-data-studio/download.md).

## <a name="install-the-sql-server-2019-extension-preview"></a>Installer l’extension de SQL Server 2019 (version préliminaire)

Pour installer l’extension, consultez [installer l’extension de SQL Server 2019 (version préliminaire)](../azure-data-studio/sql-server-2019-extension.md).

## <a name="connect-to-the-cluster"></a>Connectez-vous au cluster

Lorsque vous vous connectez à un cluster de données volumineux, vous pouvez vous connecter à SQL Server [instance principale](concept-master-instance.md) ou à la passerelle HDFS/Spark. Les sections suivantes montrent comment se connecter à chacun.

## <a id="master"></a> Instance principale

1. Dans Azure Data Studio, appuyez sur **F1** > **nouvelle connexion**.

1. Dans **type de connexion**, sélectionnez **Microsoft SQL Server**.

1. Tapez l’adresse IP de l’instance principale de SQL Server dans **nom du serveur** (par exemple :  **\<adresse IP\>, 31433**).

1. Entrez un nom de connexion SQL **nom d’utilisateur** et **mot de passe**.

1. Modifier le **nom de la base de données** à la **high_value_data** base de données.

   ![Se connecter à l’instance principale](./media/deploy-big-data-tools/connect-to-cluster.png)

1. Appuyez sur **Connect**et le **tableau de bord Server** doit apparaître.

## <a id="hdfs"></a> Passerelle HDFS/Spark

1. Dans Azure Data Studio, appuyez sur **F1** > **nouvelle connexion**.

1. Dans **type de connexion**, sélectionnez **cluster de données volumineux de SQL Server**.

1. Tapez l’adresse IP du cluster big data dans **nom du serveur**.

1. Entrez `root` pour le **utilisateur** et spécifiez le **mot de passe** à votre cluster big data.

   ![Se connecter à HDFS/Spark passerelle](./media/deploy-big-data-tools/connect-to-cluster-hdfs-spark.png)

1. Appuyez sur **Connect**et le **tableau de bord Server** doit apparaître.

## <a name="next-steps"></a>Étapes suivantes

Pour exécuter les blocs-notes dans Azure Data Studio, consultez [comment utiliser des blocs-notes en version préliminaire de SQL Server 2019](notebooks-guidance.md).
