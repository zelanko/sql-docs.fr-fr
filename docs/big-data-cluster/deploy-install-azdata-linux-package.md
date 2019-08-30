---
title: Installer azdata avec le programme d’installation sur Linux
titleSuffix: SQL Server big data clusters
description: Découvrez comment installer l’outil azdata pour installer et gérer [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (version préliminaire) avec le programme d’installation (Linux).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e11e4851294ac8ffd8efa66e2156dcd47bce3aa0
ms.sourcegitcommit: 71fac5fee00e0eca57e555f44274dd7e08d47e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160683"
---
# <a name="install-azdata-to-manage-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-on-linux"></a>Installer `azdata` pour gérer [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] sur Linux

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment installer `azdata` pour les clusters de SQL Server 2019 Big Data dans la version Release Candidate sur Linux. Pour que ces gestionnaires de packages soient disponibles, l' `azdata` installation `pip`de est obligatoire.

Les gestionnaires de packages sont conçus pour différents systèmes d’exploitation et distributions.

- Pour Linux (Ubuntu), [installez `azdata` avec `apt` ](#azdata-apt)

À ce stade, il n’y a aucun gestionnaire de `azdata` package à installer sur d’autres systèmes d’exploitation ou distributions. Pour ces plateformes, [consultez `azdata` installation sans le gestionnaire de package](./deploy-install-azdata.md).

## <a id="linux"></a>Installer `azdata` pour Linux

`azdata`le package d’installation est disponible pour `apt`Ubuntu avec.

### <a id="azdata-apt"></a>Installer `azdata` avec apt (Ubuntu)

>[!NOTE]
>Le `azdata` package n’utilise pas le système Python, mais installe son propre interpréteur Python.

1. Obtenir les packages nécessaires pour le processus d’installation:

    ```bash
    sudo apt-get update
    sudo apt-get install gnupg ca-certificates curl apt-transport-https lsb-release -y
    ```

2. Téléchargez et installez la clé de signature:

    ```bash
    wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add –
    ```

3. Ajoutez les `azdata` informations relatives au référentiel:

    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"
    ```

4. Mettre à jour les informations de référentiel `azdata`et installer:

    ```bash
    sudo apt-get update
    sudo apt-get install -y azdata-cli
    ```

5. Vérifier l’installation:

    ```bash
    azdata --version
    ```

### <a name="update"></a>Mettre à jour

Mise `azdata` à niveau uniquement:

```bash
sudo apt-get update && sudo apt-get install --only-upgrade -y azdata-cli
```

### <a name="uninstall"></a>Désinstaller l’interface

1. Désinstaller avec apt-recevoir supprimer:

    ```bash
    sudo apt-get remove -y azdata-cli
    ```

2. Supprimez `azdata` les informations de référentiel:

    >[!NOTE]
    >Cette étape n’est pas nécessaire si vous prévoyez d' `azdata` installer à l’avenir

    ```bash
    sudo rm /etc/apt/sources.list.d/azdata-cli.list
    ```

3. Supprimez la clé de signature:

    ```bash
    sudo rm /etc/apt/trusted.gpg.d/dpgswdist.v1.asc.gpg
    ```

4. Supprimez toutes les dépendances inutiles qui ont été installées avec azdata CLI:

    ```bash
    sudo apt autoremove
    ```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [ [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]que sont?](big-data-cluster-overview.md).
