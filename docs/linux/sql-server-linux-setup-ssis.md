---
title: Installer SQL Server Integration Services sur Linux
description: Cet article explique comment installer SQL Server Integration Services (SSIS) sur Linux.
author: lrtoyou1223
ms.author: lle
ms.reviewer: maghan
ms.date: 01/09/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 68f3497e9f3f47d7e43c2bda0083bc25632d8221
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68032445"
---
# <a name="install-sql-server-integration-services-ssis-on-linux"></a>Installer SQL Server Integration Services (SSIS) sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Procédez comme indiqué dans cet article pour installer SQL Server Integration Services (`mssql-server-is`) sur Linux. Pour plus d’informations sur les fonctionnalités prises en charge dans cette mise en production d’Integration Services pour Linux, consultez les [Notes de publication](sql-server-linux-release-notes.md).

Installer les serveurs d’intégration SQL Server pour votre plateforme :

- [Ubuntu 16.04](#ubuntu)
- [Red Hat Enterprise Linux](#RHEL)

## <a name="ubuntu"></a> Installer SSIS sur Ubuntu
Pour installer le package `mssql-server-is` sur Ubuntu, procédez comme suit :

1. Importez les clés GPG de dépôt public.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Enregistrez le référentiel Microsoft SQL Server Ubuntu.

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

3. Exécutez les commandes suivantes pour installer SQL Server Integration Services.

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server-is
   ```

4. Après l’installation d'Integration Services, exécutez `ssis-conf`. Pour plus d’informations, consultez [Configurer SSIS sur Linux avec ssis-conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

5. Une fois la configuration terminée, définissez le chemin d’accès.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>Mettre à jour SSIS
Si vous avez déjà installé `mssql-server-is`, vous pouvez mettre à jour vers la dernière version avec les commandes suivantes :

```bash
sudo apt-get install mssql-server-is
```

### <a name="remove-ssis"></a>Supprimer SSIS
Pour supprimer `mssql-server-is`, vous pouvez exécuter la commande suivante :
```bash
sudo apt-get remove mssql-server-is
```

## <a name="RHEL"></a> Installer SSIS sur RHEL
Pour installer le package `mssql-server-is` sur RHEL, procédez comme suit :

1. Téléchargez le fichier config du référentiel Microsoft SQL Server Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

1. Exécutez les commandes suivantes pour installer SQL Server Integration Services.

   ```bash
   sudo yum install -y mssql-server-is
   ```


1. Après l’installation, exécutez `ssis-conf`. Pour plus d’informations, consultez [Configurer SSIS sur Linux avec ssis-conf](sql-server-linux-configure-ssis.md).

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

1. Une fois la configuration terminée, définissez le chemin d’accès.

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>Mettre à jour SSIS
Si vous avez déjà installé `mssql-server-is`, vous pouvez mettre à jour vers la dernière version avec les commandes suivantes :

```bash
sudo yum update mssql-server-is
```

### <a name="remove-ssis"></a>Supprimer SSIS
Pour supprimer `mssql-server-is`, vous pouvez exécuter la commande suivante :
```bash
sudo yum remove mssql-server-is
```

## <a name="unattended-installation"></a>Installation sans assistance
Pour exécuter une installation sans assistance lors de l’exécution de `ssis-conf setup`, effectuez les opérations suivantes :
1.  Spécifiez l’option `-n` (aucune invite).
2.  Fournissez les valeurs requises en définissant les variables d’environnement.

L’exemple suivant effectue les opérations suivantes :
-   Installe SSIS.
-   Spécifie l’édition Développeur en fournissant une valeur pour la variable d’environnement `SSIS_PID`.
-   Accepte le CLUF en fournissant une valeur pour la variable d’environnement `ACCEPT_EULA`.
-   Exécute une installation sans assistance en spécifiant l'option `-n` (aucune invite).

```
sudo SSIS_PID=Developer ACCEPT_EULA=Y /opt/ssis/bin/ssis-conf -n setup 
```

### <a name="environment-variables-for-unattended-installation"></a>Variables d’environnement pour une installation sans assistance

| Variable d'environnement | Description |
|---|---|
| **ACCEPT_EULA** | Accepte le contrat de licence SQL Server lorsqu’il est défini sur n’importe quelle valeur (par exemple, `Y`).|
| **SSIS_PID** | Définit l’édition SQL Server ou la clé de produit (Product key). Les valeurs possibles sont les suivantes :<br/>Evaluation<br/>Développeur<br/>Express <br/>Web <br/>Standard<br/>Enterprise <br/>Une clé de produit (Product Key)<br/><br/>Si vous spécifiez une clé de produit (Product Key), elle doit se présenter sous la forme `#####-#####-#####-#####-#####`, où `#` est une lettre ou un nombre.  |
| | |

## <a name="next-steps"></a>Étapes suivantes

Pour exécuter des packages SSIS sur Linux, consultez [Extraire, transformer et charger des données pour SQL Server sur Linux avec SSIS](sql-server-linux-migrate-ssis.md).

Pour configurer des paramètres SSIS supplémentaires sur Linux, consultez [Configurer SQL Server Integration Services sur Linux avec ssis-conf](sql-server-linux-configure-ssis.md).

## <a name="related-content-about-ssis-on-linux"></a>Contenu connexe relatif à SSIS sur Linux
-   [Extraire, transformer et charger des données sur Linux avec SSIS](sql-server-linux-migrate-ssis.md)
-   [Configurer SQL Server Integration Services sur Linux avec ssis-conf](sql-server-linux-configure-ssis.md)
-   [Limitations et problèmes connus pour SSIS sur Linux](sql-server-linux-ssis-known-issues.md)
-   [Planifier l’exécution du package SQL Server Integration Services sur Linux avec cron](sql-server-linux-schedule-ssis-packages.md)
