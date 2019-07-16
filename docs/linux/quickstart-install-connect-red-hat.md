---
title: Prise en main de SQL Server sur Red Hat Enterprise Linux
titleSuffix: SQL Server
description: Ce démarrage rapide montre comment installer SQL Server 2017 ou SQL Server 2019 sur Red Hat Enterprise Linux et ensuite créer et interroger une base de données avec sqlcmd.
author: VanMSFT
ms.author: vanto
ms.date: 07/16/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 92503f59-96dc-4f6a-b1b0-d135c43e935e
ms.openlocfilehash: 38df65ffefbc0ed264d631214025059449d84b35
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67910507"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-red-hat"></a>Démarrage rapide : Installer SQL Server et de créer une base de données sur Red Hat

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Dans ce démarrage rapide, vous installez SQL Server 2017 ou SQL Server 2019 sur Red Hat Enterprise Linux (RHEL). Vous vous connectez ensuite avec **sqlcmd** pour créer votre première base de données et exécuter des requêtes.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Ce démarrage rapide, vous installez SQL Server 2019 aperçu sur Red Hat Enterprise Linux (RHEL) 7.3 +. Vous vous connectez ensuite avec **sqlcmd** pour créer votre première base de données et exécuter des requêtes.

::: moniker-end

> [!TIP]
> Ce didacticiel nécessite une saisie de la part de l’utilisateur et une connexion Internet. Si vous êtes intéressé par les procédures d'installation [sans assistance](sql-server-linux-setup.md#unattended) ou [hors connexion](sql-server-linux-setup.md#offline), consultez [aide à l’installation de SQL Server sur Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Prérequis

Vous devez disposer d’une machine RHEL 7.3, 7.4, 7.5 ou 7.6 avec **au moins 2 Go** de mémoire.

Pour installer Red Hat Enterprise Linux sur votre propre machine, accédez à [ https://access.redhat.com/products/red-hat-enterprise-linux/evaluation ](https://access.redhat.com/products/red-hat-enterprise-linux/evaluation). Vous pouvez également créer des machines virtuelles RHEL dans Azure. Consultez [créer et gérer des machines virtuelles Linux avec Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)et utiliser `--image RHEL` dans l’appel à `az vm create`.

Si vous avez déjà installé une version CTP ou la version RC de SQL Server 2017, vous devez d’abord supprimer l’ancien référentiel avant de suivre ces étapes. Pour plus d’informations, consultez [référentiels configurer Linux pour SQL Server 2017 et 2019](sql-server-linux-change-repo.md).

Pour les autres exigences système, consultez [configuration système requise pour SQL Server sur Linux](sql-server-linux-setup.md#system).

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="install"></a>Installer SQL Server

Pour configurer SQL Server sur RHEL, exécutez les commandes suivantes dans un terminal pour installer le package **mssql-server** :

1. Téléchargez le fichier de configuration du référentiel Microsoft SQL Server 2017 Red Hat :

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

   > [!TIP]
   > Si vous souhaitez essayer SQL Server 2019, vous devez inscrire à la place la **aperçu (2019)** référentiel. Pour les installations de SQL Server 2019, utilisez la commande suivante :
   >
   > ```bash
   > sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo
   > ```

2. Exécutez les commandes suivantes pour installer SQL Server :

   ```bash
   sudo yum install -y mssql-server
   ```

3. Après la fin de l’installation du package, exécutez le programme d’installation **mssql-conf** et suivez les invites pour définir le mot de passe SA et choisir votre édition.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Les éditions suivantes de SQL Server 2017 sont librement concédée sous licence : Evaluation, Developer et Express.

   > [!NOTE]
   > Veillez à spécifier un mot de passe fort pour le compte d’administrateur système (longueur minimale de 8 caractères, incluant des majuscules et des minuscules, des chiffres et/ou des caractères spéciaux).

4. Une fois la configuration terminée, vérifiez que le service est en cours d’exécution :

   ```bash
   systemctl status mssql-server
   ```

5. Pour autoriser les connexions à distance, ouvrez le port SQL Server sur le pare-feu sur RHEL. Le port de SQL Server par défaut est TCP 1433. Si vous utilisez **FirewallD** comme pare-feu, vous pouvez utiliser les commandes suivantes :

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

À ce stade, SQL Server est en cours d’exécution sur votre ordinateur RHEL et est prêt à être utilisé.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="install"></a>Installer SQL Server

Pour configurer SQL Server sur RHEL, exécutez les commandes suivantes dans un terminal pour installer le package **mssql-server** :

1. Téléchargez la version préliminaire de Microsoft SQL Server 2019 fichier de configuration du référentiel Red Hat :

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo
   ```

2. Exécutez les commandes suivantes pour installer SQL Server :

   ```bash
   sudo yum install -y mssql-server
   ```

3. Après la fin de l’installation du package, exécutez le programme d’installation **mssql-conf** et suivez les invites pour définir le mot de passe SA et choisir votre édition.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!NOTE]
   > Veillez à spécifier un mot de passe fort pour le compte d’administrateur système (longueur minimale de 8 caractères, incluant des majuscules et des minuscules, des chiffres et/ou des caractères spéciaux).

4. Une fois la configuration terminée, vérifiez que le service est en cours d’exécution :

   ```bash
   systemctl status mssql-server
   ```

5. Pour autoriser les connexions à distance, ouvrez le port SQL Server sur le pare-feu sur RHEL. Le port de SQL Server par défaut est TCP 1433. Si vous utilisez **FirewallD** comme pare-feu, vous pouvez utiliser les commandes suivantes :

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

À ce stade, SQL Server 2019 aperçu est en cours d’exécution sur votre ordinateur RHEL et est prêt à utiliser !

::: moniker-end

## <a id="tools"></a>Installer les outils de ligne de commande SQL Server

Pour créer une base de données, vous devez vous connecter avec un outil qui peut exécuter des instructions Transact-SQL sur le serveur SQL Server. Les étapes suivantes permettent d'installer les outils de ligne de commande de SQL Server : [sqlcmd](../tools/sqlcmd-utility.md) et [bcp](../tools/bcp-utility.md).

1. Téléchargez le fichier de configuration du référentiel Microsoft Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```

1. Si vous aviez une version précédente de **mssql-tools** installée, supprimez tous les packages unixODBC plus anciens.

   ```bash
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. Exécutez les commandes suivantes pour installer **mssql-tools** avec le package développeur unixODBC.

   ```bash
   sudo yum install -y mssql-tools unixODBC-devel
   ```

1. Pour plus de commodité, ajoutez `/opt/mssql-tools/bin/` à votre variable d'environnement de **chemin d’accès**. Cela vous permet d’exécuter les outils sans spécifier le chemin d’accès complet. Exécutez les commandes suivantes pour modifier le **chemin d’accès** pour les sessions interactives avec et sans login :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
