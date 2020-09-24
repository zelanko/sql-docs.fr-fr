---
title: Installer azdata avec zypper
titleSuffix: ''
description: Découvrez comment installer l’outil azdata avec zypper.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8fdde8b6229bd2fc98005025e17efe97104d2fc1
ms.sourcegitcommit: d56f1eca807c55cf606a6316f3872585f014fec1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90914889"
---
# <a name="install-azdata-with-zypper"></a>Installer `azdata` avec zypper

Pour les distributions Linux avec `zypper` il existe un package pour le `azdata-cli`. Le package CLI a été testé sur des versions Linux qui utilisent `zyper` :

- openSUSE 42.2 (intercalaire) +
- SLES 12 SP 2 +

[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-with-zypper"></a>Installer avec zypper
>[!IMPORTANT]
>Le package RPM de `azdata-cli` dépend du package python3. Sur votre système, il doit s’agir d’une version Python antérieure à l’exigence de *Python 3.6.x*. Si cela vous pose un problème, recherchez un remplacement au package python3 ou suivez les instructions d’installation manuelle qui utilisent [`pip`](../install/deploy-install-azdata-pip.md).

1. Installer des dépendances nécessaires pour installer `azdata-cli`

   ```bash
   sudo zypper install -y curl
   ```

1. Importer la clé de référentiel Microsoft

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

1. Créer des informations de référentiel locales

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo
   ```

1. Installer

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

Supprimer le package de votre système

```bash
   sudo zypper removerepo azdata-cli
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)] ?](../../big-data-cluster/big-data-cluster-overview.md).

Utiliser azdata avec les [services de données dotés d’Azure Arc](/azure/azure-arc/data/)