---
title: Installer SQL Server Agent sur Linux
description: Cet article décrit comment installer SQL Server Agent sur Linux.
author: VanMSFT
ms.author: vanto
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 77f16adc-e6cb-4a57-82f3-7b9780369868
ms.openlocfilehash: c27a31a5e6b9ed771df82e942087d7be88270038
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68032472"
---
# <a name="install-sql-server-agent-on-linux"></a>Installer SQL Server Agent sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

 [SQL Server Agent](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent) exécute des tâches SQL Server planifiées. En commençant par SQL Server 2017 CU4, SQL Server Agent est inclus avec le package **mssql-server** et est désactivé par défaut. Pour plus d’informations sur les fonctionnalités prises en charge pour cette version de SQL Server Agent, ainsi que les informations sur la version, consultez les [Notes de publication](sql-server-linux-release-notes.md).

 Installer/désinstaller SQL Server Agent :
- [Pour les versions 2017 CU4 et ultérieures, activez SQL Server Agent](#EnableAgentAfterCU4)
- [Pour les versions 2017 CU3 et antérieures, installez SQL Server Agent](#InstallAgentBelowCU4)


## <a name="EnableAgentAfterCU4">Pour les versions 2017 CU4 et ultérieures, activez SQL Server Agent</a>

 Pour activer SQL Server Agent, procédez comme suit.

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
sudo systemctl restart mssql-server
```

> [!NOTE]
> Si vous effectuez une mise à niveau à partir de 2017 CU3 ou version antérieure avec l’agent installé, SQL Server Agent est activé automatiquement et les packages d’agent précédents sont désinstallés.  

## <a name="InstallAgentBelowCU4">Pour les versions 2017 CU3 et antérieures, installez SQL Server Agent</a>

> [!NOTE]
> Les instructions d’installation ci-dessous s’appliquent à SQL Server versions 2017 CU3 et antérieures. Avant d’installer SQL Server Agent, commencez par [installer SQL Server](sql-server-linux-setup.md#platforms). Cela permet de configurer les clés et les référentiels que vous utilisez pour installer le package **mssql-server-agent**.

Installer SQL Server Agent pour votre plateforme :
- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

### <a name="RHEL">Installer sur RHEL</a>

Utilisez les commandes suivantes pour installer **mssql-server-agent** sur Red Hat Enterprise Linux. 

```bash
sudo yum install mssql-server-agent
sudo systemctl restart mssql-server
```

Si vous avez déjà installé **mssql-server-agent**, vous pouvez mettre à jour vers la dernière version avec les commandes suivantes :

```bash
sudo yum check-update
sudo yum update mssql-server-agent
sudo systemctl restart mssql-server
```

Si vous avez besoin d’une installation hors connexion, recherchez le téléchargement du package SQL Server Agent dans les [Notes de publication](sql-server-linux-release-notes.md). Puis utilisez les mêmes étapes d’installation hors connexion décrites dans l’article [Installer SQL Server](sql-server-linux-setup.md#offline).

### <a name="ubuntu">Installer sur Ubuntu</a>

Utilisez les commandes suivantes pour installer **mssql-server-agent** sur Ubuntu. 

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

Si vous avez déjà installé **mssql-server-agent**, vous pouvez mettre à jour vers la dernière version avec les commandes suivantes :

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

Si vous avez besoin d’une installation hors connexion, recherchez le téléchargement du package SQL Server Agent dans les [Notes de publication](sql-server-linux-release-notes.md). Puis utilisez les mêmes étapes d’installation hors connexion décrites dans l’article [Installer SQL Server](sql-server-linux-setup.md#offline).

### <a name="SLES">Installer sur SLES</a>

Utilisez les étapes suivantes pour installer **mssql-server-agent** sur SUSE Linux Enterprise Server. 

Installer **mssql-server-agent** 

```bash
sudo zypper install mssql-server-agent
sudo systemctl restart mssql-server
```

Si vous avez déjà installé **mssql-server-agent**, vous pouvez mettre à jour vers la dernière version avec les commandes suivantes :

```bash
sudo zypper refresh
sudo zypper update mssql-server-agent
sudo systemctl restart mssql-server
```

Si vous avez besoin d’une installation hors connexion, recherchez le téléchargement du package SQL Server Agent dans les [Notes de publication](sql-server-linux-release-notes.md). Puis utilisez les mêmes étapes d’installation hors connexion décrites dans l’article [Installer SQL Server](sql-server-linux-setup.md#offline).

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur l’utilisation de SQL Server Agent pour créer, planifier et exécuter des tâches, consultez [Exécuter une tâche SQL Server Agent sur Linux](sql-server-linux-run-sql-server-agent-job.md).
