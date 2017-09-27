---
title: Installer SQL Server Integration Services sur Linux | Documents Microsoft
description: "Cette rubrique décrit l’installation de SQL Server Integration Services sur Linux."
author: leolimsft
ms.author: lle
manager: craigg
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: integration-services
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c3943870ec10b8430ac4819398908c5459a8b03c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="install-sql-server-integration-services-ssis-on-linux"></a>Installer SQL Server Integration Services (SSIS) sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Suivez les étapes de cet article pour installer SQL Server Integration Services (`mssql-server-is`) sur Linux. Pour plus d’informations sur les fonctionnalités prises en charge dans cette version des Services d’intégration pour Linux, consultez le [Release Notes](sql-server-linux-release-notes.md).

Installer des serveurs d’intégration de SQL Server pour votre plateforme :

- [Ubuntu](#ubuntu)
- [Red Hat Enterprise Linux](#RHEL)



## <a name="ubuntu"></a>Installer SSIS sur Ubuntu
Pour installer le `mssql-server-is` le package sur Ubuntu, procédez comme suit :


1.  Importer les clés GPG référentiel public.

    ```bash
    curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```


2.  Inscrire le référentiel d’Ubuntu de Microsoft SQL Server.

    ```bash
    curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server.list | sudo tee /etc/apt/sources.list.d/mssql-server.list
    ```


3.  Exécutez les commandes suivantes pour installer SQL Server Integration Services.

    ```bash
    sudo apt-get update
    sudo apt-get install -y mssql-server-is
    ```


4.  Après l’installation d’Integration Services, exécutez `ssis-conf`.

    ```bash
    sudo /opt/ssis/bin/ssis-conf setup
    ```


5.  Une fois la configuration terminée, définissez le chemin d’accès.

    ```bash
    export PATH=/opt/ssis/bin:$PATH
    ```


Si vous avez déjà `mssql-server-is` installé, vous pouvez mettre à jour vers la dernière version avec la commande suivante :

```bash
sudo apt-get install mssql-server-is
```


Pour supprimer `mssql-server-is`, vous pouvez exécuter de commande suivante :
```bash
sudo apt-get remove msssql-server-is
```



## <a name="RHEL"></a>Installer SSIS sur RHEL
Pour installer le `mssql-server-is` le package sur RHEL, procédez comme suit :


1.  Activer le mode de super utilisateur.

    ```bash
    sudo su
    ```


2.  Téléchargez le fichier de configuration de Microsoft SQL Server Red Hat référentiel.

    ```bash
    curl https://packages.microsoft.com/config/rhel/7/mssql-server.repo > /etc/yum.repos.d/mssql-server.repo
    ```


3.  Quitter le mode Super utilisateur.

    ```bash
    exit
    ```


4.  Exécutez les commandes suivantes pour installer SQL Server Integration Services.

    ```bash
    sudo yum install -y mssql-server-is
    ```


5.  Après l’installation, exécutez `ssis-conf`.

    ```bash
    sudo /opt/ssis/bin/ssis-conf setup
    ```


6.  Une fois la configuration terminée, définissez le chemin d’accès.

    ```bash
    export PATH=/opt/ssis/bin:$PATH
    ```


Si vous avez déjà `mssql-server-is` installé, vous pouvez mettre à jour vers la dernière version avec la commande suivante :

```bash
sudo yum update mssql-server-is
```


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
