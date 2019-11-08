---
title: Installer azdata à l’aide du programme d’installation sur Linux
titleSuffix: SQL Server big data clusters
description: Découvrez comment installer l’outil azdata permettant d’installer et de gérer des clusters Big Data SQL Server, à l’aide du programme d’installation (Linux).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9d8d4a34e89de7c136e1e80b43929531a2d10eba
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532073"
---
# <a name="install-azdata-to-manage-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-on-linux"></a>Installer `azdata` pour gérer les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] sur Linux

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment installer `azdata` pour les clusters Big Data SQL Server 2019 sur Linux. Avant que ces gestionnaires de package soient disponibles, l’installation de `azdata` nécessitait `pip`.

Les gestionnaires de package sont conçus pour différents systèmes d’exploitation et distributions.

- Pour Windows et Linux (distribution Ubuntu), vous pouvez effectuer l’installation avec un [gestionnaire de package](./deploy-install-azdata-installer.md) pour bénéficier d’une expérience plus simple.
- Pour Linux (Ubuntu), [installez `azdata` avec `apt`](#azdata-apt).

Actuellement, il n’existe aucun gestionnaire de package permettant d’installer `azdata` sur d’autres systèmes d’exploitation ou distributions. Pour ces plateformes, consultez [Installer `azdata` sans gestionnaire de package](./deploy-install-azdata.md).

## <a id="linux"></a>Installer `azdata` pour Linux

Le package d’installation `azdata` est disponible pour Ubuntu avec `apt`.

### <a id="azdata-apt"></a>Installer `azdata` avec apt (Ubuntu)

>[!NOTE]
>Le package `azdata` n’utilise pas l’interpréteur Python du système, mais installe son propre interpréteur Python.

1. Obtenez les packages nécessaires pour le processus d’installation :

    ```bash
    sudo apt-get update
    sudo apt-get install gnupg ca-certificates curl apt-transport-https lsb-release -y
    ```

2. Téléchargez et installez la clé de signature :

    ```bash
    wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```

3. Ajoutez les informations sur le référentiel `azdata` :

    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2019.list)"
    ```

4. Mettez à jour les informations de référentiel et installez `azdata` :

    ```bash
    sudo apt-get update
    sudo apt-get install -y azdata-cli
    ```

5. Vérifiez l’installation :

    ```bash
    azdata --version
    ```

### <a name="update"></a>Update

Mettez à niveau `azdata` uniquement :

```bash
sudo apt-get update && sudo apt-get install --only-upgrade -y azdata-cli
```

### <a name="uninstall"></a>Désinstaller

1. Désinstallez avec apt-get remove :

    ```bash
    sudo apt-get remove -y azdata-cli
    ```

2. Supprimez les informations de référentiel `azdata` :

    >[!NOTE]
    >Cette étape n’est pas nécessaire si vous envisagez d’installer `azdata` à l’avenir

    ```bash
    sudo rm /etc/apt/sources.list.d/azdata-cli.list
    ```

3. Supprimez la clé de signature :

    ```bash
    sudo rm /etc/apt/trusted.gpg.d/dpgswdist.v1.asc.gpg
    ```

4. Supprimez toutes les dépendances inutiles qui ont été installées avec l’interface de ligne de commande Azdata :

    ```bash
    sudo apt autoremove
    ```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] ?](big-data-cluster-overview.md).
