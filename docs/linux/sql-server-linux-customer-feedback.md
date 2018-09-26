---
title: Commentaires des clients pour SQL Server sur Linux | Microsoft Docs
description: Décrit comment les commentaires des clients de SQL Server sont collectées et configuré sur Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 06/22/2018
ms.topic: conceptual
ms.prod: sql
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 31bd8be73051349c122eb4a99dc99417b491669d
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713582"
---
# <a name="customer-feedback-for-sql-server-on-linux"></a>Commentaires des clients pour SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Par défaut, Microsoft SQL Server collecte des informations sur la façon dont ses clients utilisent l’application. Plus précisément, SQL Server recueille des données sur l’expérience d’installation, l’utilisation et les performances. Elles aident Microsoft à améliorer le produit pour mieux répondre aux besoins des clients. Par exemple, Microsoft collecte des informations sur les types de codes d’erreur rencontrés par les utilisateurs afin que nous puissions corriger les bogues associés, améliorer notre documentation sur l’utilisation de SQL Server et déterminer s’il faudrait ajouter des fonctionnalités au produit pour mieux servir des clients.

Ce document fournit des informations détaillées sur les types d’informations sont collectées et sur la façon de configurer Microsoft SQL Server sur Linux pour envoyer ce collectées des informations à Microsoft. SQL Server 2017 inclut une déclaration de confidentialité qui explique quelles informations nous et ne collectent pas d’utilisateurs. Pour plus d’informations, consultez le [déclaration de confidentialité](http://go.microsoft.com/fwlink/?LinkID=868444).

En particulier, Microsoft n’envoie par ce mécanisme aucune information de ces types :

- valeurs des tables utilisateur ;
- identifiants d’ouverture de session ou autres informations d’authentification ;
- informations d’identification personnelle (PII).

SQL Server 2017 collecte et envoie toujours des informations sur l’expérience d’installation à partir du processus d’installation afin de nous permettre de trouver et de résoudre rapidement les problèmes d’installation que rencontre le client. SQL Server 2017 peut être configuré pour ne pas pour envoyer d’informations (sur la base d’une instance par serveur) à Microsoft via **mssql-conf**. MSSQL-conf est un script de configuration qui s’installe avec SQL Server 2017 pour Red Hat Enterprise Linux, SUSE Linux Enterprise Server et Ubuntu.

> [!NOTE]
> Vous ne pouvez désactiver l’envoi d’informations à Microsoft que dans les versions payantes de SQL Server.

## <a name="disable-customer-feedback"></a>Désactiver les commentaires client

Cette option vous permet de modifier si SQL Server envoie des commentaires à Microsoft ou non. Par défaut, cette valeur est définie sur true. Pour modifier la valeur, exécutez les commandes suivantes :

> [!IMPORTANT]
> Vous ne pouvez pas désactiver les commentaires des clients gratuitement éditions de SQL Server, Express et Developer.

### <a name="on-red-hat-suse-and-ubuntu"></a>Sur Ubuntu, SUSE et Red Hat

1. Exécutez le script mssql-conf en tant que root avec la **définir** commande **telemetry.customerfeedback**. L’exemple suivant désactive les commentaires des clients en spécifiant **false**.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.customerfeedback false
   ```

1. Redémarrez le service SQL Server :

   ```bash
   sudo systemctl restart mssql-server
   ```
   
### <a name="on-docker"></a>Sur Docker
Pour désactiver les commentaires des clients sur docker, vous devez disposer de Docker [conserver vos données](sql-server-linux-configure-docker.md). 

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. Ajouter un `mssql.conf` fichier avec les lignes `[telemetry]` et `customerfeedback = false` dans le répertoire de l’hôte :
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'customerfeedback = false' >> <host directory>/mssql.conf
   ```

2. Exécuter l’image conteneur

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

1. Ajouter un `mssql.conf` fichier avec les lignes `[telemetry]` et `customerfeedback = false` dans le répertoire de l’hôte :

   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'customerfeedback = false' >> <host directory>/mssql.conf
   ```

2. Exécuter l’image conteneur

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu
   ```

::: moniker-end

## <a name="local-audit-for-sql-server-on-linux-usage-feedback-collection"></a>Audit local pour SQL Server sur la collecte de commentaires d’utilisation de Linux

Microsoft SQL Server 2017 contient des fonctionnalités Internet qui peuvent recueillir et envoyer des informations sur votre ordinateur ou appareil (« informations standard de l’ordinateur ») à Microsoft. Le composant d’Audit Local de la collection de commentaires sur l’utilisation de SQL Server puisse écrire des données collectées par le service dans un dossier désigné, représentant les données (journaux) qui seront envoyées à Microsoft. L’objectif de l’audit local est d’autoriser les clients à visualiser toutes les données collectées par Microsoft avec cette fonctionnalité, pour des raisons de conformité, de réglementation ou de validation de la confidentialité.

Dans SQL Server sur Linux, l’Audit Local est configurable au niveau de l’instance du moteur de base de données SQL Server. Autres composants SQL Server et les outils SQL Server n’ont pas la fonctionnalité d’Audit Local pour la collecte de commentaires d’utilisation.

### <a name="enable-local-audit"></a>Activer l’Audit Local

Cette option permet l’Audit Local et vous permet de définir le répertoire dans lequel les journaux d’Audit Local sont créées.

1. Créez un répertoire cible pour les nouveaux journaux d’Audit Local. L’exemple suivant crée un nouveau **/tmp/audit** directory :

   ```bash
   sudo mkdir /tmp/audit
   ```

2. Modifier le propriétaire et le groupe du répertoire à la **mssql** utilisateur :

   ```bash
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
   ```

3. Exécutez le script mssql-conf en tant que root avec la **définir** commande **telemetry.userrequestedlocalauditdirectory**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
   ```

4. Redémarrez le service SQL Server :

   ```bash
   sudo systemctl restart mssql-server
   ```
   
### <a name="on-docker"></a>Sur Docker
Pour activer l’Audit Local sur docker, vous devez disposer de Docker [conserver vos données](sql-server-linux-configure-docker.md). 

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. Le répertoire cible pour les nouveaux journaux d’Audit Local sera dans le conteneur. Créez un répertoire cible pour les nouveaux journaux d’Audit Local dans le répertoire de l’hôte sur votre ordinateur. L’exemple suivant crée un nouveau **/ d’audit** directory :

   ```bash
   sudo mkdir <host directory>/audit
   ```

1. Ajouter un `mssql.conf` fichier avec les lignes `[telemetry]` et `userrequestedlocalauditdirectory = <host directory>/audit` dans le répertoire de l’hôte :
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'userrequestedlocalauditdirectory = <host directory>/audit' >> <host directory>/mssql.conf
   ```

1. Exécuter l’image conteneur

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

1. Le répertoire cible pour les nouveaux journaux d’Audit Local sera dans le conteneur. Créez un répertoire cible pour les nouveaux journaux d’Audit Local dans le répertoire de l’hôte sur votre ordinateur. L’exemple suivant crée un nouveau **/ d’audit** directory :

   ```bash
   sudo mkdir <host directory>/audit
   ```

1. Ajouter un `mssql.conf` fichier avec les lignes `[telemetry]` et `userrequestedlocalauditdirectory = <host directory>/audit` dans le répertoire de l’hôte :
 
   ```bash
   echo '[telemetry]' >> <host directory>/mssql.conf
   ```

   ```bash
   echo 'userrequestedlocalauditdirectory = <host directory>/audit' >> <host directory>/mssql.conf
   ```

1. Exécuter l’image conteneur

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu
   ```

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur SQL Server sur Linux, consultez le [vue d’ensemble de SQL Server sur Linux](sql-server-linux-overview.md).
