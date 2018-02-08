---
title: Installer SQL Server Integration Services sur Linux | Documents Microsoft
description: "Cette rubrique décrit l’installation de SQL Server Integration Services (SSIS) sur Linux."
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: On Demand
ms.openlocfilehash: d265d1c4fa25f10c58e321cef06cf293fdce5ac5
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="install-sql-server-integration-services-ssis-on-linux"></a>Installer SQL Server Integration Services (SSIS) sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Suivez les étapes de cet article pour installer SQL Server Integration Services (`mssql-server-is`) sur Linux. Pour plus d’informations sur les fonctionnalités prises en charge dans cette version des Services d’intégration pour Linux, consultez les [notes de publication](sql-server-linux-release-notes.md).

Installer SQL Server Integration Services pour votre plateforme :

- [Ubuntu](#ubuntu)
- [Red Hat Enterprise Linux](#RHEL)

## <a name="ubuntu"></a>Installer SSIS sur Ubuntu
Pour installer le package `mssql-server-is` sur Ubuntu, procédez comme suit :

1. Importer les clés GPG référentiel public.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Inscrire le référentiel Microsoft SQL Server pour Ubuntu.

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

3. Exécutez les commandes suivantes pour installer SQL Server Integration Services.

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server-is
   ```

4. Après l’installation d’Integration Services, exécutez `ssis-conf`. Pour plus d’informations, consultez [configurer de SSIS sur Linux avec ssis-conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

5. Une fois la configuration terminée, configurez le chemin d’accès.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>Mise à jour SSIS
Si `mssql-server-is` est déjà installé, vous pouvez mettre à jour vers la dernière version avec la commande suivante :

```bash
sudo apt-get install mssql-server-is
```

### <a name="remove-ssis"></a>Supprimer SSIS
Pour supprimer `mssql-server-is`, vous pouvez exécuter la commande suivante :
```bash
sudo apt-get remove msssql-server-is
```

## <a name="RHEL"></a>Installer SSIS sur RHEL
Pour installer le package `mssql-server-is` sur RHEL, procédez comme suit :

1. Téléchargez le fichier de configuration du référentiel Microsoft SQL Server Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

1. Exécutez les commandes suivantes pour installer SQL Server Integration Services.

   ```bash
   sudo yum install -y mssql-server-is
   ```


1. Après l’installation, exécutez `ssis-conf`. Pour plus d’informations, consultez [configurer de SSIS sur Linux avec ssis-conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

1. Une fois la configuration terminée, configurez le chemin d’accès.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>Mise à jour SSIS
Si `mssql-server-is` est déjà installé, vous pouvez mettre à jour vers la dernière version avec la commande suivante :

```bash
sudo yum update mssql-server-is
```

### <a name="remove-ssis"></a>Supprimer SSIS
Pour supprimer `mssql-server-is`, vous pouvez exécuter de commande suivante :
```bash
sudo yum remove msssql-server-is
```




## <a name="run-a-package"></a>Exécuter un package
Copiez le package SSIS sur l’ordinateur Linux. Puis utilisez la commande suivante pour exécuter le package.

```bash
dtexec /F <package name> /DE <protection password>
```



## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’utilisation de SSIS sur Linux pour extraire, transformer et charger des données, consultez [extraire, transformer et charger les données pour SQL Server sur Linux avec SSIS](sql-server-linux-migrate-ssis.md).
