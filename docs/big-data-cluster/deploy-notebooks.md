---
title: Déployer SQL Server Cluster Big Data avec des blocs-notes Azure Data Studio
titleSuffix: Deploy SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Utilisez un bloc-notes à partir de Azure Data Studio pour déployer un cluster Big Data.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f12a4f06ceb1c3a48b2b2fc661c59594e6d6cce3
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426419"
---
# <a name="deploy-sql-server-big-data-cluster-with-azure-data-studio-notebooks"></a>Déployer SQL Server Cluster Big Data avec des blocs-notes Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]fournit une extension pour Azure Data Studio qui inclut des blocs-notes de déploiement. Un bloc-notes de déploiement comprend la documentation et le code que vous pouvez utiliser dans Azure Data Studio pour créer un cluster SQL Server Big Data. 

Initialement implémentée en tant que projet open source, les [blocs-notes](notebooks-guidance.md) ont été implémentés dans [Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download). Vous pouvez utiliser la démarque pour le texte des cellules de texte et l’un des noyaux disponibles pour écrire du code dans les cellules du code.

Vous pouvez utiliser des blocs-notes pour déployer des clusters Big Data pour [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

## <a name="prerequisites"></a>Prérequis
Les conditions préalables suivantes sont requises pour pouvoir lancer le bloc-notes:

* Dernière version de [Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download) installée
* [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]extension installée dans Azure Data Studio

En plus de ce qui précède, le déploiement de SQL Server 2019 Big Data cluster nécessite également:

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Interface de ligne de commande Azure](/cli/azure/install-azure-cli)

## <a name="launch-the-notebook"></a>Lancer le bloc-notes

1. Installez et lancez la [Build insiders Azure Data Studio](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master).
1.  Sous l’onglet **connexions** , cliquez sur **...** , puis sélectionnez **déployer SQL Server Cluster Big Data...** .

   ![IA et ML](media/deploy-notebooks/deploy-notebooks-1.png)

1. À partir de la **cible déploiement**, sous **options**, sélectionnez **nouveau cluster Azure Kubernetes** ou **cluster Azure Kubernetes service existant**.
1. Sélectionnez **ouvrir le bloc-notes**.

Cette action lance le bloc-notes approprié. Pour terminer le déploiement, suivez les instructions du Notebook pour déployer un cluster Big Data pour [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] sur un cluster Azure Kubernetes service existant ou nouveau.
