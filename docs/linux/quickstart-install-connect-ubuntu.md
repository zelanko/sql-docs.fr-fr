---
title: 'Ubuntu : Installer SQL Server sur Linux'
description: Ce démarrage rapide montre comment installer SQL Server 2017 ou SQL Server 2019 sur Ubuntu, puis comment créer et interroger une base de données avec sqlcmd.
author: VanMSFT
ms.author: vanto
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: seo-lt-2019
ms.technology: linux
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.openlocfilehash: df3609c5bf4f31ee8a32992127681d42609b9528
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "75558419"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-ubuntu"></a>Démarrage rapide : Installer SQL Server et créer une base de données sur Ubuntu
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]


<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Dans ce guide de démarrage rapide, vous installez SQL Server 2017 ou SQL Server 2019 sur Ubuntu 16.04. Ensuite, vous vous connectez avec **sqlcmd** pour créer votre première base de données et exécuter des requêtes.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Dans ce guide de démarrage rapide, vous installez SQL Server 2019 sur Ubuntu 16.04. Ensuite, vous vous connectez avec **sqlcmd** pour créer votre première base de données et exécuter des requêtes.

::: moniker-end

> [!TIP]
> Ce tutoriel nécessite l'intervention de l'utilisateur et une connexion Internet. Si vous êtes intéressé par les procédures d'installation sans assistance ou hors ligne, voir [Conseils d’installation pour SQL Server sur Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Conditions préalables requises

Vous devez disposer d’une machine Ubuntu 16.04 avec **au moins 2 Go** de mémoire.

Pour installer Ubuntu 16.04 sur votre propre machine, allez à [http://releases.ubuntu.com/xenial/](http://releases.ubuntu.com/xenial/). Vous pouvez également créer des machines virtuelles Ubuntu dans Azure. Voir [Créer et gérer des machines virtuelles Linux avec l’interface Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm).

> [!NOTE]
> Pour le moment, le [sous-système Windows pour Linux](https://msdn.microsoft.com/commandline/wsl/about) pour Windows 10 n'est pas pris en charge comme cible d'installation.

Pour les autres configurations système requises, voir [Configuration système requise pour SQL Server sur Linux](sql-server-linux-setup.md#system).

> [!NOTE]
> Ubuntu 18.04 n’est pas encore officiellement pris en charge, mais l’exécution de SQL Server est possible avec des [modifications](https://blogs.msdn.microsoft.com/sql_server_team/installing-sql-server-2017-for-linux-on-ubuntu-18-04-lts/).

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="install"></a>Installer SQL Server

Pour configurer SQL Server sur Ubuntu, exécutez les commandes suivantes dans un terminal afin d’installer le package **mssql-server**.

1. Importez les clés GPG de dépôt public :

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Enregistrez le référentiel Microsoft SQL Server Ubuntu :

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

   > [!TIP]
   > Si vous voulez tester SQL Server 2019, vous devez inscrire à la place le référentiel SQL Server 2019. Utilisez la commande suivante pour les installations SQL Server 2019 :
   >
   > ```bash
   > sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2019.list)"
   > ```

3. Exécutez les commandes suivantes pour installer SQL Server :

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
   ```

4. Une fois l'installation du package terminée, lancez **mssql-conf setup** et suivez les invites pour définir le mot de passe AS et choisir votre édition.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Les éditions suivantes de SQL Server 2017 sont sous licence libre : Evaluation, Developer et Express.

   > [!NOTE]
   > Assurez-vous de spécifier un mot de passe fort pour le compte AS (longueur minimale de 8 caractères, lettres majuscules et minuscules comprises, chiffres de la base 10 et/ou symboles non alphanumériques).

5. Une fois la configuration terminée, vérifiez que le service est en cours d'exécution :

   ```bash
   systemctl status mssql-server --no-pager
   ```

6. Si vous prévoyez de vous connecter à distance, vous devrez peut-être aussi ouvrir le port TCP de SQL Server (par défaut 1433) sur votre pare-feu.

À ce stade, SQL Server fonctionne sur votre machine Ubuntu et est prêt à l'emploi !

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="install"></a>Installer SQL Server

Pour configurer SQL Server sur Ubuntu, exécutez les commandes suivantes dans un terminal afin d’installer le package **mssql-server**.

1. Importez les clés GPG de dépôt public :

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Inscrivez le référentiel Microsoft SQL Server Ubuntu pour SQL Server 2019 :

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2019.list)"
   ```

3. Exécutez les commandes suivantes pour installer SQL Server :

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
   ```

4. Une fois l'installation du package terminée, lancez **mssql-conf setup** et suivez les invites pour définir le mot de passe AS et choisir votre édition.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!NOTE]
   > Assurez-vous de spécifier un mot de passe fort pour le compte AS (longueur minimale de 8 caractères, lettres majuscules et minuscules comprises, chiffres de la base 10 et/ou symboles non alphanumériques).

5. Une fois la configuration terminée, vérifiez que le service est en cours d'exécution :

   ```bash
   systemctl status mssql-server --no-pager
   ```

6. Si vous prévoyez de vous connecter à distance, vous devrez peut-être aussi ouvrir le port TCP de SQL Server (par défaut 1433) sur votre pare-feu.

À ce stade, SQL Server 2019 fonctionne sur votre machine Ubuntu et est prêt à l’emploi !

::: moniker-end

## <a id="tools"></a>Installer les outils en ligne de commande SQL Server

Pour créer une base de données, vous devez vous connecter à un outil capable d’exécuter des instructions Transact-SQL sur SQL Server. Les étapes suivantes installent les outils en ligne de commande SQL Server : [sqlcmd](../tools/sqlcmd-utility.md) et [bcp](../tools/bcp-utility.md).

Suivez les étapes suivantes pour installer **mssql-tools** sur Ubuntu. 

1. Importez les clés GPG de référentiel public.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Enregistrez le référentiel Microsoft Ubuntu.

   ```bash
   curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
   ```

1. Mettez à jour la liste des sources et exécutez la commande d'installation avec le package pour développeur unixODBC.

   ```bash
   sudo apt-get update 
   sudo apt-get install mssql-tools unixodbc-dev
   ```

   > [!Note] 
   > Pour mettre à jour vers la dernière version de **mssql-tools**, exécutez les commandes suivantes :
   >    ```bash
   >   sudo apt-get update 
   >   sudo apt-get install mssql-tools 
   >   ```

1. **Facultatif** : Ajoutez `/opt/mssql-tools/bin/` à votre variable d'environnement **PATH** dans un interpréteur de commandes Bash.

   Afin de rendre **sqlcmd/bcp** accessible depuis l’interpréteur de commandes Bash pour les sessions de connexion, modifiez votre **PATH** dans le fichier **~/.bash_profile** à l’aide de la commande suivante :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Afin de rendre **sqlcmd/bcp** accessible depuis l’interpréteur de commandes Bash pour les sessions interactives/sans connexion, modifiez le **PATH** dans le fichier **~/.bashrc** à l’aide de la commande suivante :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
