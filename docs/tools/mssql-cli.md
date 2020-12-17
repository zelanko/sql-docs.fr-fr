---
title: mssql-cli
description: mssql-cli est un outil de requête de ligne de commande interactif pour SQL Server qui s’exécute sur Windows, macOS ou Linux.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, sstein, maghan
ms.custom: tools|mssql-cli
ms.date: 02/22/2018
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017
ms.openlocfilehash: 345d188106877f5f5aa6740c7e4db7c0c0511bfb
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97471780"
---
# <a name="mssql-cli-command-line-query-tool-for-sql-server-preview"></a>Outil de requête de ligne de commande mssql-cli pour SQL Server (préversion)

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

mssql-cli est un outil de requête de ligne de commande interactif pour interroger SQL Server exécuté sur Windows, macOS ou Linux.

## <a name="install-mssql-cli"></a>Installer mssql-cli

Pour obtenir des instructions d’installation plus détaillées, consultez le [Guide d’installation](https://github.com/dbcli/mssql-cli/tree/master/doc/installation). Les scénarios d’installation les plus courants sont résumés ci-dessous.

### <a name="windows-and-macos-installation"></a>Installation Windows et macOS

mssql-cli est installé sur Windows et macOS à l’aide de `pip` :

```$ pip install mssql-cli```

Pour obtenir des instructions plus détaillées, consultez le [Guide d’installation](https://github.com/dbcli/mssql-cli/tree/master/doc/installation).

### <a name="linux-installation"></a>Installation sur Linux

Après avoir inscrit le référentiel Microsoft, mssql-cli peut être installé et mis à niveau par le biais de gestionnaires de package sur plusieurs distributions Linux.

L’exemple suivant s’applique à Ubuntu 18.04 (Bionic). vous trouverez des informations supplémentaires et des exemples pour les autres distributions dans le [Guide d’installation](https://github.com/dbcli/mssql-cli/tree/master/doc/installation).

```
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo apt-add-repository https://packages.microsoft.com/ubuntu/18.04/prod

# Update the list of products
sudo apt-get update

# Install mssql-cli
sudo apt-get install mssql-cli

# Install missing dependencies
sudo apt-get install -f
```

## <a name="mssql-cli-documentation"></a>Documentation mssql-cli

La documentation concernant mssql-cli se trouve dans le [référentiel GitHub mssql-cli](https://github.com/dbcli/mssql-cli).

- [Page principale/Lisez-moi](https://github.com/dbcli/mssql-cli)
- [Guide d’installation](https://github.com/dbcli/mssql-cli/tree/master/doc/installation)
- [Guide d’utilisation](https://github.com/dbcli/mssql-cli/blob/master/doc/usage_guide.md)

Vous trouverez une documentation supplémentaire dans le [dossier doc](https://github.com/dbcli/mssql-cli/tree/master/doc).
