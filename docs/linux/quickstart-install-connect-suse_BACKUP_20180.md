---
title: Prise en main 2017 du serveur SQL sur SUSE Linux Enterprise Server | Documents Microsoft
description: "Ce démarrage rapide montre comment installer SQL Server 2017 sur SUSE Linux Enterprise Server puis créer et interroger une base de données avec sqlcmd."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/22/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 31ddfb80-f75c-4f51-8540-de6213cb68b8
ms.workload: On Demand
ms.openlocfilehash: e1690120790be2de70ddd19aa3c1c4893178cb08
ms.sourcegitcommit: f0c5e37c138be5fb2cbb93e9f2ded307665b54ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2018
<<<<<<< HEAD
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-suse-linux-enterprise-server"></a>Démarrage rapide : Installer SQL Server et créer une base de données sur SUSE Linux Enterprise Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dans ce guide de démarrage rapide, vous installez d’abord SQL Server 2017 sur SUSE Linux Enterprise Server (SLES) v12 SP2. Ensuite, vous vous connectez avec **sqlcmd** pour créer votre première base de données et exécuter des requêtes.

> [!TIP]
> Ce didacticiel nécessite une saisie de la part de l’utilisateur et une connexion Internet. Si vous êtes intéressé par les procédures d'installation [sans assistance](sql-server-linux-setup.md#unattended) ou [hors connexion](sql-server-linux-setup.md#offline), consultez [Aide à l’installation de SQL Server sur Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Configuration requise

Vous devez disposer d’un ordinateur SP2 SLES v12 avec **au moins 3,25 Go** de mémoire. Le système de fichiers doit être **XFS** ou **EXT4**. D'autres systèmes de fichiers tels que **BTRFS**, ne sont pas pris en charge.

