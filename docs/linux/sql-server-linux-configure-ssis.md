---
title: Configurer SSIS sur Linux avec ssis-conf | Microsoft Docs
description: Cet article décrit comment configurer SQL Server Integration Services (SSIS) sur Linux avec l’utilitaire ssis-conf.
author: lrtoyou1223
ms.author: lle
ms.reviewer: maghan
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: fa00ec33039cd4a6e601321604ae60bd125fec7e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705567"
---
# <a name="configure-sql-server-integration-services-on-linux-with-ssis-conf"></a>Configurer SQL Server Integration Services sur Linux avec ssis-conf

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Vous exécutez le `ssis-conf` script de configuration lorsque vous installez SQL Server Integration Services (SSIS) pour Red Hat Enterprise Linux et Ubuntu. Pour plus d’informations sur l’installation de SSIS, consultez [installer SQL Server Integration Services (SSIS) sur Linux](sql-server-linux-setup-ssis.md).

Vous pouvez également utiliser le `ssis-conf` utilitaire pour configurer les propriétés suivantes :

| Command | Description |
|-------------|---------------------------------------------------------------------|
| set-edition | Définir l’édition de SQL Server                                       |
| données de télémétrie   | Activer ou désactiver le service de télémétrie SQL Server Integration Services |
| configurer       | Initialiser et configurer Microsoft SQL Server Integration Services      |
|||

## <a name="run-ssis-conf"></a>Exécutez ssis-conf

Les exemples de cet article nécessitent de spécifier le chemin complet `/opt/ssis/bin/ssis-conf` afin d'exécuter `ssis-conf`. Si au préalable vous accédez à cet emplacement avant d’exécuter `ssis-conf`, vous pouvez exécuter l’utilitaire dans le contexte du répertoire actif : `./ssis-conf`.

Veillez à exécuter les commandes qui sont décrites dans cet article avec des privilèges `root`. Par exemple, exécutez `sudo /opt/ssis/bin/ssis-conf setup` et non `/opt/ssis/bin/ssis-conf setup`.

Pour exécuter ces commandes avec des messages dans la langue que vous préférez, vous pouvez spécifier des paramètres régionaux. Par exemple, pour recevoir des invites en chinois, exécutez la commande suivante : `sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="use-set-edition-to-set-the-edition-of-sql-server-integration-services"></a>Set-edition permet de définir l’édition de SQL Server Integration Services

L’édition de SSIS est alignée avec l’édition de SQL Server.

Entrez la commande suivante : `$ sudo /opt/ssis/bin/ssis-conf set-edition`.

Après avoir entré la commande, vous recevrez l’invite suivante :

```
Choose an edition of SQL Server:

1) Evaluation (free, no production use rights, 180-day limit)

2) Developer (free, no production use rights)

3) Express (free)

4) Web (PAID)

5) Standard (PAID)

6) Enterprise (PAID)

7) Enterprise Core (PAID)

8) I bought a license through a retail sales channel and have a product key to enter.

Details about editions can be found at https://go.microsoft.com/fwlink/?LinkId=852748&clcid=0x409.

Use of PAID editions of this software requires separate licensing through a Microsoft Volume Licensing program.

By choosing a PAID edition, you are verifying that you have the appropriate number of licenses in place to install and run this software.

Enter your edition (1-8):
```

Si vous entrez une valeur comprise entre 1 et 7, le système configure une édition gratuite ou payante. Si vous entrez 8, l’utilitaire vous invite à entrer la clé de produit que vous avez achetées :

```
Enter the 25-character product key:
```

## <a name="use-telemetry-to-configure-customer-feedback"></a>Utilisation de la télémétrie pour configurer les commentaires des clients

La commande `telemetry` détermine si SSIS envoie des relevés de télémétrie à Microsoft.

Pour les éditions gratuites (autrement dit, les éditions Express, Developer et Evaluation), le service de télémétrie est toujours activé. Si vous avez une édition gratuite, vous ne pouvez pas utiliser le `telemetry` commande pour désactiver la télémétrie.

Entrez la commande suivante : `$ sudo /opt/ssis/bin/ssis-conf telemetry`.

Pour les éditions payantes, après avoir entré la commande, vous recevrez le message suivant :

```
Send feature usage data to Microsoft. Feature usage data includes information about your hardware configuration and how you use SQL Server Integration Services.

[Yes/No]:
```

Si vous sélectionnez **Oui**, le service de télémétrie est activé et commence à s’exécuter. Le service démarre automatiquement après chaque démarrage. Si vous sélectionnez **non**, le service de télémétrie s’arrête et est désactivé.

## <a name="use-setup-to-initialize-and-set-up-microsoft-sql-server-integration-services"></a>Utilisez le programme d’installation pour initialiser et configurer Microsoft SQL Server Integration Services

Utilisez la commande `setup` chaque fois que vous installez SSIS.

Entrez la commande suivante : `sudo /opt/ssis/bin/ssis-conf setup`.

L’utilitaire vous invite à accepter ou de fournir des valeurs pour les éléments suivants :
-   Licence de produit
-   CLUF
-   Service de télémétrie
-   La langue utilisée par les Services d’intégration

Pour exécuter le `setup` commande invite dans la langue que vous préférez, vous pouvez spécifier des paramètres régionaux. Par exemple, pour recevoir des invites en chinois, exécutez la commande suivante : `sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="ssisconf-format"></a>format de SSIS.conf

Le fichier `/var/opt/ssis/ssis.conf` suivant fournit un exemple pour chaque paramètre.

Pour SQL Server, vous pouvez modifier les paramètres du système en modifiant les valeurs dans le fichier `mssql.conf`. Pour SSIS, vous *ne pouvez pas* modifier les paramètres système en modifiant les valeurs dans le fichier `ssis.conf`. Le fichier `ssis.conf` montre uniquement les résultats après l’installation. Si vous souhaitez modifier les paramètres de SSIS, vous devez supprimer le fichier `ssis.conf` et exécuter à nouveau la commande `setup`.

Voici un exemple de fichier `ssis.conf`. Chaque champ correspond au résultat d’une étape d’installation.

```
[LICENSE]
                       
registered = Y        
                       
pid = enterprisecore  
                       
[EULA]
                       
accepteula = Y        
                       
[TELEMETRY]
                       
enabled = Y           
                       
[language]
                       
lcid = 2052
```

## <a name="related-content-about-ssis-on-linux"></a>Contenu associé sur SSIS sur Linux
-   [Extraire, transformer et charger des données sur Linux avec SSIS](sql-server-linux-migrate-ssis.md)
-   [Installer SQL Server Integration Services (SSIS) sur Linux](sql-server-linux-setup-ssis.md)
-   [Limitations et problèmes connus pour SSIS sur Linux](sql-server-linux-ssis-known-issues.md)
-   [L’exécution sur Linux avec cron du package de planification SQL Server Integration Services](sql-server-linux-schedule-ssis-packages.md)
