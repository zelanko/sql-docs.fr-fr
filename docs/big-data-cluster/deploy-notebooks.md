---
title: Déployer un cluster Big Data SQL Server avec des notebooks Azure Data Studio
titleSuffix: Deploy SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Utilisez un notebook d’Azure Data Studio pour déployer un cluster Big Data.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: fb1da50fb84cbfd44aeab50a00be1c8433b3041e
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892457"
---
# <a name="deploy-sql-server-big-data-cluster-with-azure-data-studio-notebooks"></a>Déployer un cluster Big Data SQL Server avec des notebooks Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] fournit une extension pour Azure Data Studio qui inclut des notebooks de déploiement. Un notebook de déploiement comprend la documentation et le code que vous pouvez utiliser dans Azure Data Studio pour créer un cluster Big Data SQL Server.

Initialement implémentés en tant que projet open source, les [notebooks](notebooks-guidance.md) ont été implémentés dans [Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download). Vous pouvez utiliser un marquage Markdown pour le texte des cellules de texte et un des noyaux disponibles pour écrire du code dans les cellules de code.

Vous pouvez utiliser des notebooks pour déployer des clusters Big Data pour [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

## <a name="prerequisites"></a>Prérequis

Les prérequis suivants sont nécessaires pour pouvoir lancer le notebook :

* Version la plus récente de [Azure Data Studio Build](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master) Insiders installée
* Extension [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] installée dans Azure Data Studio

En plus de ce qui précède, le déploiement d’un cluster Big Data SQL Server 2019 nécessite également :

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="launch-the-notebook"></a>Lancer le notebook

1. Lancez le Azure Data Studio Insider.

1. Sous l’onglet **Connections**, cliquez sur **...** et sélectionnez **Deploy SQL Server big data cluster...** (Déployer le cluster Big Data SQL Server).

   ![IA et ML](media/deploy-notebooks/deploy-notebooks-1.png)

1. À partir **Deployment Target** (Cible de déploiement), sous **Options**, sélectionnez **New Azure Kubernetes Cluster** (Nouveau cluster Azure Kubernetes) ou **Existing Azure Kubernetes Service cluster** (Cluster Azure Kubernetes Service existant).

1. Cliquez sur le bouton **Sélectionner** .

1. Cette action lance une boîte de dialogue pour collecter les entrées d’utilisateur, fournir les informations requises et passer en revue les valeurs par défaut.

1. Cliquez sur le bouton **ouvrir le bloc-notes** .
Cette action lance le notebook approprié. Pour terminer le déploiement, suivez les instructions du notebook afin de déployer un cluster Big Data pour [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] sur un cluster Azure Kubernetes Service existant ou nouveau.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur le déploiement, consultez [Guide de déploiement pour les clusters Big Data SQL Server](deployment-guidance.md).
