---
title: Installer PolyBase sur Linux | Microsoft Docs
description: Cet article décrit comment installer la recherche en texte intégral SQL Server sur Linux.
author: aboke
ms.author: aboke
ms.date: 4/12/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: bb42076f-e823-4cee-9281-cd3f83ae42f5
ms.openlocfilehash: 33a6a4415b5ced4bb2a5ca4448ccca8618f96832
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68062145"
---
# <a name="install-polybase-on-linux"></a>Installer PolyBase sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Les étapes suivantes permettent d’installer [PolyBase](../../relational-databases/search/full-text-search.md) (**mssql-server-polybase**) sur Linux. PolyBase vous permet d’exécuter des requêtes externes par rapport à des sources de données distantes. 

>[!NOTE]
> Avant d’installer Polybase, vous devez d’abord [installer SQL Server](../../linux/sql-server-linux-setup.md#platforms). Cela permet de configurer les clés et les référentiels que vous utilisez pour installer le package **mssql-server-polybase**.

> Le scale-out pour PolyBase sur Linux est actuellement indisponible.


Installation de PolyBase pour votre système d’exploitation :

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)



## <a name="RHEL">Installer sur RHEL</a>

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

## <a name="ubuntu">Installer sur Ubuntu</a>

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

## <a name="SLES">Installer sur SLES</a>

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


## <a name="enable">Activer PolyBase</a> 

Après l’installation, vous devez activer PolyBase pour accéder à ses fonctionnalités. Connectez-vous à l’instance de SQL Server installée et utilisez la commande Transact-SQL suivante pour l’activation.

```sql
exec sp_configure @configname = 'polybase enabled', @configvalue = 1;
RECONFIGURE [WITH OVERRIDE];
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

### <a name="supported-external-data-sources-on-linux"></a>Sources de données externes prises en charge sur Linux

PolyBase sur Linux peut accéder aux sources de données suivantes. Suivez les liens pour plus d’informations sur la façon dont la création d’une table externe à partir de ces sources sur PolyBase est permise. 

- [SQL Server ( & SQL DB, Azure SQL DW)](../../relational-databases/polybase/polybase-configure-sql-server.md)
- [Oracle](../../relational-databases/polybase/polybase-configure-oracle.md)
- [Teradata](../../relational-databases/polybase/polybase-configure-teradata.md)
- [MongoDB (& Cosmos DB)](../../relational-databases/polybase/polybase-configure-mongodb.md)

Pour plus d’informations sur l’utilisation de ces paramètres, consultez l’article de référence sur Transact-SQL pour [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).