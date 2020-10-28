---
title: Installer Azure Data CLI (azdata)
titleSuffix: ''
description: Découvrez comment installer l’outil azdata (Azure Data CLI).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 82aa3a2795328804a10a76e9ecd8af80f3bf7152
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257399"
---
# <a name="install-azure-data-cli-azdata"></a>Installer [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]

[!INCLUDE[azdata](../../includes/applies-to-version/azdata.md)]

[!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)] est un utilitaire en ligne de commande écrit en Python qui permet de démarrer et de gérer les services de données via des API REST. 

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

Utiliser azdata avec les clusters Big Data, consultez [Présentation des [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]](../../big-data-cluster/big-data-cluster-overview.md).

Utiliser azdata avec les [services de données dotés d’Azure Arc](/azure/azure-arc/data/)
