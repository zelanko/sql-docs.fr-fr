---
title: Installer azdata
titleSuffix: SQL Server big data clusters
description: Découvrez comment installer l’outil azdata pour installer et gérer des clusters Big Data.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 40338c4083241fedd113bca3a1beb839dbdd3fca
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75721700"
---
# <a name="install-azdata"></a>Installer `azdata`

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

`azdata` est un utilitaire en ligne de commande écrit en Python qui permet de démarrer et de gérer les clusters Big Data via des API REST. 

## <a name="find-latest-version"></a>Trouver la version la plus récente

La liste des fichiers de la dernière version est toujours disponible sur [https://aka.ms/azdata](https://aka.ms/azdata).

Pour connaître la version que vous avez installée et savoir si elle nécessite d’être mise à jour, exécutez `azdata --version`.

## <a name="os-specific-instructions"></a>Instructions spécifiques au système d’exploitation

* [Installer sur Windows](deploy-install-azdata-installer.md)
* [Installer sur macOS](deploy-install-azdata-macos.md)
* Installer sur Linux ou le [Sous-système Windows pour Linux (WSL)](/windows/wsl/about/)
   * [Installer avec apt sur Debian ou Ubuntu](deploy-install-azdata-linux-package.md)
   * [Installer avec yum sur RHEL ou CentOS](deploy-install-azdata-yum.md)
   * [Installer avec Zypper sur openSUSE ou SLE](deploy-install-azdata-zypper.md)
   * [Installer à partir du script](deploy-install-azdata-pip.md)

[!INCLUDE [azdata-package-installation-remove-pip-install](../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] ?](big-data-cluster-overview.md).
