---
title: Gérer SQL Server Cluster Big Data avec des blocs-notes Azure Data Studio
titleSuffix: Manage SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Utilisez un bloc-notes à partir de Azure Data Studio pour gérer et dépanner un cluster Big Data.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8d87b09878539cccd40191d870bf97487579dca2
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426399"
---
# <a name="manage-big-data-clusters-for-sql-server-with-azure-data-studio-notebooks"></a>Gérer des clusters Big Data pour SQL Server avec des blocs-notes Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]fournit une extension pour Azure Data Studio qui inclut des blocs-notes de déploiement. Un bloc-notes de déploiement comprend la documentation et le code que vous pouvez utiliser dans Azure Data Studio pour gérer les clusters Big Data pour SQL Server.

Initialement implémentée en tant que projet open source, les [blocs-notes](notebooks-guidance.md) ont été implémentés dans [Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download). Vous pouvez utiliser la démarque pour le texte des cellules de texte et l’un des noyaux disponibles pour écrire du code dans les cellules du code.

Vous pouvez utiliser des blocs-notes pour déployer des clusters Big Data pour [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

## <a name="prerequisites"></a>Prérequis

Les conditions préalables suivantes sont requises pour pouvoir lancer le bloc-notes:

* Version la plus récente de [Azure Data Studio builds](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master) Insider
* [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]extension installée dans Azure Data Studio

En plus de ce qui précède, le déploiement de SQL Server 2019 Big Data cluster nécessite également:

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Interface de ligne de commande Azure](/cli/azure/install-azure-cli)
