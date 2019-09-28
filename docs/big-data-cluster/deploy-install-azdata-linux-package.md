---
title: Installer azdata avec le programme d’installation sur Linux
titleSuffix: SQL Server big data clusters
description: Découvrez comment installer l’outil azdata pour l’installation et la gestion de [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (version préliminaire) avec le programme d’installation (Linux).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2795178cb975ecb620528c4a5dc8715b70d447fd
ms.sourcegitcommit: c4875c097e3aae1b76233777d15e0a0ec8e0d681
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71342007"
---
# <a name="install-azdata-to-manage-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-on-linux"></a>Installer `azdata` pour gérer [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] sur Linux

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment installer `azdata` pour les clusters Big Data SQL Server 2019 version Release Candidate sur Linux. Avant que ces gestionnaires de packages ne soient disponibles, l’installation de `azdata` nécessitait `pip`.

Les gestionnaires de packages sont conçus pour différents systèmes d’exploitation et distributions.

- Pour Linux (Ubuntu), [installez `azdata` avec `apt`](#azdata-apt)

À ce stade, il n’y a aucun gestionnaire de package à installer `azdata` sur d’autres systèmes d’exploitation ou distributions. Pour ces plateformes, consultez [installer `azdata` sans le gestionnaire de package](./deploy-install-azdata.md).

## <a id="linux"></a>Installer `azdata` pour Linux

`azdata` package d’installation est disponible pour Ubuntu avec `apt`.

### <a id="azdata-apt"></a>Installer `azdata` avec apt (Ubuntu)

>[!NOTE]
>Le package `azdata` n’utilise pas le système Python, mais installe son propre interpréteur Python.

1. Obtenir les packages nécessaires pour le processus d’installation :

    ```bash
    sudo apt-get update
    sudo apt-get install gnupg ca-certificates curl apt-transport-https lsb-release -y
    ```

2. Téléchargez et installez la clé de signature :

    ```bash
    wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```

3. Ajoutez les informations de référentiel `azdata` :

    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"
    ```

4. Mettre à jour les informations de référentiel et installer `azdata` :

    ```bash
    sudo apt-get update
    sudo apt-get install -y azdata-cli
    ```

5. Vérifier l’installation :

    ```bash
    azdata --version
    ```

### <a name="update"></a>Update

Mettre à niveau `azdata` uniquement :

```bash
sudo apt-get update && sudo apt-get install --only-upgrade -y azdata-cli
```

### <a name="uninstall"></a>Désinstaller l’interface

1. Désinstaller avec apt-recevoir supprimer :

    ```bash
    sudo apt-get remove -y azdata-cli
    ```

2. Supprimez les informations de référentiel `azdata` :

    >[!NOTE]
    >Cette étape n’est pas nécessaire si vous prévoyez d’installer `azdata` à l’avenir.

    ```bash
    sudo rm /etc/apt/sources.list.d/azdata-cli.list
    ```

3. Supprimez la clé de signature :

    ```bash
    sudo rm /etc/apt/trusted.gpg.d/dpgswdist.v1.asc.gpg
    ```

4. Supprimez toutes les dépendances inutiles qui ont été installées avec azdata CLI :

    ```bash
    sudo apt autoremove
    ```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, voir [qu’est-ce que [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] ?](big-data-cluster-overview.md).
