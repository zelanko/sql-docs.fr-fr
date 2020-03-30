---
title: Installer PolyBase sur Linux
titlesuffix: SQL Server
description: Cet article décrit comment installer PolyBase SQL Server sur Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.date: 7/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: 117620c170b183b12d06eb717cfc1bb4b2dc559c
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "77173560"
---
# <a name="install-polybase-on-linux"></a>Installer PolyBase sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Les étapes suivantes permettent d’installer [PolyBase](../../relational-databases/search/full-text-search.md) (**mssql-server-polybase**) sur Linux. PolyBase vous permet d’exécuter des requêtes externes par rapport à des sources de données distantes. 

>[!NOTE]
> Avant d’installer Polybase, vous devez d’abord [installer SQL Server 2019 (préversion)](../../linux/sql-server-linux-setup.md#platforms). Cela permet de configurer les clés et les référentiels que vous utilisez pour installer le package **mssql-server-polybase**.
>
> PolyBase n’est pas pris en charge par SQL Server 2017 pour Linux.
> Le scale-out pour PolyBase sur Linux est actuellement indisponible.

Installation de PolyBase pour votre système d’exploitation :

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)



## <a name=""></a><a name="RHEL">Installer sur RHEL</a>

Utilisez la commande suivante pour installer **mssql-server-polybase** sur Red Hat Enterprise Linux. 

```bash
sudo yum install -y mssql-server-polybase
```

Vous devrez redémarrer l’instance de SQL Server. Pour ce faire, exécutez la commande suivante.

```bash
sudo systemctl restart mssql-server
```

>[!NOTE]
>Après l’installation, vous devez [activer la fonctionnalité PolyBase](#enable).

Si vous avez besoin d’une installation hors connexion, recherchez le téléchargement du package PolyBase dans les [Notes de publication](../../linux/sql-server-linux-release-notes.md). Puis utilisez les mêmes étapes d’installation hors connexion décrites dans l’article [Installer SQL Server](../../linux/sql-server-linux-setup.md#offline).

## <a name=""></a><a name="ubuntu">Installer sur Ubuntu</a>

Utilisez la commande suivante pour installer **mssql-server-polybase** sur Ubuntu. 

```bash
sudo apt-get install mssql-server-polybase
```

Vous devrez redémarrer l’instance de SQL Server. Pour ce faire, exécutez la commande suivante.

```bash
sudo systemctl restart mssql-server
```

>[!NOTE]
>Après l’installation, vous devez [activer la fonctionnalité PolyBase](#enable).

Si vous avez besoin d’une installation hors connexion, recherchez le téléchargement du package PolyBase dans les [Notes de publication](../../linux/sql-server-linux-release-notes.md). Puis utilisez les mêmes étapes d’installation hors connexion décrites dans l’article [Installer SQL Server](../../linux/sql-server-linux-setup.md#offline).

## <a name=""></a><a name="SLES">Installer sur SLES</a>

Utilisez la commande suivante pour installer **mssql-server-polybase** sur SLES. 

```bash
sudo zypper install mssql-server-polybase
```

Vous devrez redémarrer l’instance de SQL Server. Pour ce faire, exécutez la commande suivante.

```bash
sudo systemctl restart mssql-server
```

>[!NOTE]
>Après l’installation, vous devez [activer la fonctionnalité PolyBase](#enable).


Si vous avez besoin d’une installation hors connexion, recherchez le téléchargement du package PolyBase dans les [Notes de publication](../../linux/sql-server-linux-release-notes.md). Puis utilisez les mêmes étapes d’installation hors connexion décrites dans l’article [Installer SQL Server](../../linux/sql-server-linux-setup.md#offline).


## <a name=""></a><a name="enable">Activer PolyBase</a> 

Après l’installation, vous devez activer PolyBase pour accéder à ses fonctionnalités. Connectez-vous à l’instance de SQL Server installée et utilisez la commande Transact-SQL suivante pour l’activation.

```sql
exec sp_configure @configname = 'polybase enabled', @configvalue = 1;
RECONFIGURE WITH OVERRIDE;
```

## <a name="update-polybase"></a>Mettre à jour PolyBase

Si vous avez déjà installé **mssql-server-polybase**, vous pouvez mettre à jour vers la dernière version avec les commandes suivantes :

### <a name="rhel"></a>RHEL

```bash
sudo yum remove -y mssql-server-polybase
sudo yum check-update
sudo yum install -y mssql-server-polybase
```

Vous devrez redémarrer l’instance de SQL Server. Pour ce faire, exécutez la commande suivante.

```
sudo systemctl restart mssql-server
```

### <a name="ubuntu"></a>Ubuntu

```bash
sudo apt-get remove mssql-server-polybase
sudo apt-get update 
sudo apt-get install mssql-server-polybase
```

Vous devrez redémarrer l’instance de SQL Server. Pour ce faire, exécutez la commande suivante.

```
sudo systemctl restart mssql-server
```

### <a name="sles"></a>SLES

```bash
sudo zypper remove mssql-server-polybase
sudo zypper refresh
sudo zypper install mssql-server-polybase
```

Vous devrez redémarrer l’instance de SQL Server. Pour ce faire, exécutez la commande suivante.

```
sudo systemctl restart mssql-server
```

>[!NOTE]
>Après l’installation, vous devez [activer la fonctionnalité PolyBase](#enable).

## <a name="next-steps"></a>Étapes suivantes

PolyBase sur Linux peut accéder aux sources de données suivantes. Suivez les liens pour plus d’informations sur la façon dont la création d’une table externe à partir de ces sources sur PolyBase est permise. 

- [SQL Server ( & SQL DB, Azure SQL DW)](../../relational-databases/polybase/polybase-configure-sql-server.md)
- [Oracle](../../relational-databases/polybase/polybase-configure-oracle.md)
- [Teradata](../../relational-databases/polybase/polybase-configure-teradata.md)
- [MongoDB (& Cosmos DB)](../../relational-databases/polybase/polybase-configure-mongodb.md)

Pour plus d’informations sur l’utilisation de ces paramètres, consultez l’article de référence sur Transact-SQL pour [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
