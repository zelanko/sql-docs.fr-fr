---
title: Installer Azure Data CLI (azdata) avec zypper
titleSuffix: ''
description: Découvrez comment installer l’outil azdata (Azure Data CLI) avec zypper.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 09/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d43a1f9c65aa17fae3d262a51f45105b5f583cdd
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257508"
---
# <a name="install-azure-data-cli-azdata-with-zypper"></a>Installer [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)] avec zypper

[!INCLUDE[azdata](../../includes/applies-to-version/azdata.md)]

Pour les distributions Linux avec `zypper` il existe un package pour le `azdata-cli`. Le package CLI a été testé sur des versions Linux qui utilisent `zypper` :

- openSUSE 42.2 (intercalaire) +
- SLES 12 SP 2 +

[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-with-zypper"></a>Installer avec zypper

>[!IMPORTANT]
>Le package RPM de `azdata-cli` dépend du package python3. Sur votre système, il doit s’agir d’une version Python antérieure à l’exigence de *Python 3.6.x* . Si cela vous pose un problème, recherchez un remplacement au package python3 ou suivez les instructions d’installation manuelle qui utilisent [`pip`](../install/deploy-install-azdata-pip.md).

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