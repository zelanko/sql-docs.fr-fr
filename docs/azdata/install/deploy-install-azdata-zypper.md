---
title: Installer azdata avec zypper
titleSuffix: ''
description: Découvrez comment installer l’outil azdata avec zypper.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 09/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ec87d5739e3707c056f7945a2c882eb00700464d
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725255"
---
# <a name="install-azdata-with-zypper"></a>Installer `azdata` avec zypper

[!INCLUDE[azdata](../../includes/applies-to-version/azdata.md)]

Pour les distributions Linux avec `zypper` il existe un package pour le `azdata-cli`. Le package CLI a été testé sur des versions Linux qui utilisent `zypper` :

- openSUSE 42.2 (intercalaire) +
- SLES 12 SP 2 +

[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-with-zypper"></a>Installer avec zypper

>[!IMPORTANT]
>Le package RPM de `azdata-cli` dépend du package python3. Sur votre système, il doit s’agir d’une version Python antérieure à l’exigence de *Python 3.6.x*. Si cela vous pose un problème, recherchez un remplacement au package python3 ou suivez les instructions d’installation manuelle qui utilisent [`pip`](../install/deploy-install-azdata-pip.md).

1. Installez les dépendances nécessaires pour installer `azdata-cli`.

   ```bash
   sudo zypper install -y curl
   ```

1. Importez la clé de référentiel Microsoft.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

1. Créez des informations de dépôt local.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo
   ```

1. Installez `azdata-cli`.

   ```bash
   sudo zypper install --from packages-microsoft-com-mssql-server-2019 -y azdata-cli
   ```

## <a name="verify-install"></a>Vérifier l’installation

```bash
azdata
azdata --version
```

## <a name="update"></a>Update

Mettez à jour le `azdata-cli` avec la commande `zypper update`.

```bash
sudo zypper refresh
sudo zypper update azdata-cli
```

## <a name="uninstall"></a>Désinstaller l’interface

Supprimez le package de votre système.

```bash
sudo zypper removerepo azdata-cli
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)] ?](../../big-data-cluster/big-data-cluster-overview.md).

Utiliser azdata avec les [services de données dotés d’Azure Arc](/azure/azure-arc/data/)