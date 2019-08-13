---
title: Mise en route avec SQL Server sur Red Hat Enterprise Linux
titleSuffix: SQL Server
description: Ce démarrage rapide montre comment installer SQL Server 2017 ou SQL Server 2019 sur Red Hat Enterprise Linux, puis comment créer et interroger une base de données avec sqlcmd.
author: VanMSFT
ms.author: vanto
ms.date: 07/16/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 92503f59-96dc-4f6a-b1b0-d135c43e935e
ms.openlocfilehash: 38df65ffefbc0ed264d631214025059449d84b35
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67910507"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-red-hat"></a>Démarrage rapide : Installer SQL Server et créer une base de données sur Red Hat

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Dans ce démarrage rapide, vous installez SQL Server 2017 ou SQL Server 2019 sur Red Hat Enterprise Linux (RHEL). Ensuite, vous vous connectez avec **sqlcmd** pour créer votre première base de données et exécuter des requêtes.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Dans ce démarrage rapide, vous installez la préversion de SQL Server 2019 sur Red Hat Enterprise Linux (RHEL) 7.3 et versions ultérieures. Ensuite, vous vous connectez avec **sqlcmd** pour créer votre première base de données et exécuter des requêtes.

::: moniker-end

> [!TIP]
> Ce tutoriel nécessite l'intervention de l'utilisateur et une connexion Internet. Si vous êtes intéressé par les procédures d'installation [sans assistance](sql-server-linux-setup.md#unattended) ou [hors ligne](sql-server-linux-setup.md#offline), voir [Conseils d’installation pour SQL Server sur Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Conditions préalables requises

Vous devez disposer d’une machine RHEL 7.3, 7.4, 7.5 ou 7.6 avec **au moins 2 Go** de mémoire.

Pour installer Red Hat Enterprise Linux sur votre propre machine, voir [https://access.redhat.com/products/red-hat-enterprise-linux/evaluation](https://access.redhat.com/products/red-hat-enterprise-linux/evaluation). Vous pouvez également créer des machines virtuelles RHEL dans Azure. Consultez [Créer et gérer des machines virtuelles Linux avec l’interface Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm), puis utilisez `--image RHEL` dans l’appel à `az vm create`.

Si vous avez déjà installé une version CTP ou RC de SQL Server 2017, vous devez d'abord supprimer l'ancien référentiel avant de suivre ces étapes. Pour plus d'informations, voir [Configurer des référentiels Linux pour SQL Server 2017 et 2019](sql-server-linux-change-repo.md).

Pour les autres configurations système requises, voir [Configuration système requise pour SQL Server sur Linux](sql-server-linux-setup.md#system).

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="install"></a>Installer SQL Server

Pour configurer SQL Server sur RHEL, exécutez les commandes suivantes dans un terminal afin d’installer le package **mssql-server** :

1. Téléchargez le fichier config du référentiel Microsoft SQL Server 2017 Red Hat :

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

   > [!TIP]
   > Si vous voulez tester SQL Server 2019, vous devez plutôt enregistrer le référentiel de la **préversion (2019)** . Utilisez la commande suivante pour les installations SQL Server 2019 :
   >
   > ```bash
   > sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo
   > ```

2. Exécutez les commandes suivantes pour installer SQL Server :

   ```bash
   sudo yum install -y mssql-server
   ```

3. Une fois l'installation du package terminée, lancez **mssql-conf setup** et suivez les invites pour définir le mot de passe AS et choisir votre édition.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Les éditions suivantes de SQL Server 2017 sont sous licence libre : Evaluation, Developer et Express.

   > [!NOTE]
   > Assurez-vous de spécifier un mot de passe fort pour le compte AS (longueur minimale de 8 caractères, lettres majuscules et minuscules comprises, chiffres de la base 10 et/ou symboles non alphanumériques).

4. Une fois la configuration terminée, vérifiez que le service est en cours d'exécution :

   ```bash
   systemctl status mssql-server
   ```

5. Pour autoriser les connexions à distance, ouvrez le port SQL Server sur le pare-feu de RHEL. Le port par défaut du serveur SQL est TCP 1433. Si vous utilisez **FirewallD** pour votre pare-feu, vous pouvez utiliser les commandes suivantes :

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

À ce stade, SQL Server fonctionne sur votre machine RHEL et est prêt à l'emploi !

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="install"></a>Installer SQL Server

Pour configurer SQL Server sur RHEL, exécutez les commandes suivantes dans un terminal afin d’installer le package **mssql-server** :

1. Téléchargez la préversion du fichier config du référentiel Microsoft SQL Server 2019 preview Red Hat :

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo
   ```

2. Exécutez les commandes suivantes pour installer SQL Server :

   ```bash
   sudo yum install -y mssql-server
   ```

3. Une fois l'installation du package terminée, lancez **mssql-conf setup** et suivez les invites pour définir le mot de passe AS et choisir votre édition.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!NOTE]
   > Assurez-vous de spécifier un mot de passe fort pour le compte AS (longueur minimale de 8 caractères, lettres majuscules et minuscules comprises, chiffres de la base 10 et/ou symboles non alphanumériques).

4. Une fois la configuration terminée, vérifiez que le service est en cours d'exécution :

   ```bash
   systemctl status mssql-server
   ```

5. Pour autoriser les connexions à distance, ouvrez le port SQL Server sur le pare-feu de RHEL. Le port par défaut du serveur SQL est TCP 1433. Si vous utilisez **FirewallD** pour votre pare-feu, vous pouvez utiliser les commandes suivantes :

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

À ce stade, la préversion de SQL Server 2019 fonctionne sur votre machine RHEL et est prête à l'emploi !

::: moniker-end

## <a id="tools"></a>Installer les outils en ligne de commande SQL Server

Pour créer une base de données, vous devez vous connecter à un outil capable d’exécuter des instructions Transact-SQL sur SQL Server. Les étapes suivantes installent les outils en ligne de commande SQL Server : [sqlcmd](../tools/sqlcmd-utility.md) et [bcp](../tools/bcp-utility.md).

1. Téléchargez le fichier config du référentiel Microsoft Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```

1. Si vous aviez une version précédente de **mssql-tools** installée, supprimez tous les anciens packages unixODBC.

   ```bash
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. Exécutez les commandes suivantes pour installer **mssql-tools** avec le package pour développeur unixODBC.

   ```bash
   sudo yum install -y mssql-tools unixODBC-devel
   ```

1. Par commodité, ajoutez `/opt/mssql-tools/bin/` à votre variable d'environnement **PATH**. Vous pourrez ainsi exécuter les outils sans spécifier le chemin complet. Exécutez les commandes suivantes afin de modifier la variable **PATH** pour les sessions de connexion et les sessions interactives/sans connexion :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