Pour installer SUSE Linux Enterprise Server sur votre propre ordinateur, accédez à [https://www.suse.com/products/server](https://www.suse.com/products/server). Vous pouvez également créer des machines virtuelles SLES dans Azure. Consultez [créer et gérer des machines virtuelles Linux avec l’interface CLI Azure](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)et utiliser `--image SLES` dans l’appel à `az vm create`.

> [!NOTE]
> À ce stade, le [sous-système Windows pour Linux](https://msdn.microsoft.com/commandline/wsl/about) pour Windows 10 n’est pas pris en charge comme cible d’installation.

Pour les autres exigences système, consultez [configuration système requise pour SQL Server sur Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Installation de SQL Server

Pour configurer SQL Server sur SLES, exécutez les commandes suivantes dans un terminal pour installer le package **mssql-serveur** :

> [!IMPORTANT]
> Si vous avez déjà installé une version CTP ou RC de SQL Server 2017, vous devez d’abord supprimer l’ancien référentiel avant d’inscrire l'un des référentiels à disponibilité générale (GA). Pour plus d’informations, consultez [passer du référentiel de préversion au référentiel à disponibilité générale](sql-server-linux-change-repo.md).

1. Téléchargez le fichier de configuration du référentiel de Microsoft SQL Server SLES :

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
   ```

   > [!NOTE]
   > Il s’agit du référentiel de mise à jour cumulative (CU). Pour plus d’informations sur les options de votre référentiel et leurs différences, consultez [modifier les référentiels sources](sql-server-linux-change-repo.md).

1. Actualiser vos référentiels.

   ```bash
   sudo zypper --gpg-auto-import-keys refresh 
   ```
   
1. Exécutez les commandes suivantes pour installer SQL Server :

   ```bash
   sudo zypper install -y mssql-server
   ```

1. Après la fin de l’installation du package, exécutez le programme d’installation **mssql-conf** et suivez les invites pour définir le mot de passe SA et choisir votre édition.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Si vous testez SQL Server 2017 avec ce didacticiel, les éditions suivantes sont concédées librement sous licence  : Evaluation, Developer et Express.

   > [!NOTE]
   > Veillez à spécifier un mot de passe fort pour le compte d’administrateur système (longueur minimum 8 caractères, incluant des majuscules et des minuscules, des chiffres et/ou des caractères spéciaux).

1. Une fois la configuration terminée, vérifiez que le service est en cours d’exécution :

   ```bash
   systemctl status mssql-server
   ```

1. Si vous envisagez de vous connecter à distance, vous devrez peut-être également ouvrir le port TCP du serveur SQL (1433 par défaut) sur votre pare-feu. Si vous utilisez le pare-feu SuSE, vous devez modifier le fichier de configuration **/etc/sysconfig/SuSEfirewall2**. Modifiez l'entrée **FW_SERVICES_EXT_TCP** pour inclure le numéro de port SQL Server.

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

À ce stade, SQL Server est en cours d’exécution sur votre ordinateur SLES et est prêt à être utilisé.

## <a id="tools"></a>Installer les outils de ligne de commande SQL Server

Pour créer une base de données, vous devez vous connecter avec un outil qui peut exécuter des instructions Transact-SQL sur le serveur SQL Server. Les étapes suivantes permettent d'installer les outils de ligne de commande de SQL Server : [sqlcmd](../tools/sqlcmd-utility.md) et [bcp](../tools/bcp-utility.md).

1. Ajoutez le référentiel Microsoft SQL Server à Zypper.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. Installer **mssql-tools** avec le kit du développeur unixODBC.

   ```bash
   sudo zypper install -y mssql-tools unixODBC-devel
   ```

1. Pour plus de commodité, ajoutez `/opt/mssql-tools/bin/` à votre variable d'environnement de **chemin d’accès**. Cela vous permet d’exécuter les outils sans spécifier le chemin d’accès complet. Exécutez les commandes suivantes pour modifier le **chemin d’accès** pour les sessions interactives avec et sans connexion :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

> [!TIP]
> **SQLCMD** est un outil unique pour se connecter à SQL Server afin d'exécuter des requêtes et d'effectuer les tâches de gestion et de développement. D'autres outils incluent :
>
> * [SQL Server Operations Studio (préversion)](../sql-operations-studio/what-is.md)
> * [SQL Server Management Studio](sql-server-linux-develop-use-ssms.md)
> * [Visual Studio Code](sql-server-linux-develop-use-vscode.md).
> * [mssql-cli (préversion)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
||||||| merged common ancestors
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-suse-linux-enterprise-server"></a>Démarrage rapide : Installer SQL Server et de créer une base de données sur SUSE Linux Enterprise Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ce guide de démarrage rapide, vous d’abord installez SQL Server 2017 sur SUSE Linux Enterprise Server (SLES) v12 SP2. Ensuite, vous vous connectez avec **sqlcmd** pour créer votre première base de données et exécuter des requêtes.

> [!TIP]
> Ce didacticiel nécessite l’entrée d’utilisateur et une connexion internet. Si vous êtes intéressé par le [sans assistance](sql-server-linux-setup.md#unattended) ou [hors connexion](sql-server-linux-setup.md#offline) procédures d’installation, consultez [aide à l’Installation de SQL Server sur Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Configuration requise

Vous devez disposer d’un ordinateur de SP2 SLES v12 avec **au moins 2 Go** de mémoire. Le système de fichiers doit être **XFS** ou **EXT4**. Autres systèmes de fichiers, tel que **BTRFS**, non pris en charge.

Pour installer SUSE Linux Enterprise Server sur votre propre ordinateur, accédez à [https://www.suse.com/products/server](https://www.suse.com/products/server). Vous pouvez également créer des machines virtuelles SLES dans Azure. Consultez [créer et gérer des machines virtuelles Linux avec l’interface CLI Azure](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)et utiliser `--image SLES` dans l’appel à `az vm create`.

> [!NOTE]
> À ce stade, le [sous-système Windows pour Linux](https://msdn.microsoft.com/commandline/wsl/about) pour Windows 10 n’est pas prise en charge comme cible d’installation.

Pour les autres exigences système, consultez [configuration système requise pour SQL Server sur Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Installation de SQL Server

Pour configurer SQL Server sur SLES, exécutez les commandes suivantes dans un Terminal Server pour installer le **mssql-serveur** package :

> [!IMPORTANT]
> Si vous avez déjà installé un CTP ou la version RC de SQL Server 2017, vous devez d’abord supprimer l’ancien référentiel avant d’inscrire un des référentiels de la disponibilité générale. Pour plus d’informations, consultez [modifier les référentiels à partir du référentiel d’aperçu dans le référentiel GA](sql-server-linux-change-repo.md).

1. Téléchargez le fichier de configuration de Microsoft SQL Server SLES référentiel :

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
   ```

   > [!NOTE]
   > Il s’agit de l’espace de stockage de mise à jour Cumulative (CU). Pour plus d’informations sur les options de votre référentiel et leurs différences, consultez [configurer des référentiels pour SQL Server sur Linux](sql-server-linux-change-repo.md).

1. Actualiser vos référentiels.

   ```bash
   sudo zypper --gpg-auto-import-keys refresh 
   ```
   
1. Exécutez les commandes suivantes pour installer SQL Server :

   ```bash
   sudo zypper install -y mssql-server
   ```

1. Après la fin de l’installation package, exécutez **le programme d’installation de mssql-conf** et suivez les invites pour définir le mot de passe SA et choisissez votre édition.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Si vous essayez de SQL Server 2017 dans ce didacticiel, les éditions suivantes sont concédés sous licence librement : Evaluation, Developer et Express.

   > [!NOTE]
   > Veillez à spécifier un mot de passe fort pour le compte d’administrateur système (Minimum longueur 8 caractères, y compris les majuscules et minuscules, chiffres en base 10 et/ou des symboles non alphanumériques).

1. Une fois la configuration terminée, vérifiez que le service est en cours d’exécution :

   ```bash
   systemctl status mssql-server
   ```

1. Si vous envisagez de vous connecter à distance, vous devrez peut-être également ouvrir le port TCP du serveur SQL (1433 par défaut) sur votre pare-feu. Si vous utilisez le pare-feu SuSE, vous devez modifier le **/etc/sysconfig/SuSEfirewall2** fichier de configuration. Modifier la **FW_SERVICES_EXT_TCP** entrée à inclure le numéro de port SQL Server.

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

À ce stade, SQL Server est en cours d’exécution sur votre ordinateur SLES et est prêt à utiliser.

## <a id="tools"></a>Installer les outils de ligne de commande SQL Server

Pour créer une base de données, vous devez vous connecter avec un outil qui peut exécuter des instructions Transact-SQL sur le serveur SQL Server. Les étapes suivantes installer les outils de ligne de commande de SQL Server : [sqlcmd](../tools/sqlcmd-utility.md) et [bcp](../tools/bcp-utility.md).

1. Ajoutez le référentiel Microsoft SQL Server à Zypper.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. Installer **mssql-tools** avec le kit du développeur unixODBC.

   ```bash
   sudo zypper install -y mssql-tools unixODBC-devel
   ```

1. Pour plus de commodité, ajoutez `/opt/mssql-tools/bin/` à votre **chemin d’accès** variable d’environnement. Cela vous permet d’exécuter les outils sans spécifier le chemin d’accès complet. Exécutez les commandes suivantes pour modifier la **chemin d’accès** des sessions de connexion et des sessions/non-connexion interactive :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

> [!TIP]
> **SQLCMD** est le seul outil pour la connexion à SQL Server pour exécuter des requêtes et d’effectuer les tâches de gestion et de développement. Autres outils incluent :
>
> * [SQL Server Operations Studio (préversion)](../sql-operations-studio/what-is.md)
> * [SQL Server Management Studio](sql-server-linux-develop-use-ssms.md)
> * [Code Visual Studio](sql-server-linux-develop-use-vscode.md).
> * [mssql-cli (préversion)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
=======
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-suse-linux-enterprise-server"></a>Démarrage rapide : Installer SQL Server et de créer une base de données sur SUSE Linux Enterprise Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ce guide de démarrage rapide, vous d’abord installez SQL Server 2017 sur SUSE Linux Enterprise Server (SLES) v12 SP2. Ensuite, vous vous connectez avec **sqlcmd** pour créer votre première base de données et exécuter des requêtes.

> [!TIP]
> Ce didacticiel nécessite une saisie de la part de l’utilisateur et une connexion Internet. Si vous êtes intéressé par les procédures d'installation [sans assistance](sql-server-linux-setup.md#unattended) ou [hors connexion](sql-server-linux-setup.md#offline), consultez [Aide à l’installation de SQL Server sur Linux](sql-server-linux-setup.md). 

## <a name="prerequisites"></a>Configuration requise

Vous devez disposer d’un ordinateur de SP2 SLES v12 avec **au moins 2 Go** de mémoire. Le système de fichiers doit être **XFS** ou **EXT4**. Autres systèmes de fichiers, tel que **BTRFS**, non pris en charge.

Pour installer SUSE Linux Enterprise Server sur votre propre ordinateur, accédez à [https://www.suse.com/products/server](https://www.suse.com/products/server). Vous pouvez également créer des machines virtuelles SLES dans Azure. Consultez [créer et gérer des machines virtuelles Linux avec l’interface CLI Azure](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)et utiliser `--image SLES` dans l’appel à `az vm create`.

> [!NOTE]
> À ce stade, le [sous-système Windows pour Linux](https://msdn.microsoft.com/commandline/wsl/about) pour Windows 10 n’est pas pris en charge comme cible d’installation.

Pour les autres exigences système, consultez [configuration système requise pour SQL Server sur Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Installation de SQL Server

Pour configurer SQL Server sur SLES, exécutez les commandes suivantes dans un terminal pour installer le package **mssql-server** :

> [!IMPORTANT]
> Si vous avez déjà installé une version CTP ou RC de SQL Server 2017, vous devez d’abord supprimer l’ancien référentiel avant d’inscrire l'un des référentiels à disponibilité générale (GA). Pour plus d’informations, consultez [passer du référentiel de préversion au référentiel à disponibilité générale](sql-server-linux-change-repo.md).

1. Téléchargez le fichier de configuration du référentiel de Microsoft SQL Server SLES :

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
   ```

   > [!NOTE]
   > Il s’agit de l’espace de stockage de mise à jour Cumulative (CU). Pour plus d’informations sur les options de votre référentiel et leurs différences, consultez [configurer des référentiels pour SQL Server sur Linux](sql-server-linux-change-repo.md).

1. Actualiser vos référentiels.

   ```bash
   sudo zypper --gpg-auto-import-keys refresh 
   ```
   
1. Exécutez les commandes suivantes pour installer SQL Server :

   ```bash
   sudo zypper install -y mssql-server
   ```

1. Après la fin de l’installation du package, exécutez le programme d’installation **mssql-conf** et suivez les invites pour définir le mot de passe SA et choisir votre édition. 

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Si vous testez SQL Server 2017 avec ce didacticiel, les éditions suivantes sont concédées librement sous licence  : Evaluation, Developer et Express.

   > [!NOTE]
   > Veillez à spécifier un mot de passe fort pour le compte d’administrateur système (longueur minimum 8 caractères, incluant des majuscules et des minuscules, des chiffres et/ou des caractères spéciaux). 

1. Une fois la configuration terminée, vérifiez que le service est en cours d’exécution :

   ```bash
   systemctl status mssql-server
   ```

1. Si vous envisagez de vous connecter à distance, vous devrez peut-être également ouvrir le port TCP du serveur SQL (1433 par défaut) sur votre pare-feu. Si vous utilisez le pare-feu SuSE, vous devez modifier le fichier de configuration **/etc/sysconfig/SuSEfirewall2**. Modifiez l'entrée **FW_SERVICES_EXT_TCP** pour inclure le numéro de port SQL Server. 

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

À ce stade, SQL Server est en cours d’exécution sur votre ordinateur SLES et est prêt à être utilisé.

## <a id="tools"></a>Installer les outils de ligne de commande SQL Server

Pour créer une base de données, vous devez vous connecter avec un outil qui peut exécuter des instructions Transact-SQL sur le serveur SQL Server. Les étapes suivantes permettent d'installer les outils de ligne de commande de SQL Server : [sqlcmd](../tools/sqlcmd-utility.md) et [bcp](../tools/bcp-utility.md).

1. Ajoutez le référentiel Microsoft SQL Server à Zypper.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. Installer **mssql-tools** avec le kit du développeur unixODBC.

   ```bash
   sudo zypper install -y mssql-tools unixODBC-devel
   ```

1. Pour plus de commodité, ajoutez `/opt/mssql-tools/bin/` à votre variable d'environnement de **chemin d’accès**. Cela vous permet d’exécuter les outils sans spécifier le chemin d’accès complet. Exécutez les commandes suivantes pour modifier le **chemin d’accès** pour les sessions interactives avec et sans connexion : 

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

> [!TIP]
> **SQLCMD** est le seul outil pour la connexion à SQL Server pour exécuter des requêtes et d’effectuer les tâches de gestion et de développement. Autres outils incluent :
>
> * [SQL Server Operations Studio (préversion)](../sql-operations-studio/what-is.md)
> * [SQL Server Management Studio](sql-server-linux-develop-use-ssms.md)
> * [Code Visual Studio](sql-server-linux-develop-use-vscode.md).
> * [mssql-cli (préversion)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
>>>>>>> live
