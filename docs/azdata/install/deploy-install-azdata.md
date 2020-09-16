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
ms.openlocfilehash: 408dec76480a36ff2280926147b948859fa7088d
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733896"
---
# <a name="install-azdata"></a>Installer `azdata`

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

`azdata` est un utilitaire en ligne de commande écrit en Python qui permet de démarrer et de gérer les clusters Big Data via des API REST. 

## <a name="find-latest-version"></a>Trouver la version la plus récente

La liste des fichiers de la dernière version est toujours disponible sur [https://aka.ms/azdata](https://aka.ms/azdata).

Pour connaître la version que vous avez installée et savoir si elle nécessite d’être mise à jour, exécutez `azdata --version`.

## <a name="os-specific-instructions"></a>Instructions spécifiques au système d’exploitation

* [Installer sur Windows](../install/deploy-install-azdata-installer.md)
* [Installer sur macOS](../install/deploy-install-azdata-macos.md)
* Installer sur Linux ou le [Sous-système Windows pour Linux (WSL)](/windows/wsl/about/)
   * [Installer avec apt sur Debian ou Ubuntu](../install/deploy-install-azdata-linux-package.md)
   * [Installer avec yum sur RHEL ou CentOS](../install/deploy-install-azdata-yum.md)
   * [Installer avec Zypper sur openSUSE ou SLE](../install/deploy-install-azdata-zypper.md)
   * [Installer à partir du script](../install/deploy-install-azdata-pip.md)

[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)] ?](../../big-data-cluster/big-data-cluster-overview.md).
