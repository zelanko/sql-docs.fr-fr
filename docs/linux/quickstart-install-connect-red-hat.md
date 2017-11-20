---
title: Prise en main 2017 du serveur SQL sur Red Hat Enterprise Linux | Documents Microsoft
description: "Ce didacticiel de démarrage rapide montre comment installer SQL Server 2017 sur Red Hat Enterprise Linux puis créer et interroger une base de données avec sqlcmd."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 92503f59-96dc-4f6a-b1b0-d135c43e935e
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 6d18cbe5b20882581afa731ce5d207cbbc69be6c
ms.openlocfilehash: d5f7a249e43619e0730da0a30fd5597788441bb8
ms.contentlocale: fr-fr
ms.lasthandoff: 10/21/2017

---
# <a name="install-sql-server-and-create-a-database-on-red-hat"></a>Installer SQL Server et de créer une base de données sur Red Hat

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Dans ce didacticiel de démarrage rapide, vous d’abord installez SQL Server 2017 sur Red Hat Enterprise Linux (RHEL) 7.3 +. Se connecter avec **sqlcmd** à créer votre première base de données et exécuter des requêtes.

> [!TIP]
> Ce didacticiel nécessite l’entrée d’utilisateur et une connexion internet. Si vous êtes intéressé par le [sans assistance](sql-server-linux-setup.md#unattended) ou [hors connexion](sql-server-linux-setup.md#offline) procédures d’installation, consultez [aide à l’Installation de SQL Server sur Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Conditions préalables

Vous devez avoir un 7.3 RHEL ou ordinateur 7.4 avec **au moins 3,25 Go** de mémoire.

Pour installer Red Hat Enterprise Linux sur votre propre ordinateur, accédez à [http://access.redhat.com/products/red-hat-enterprise-linux/evaluation](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation). Vous pouvez également créer des machines virtuelles RHEL dans Azure. Consultez [créer et gérer des machines virtuelles Linux avec l’interface CLI Azure](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)et utiliser `--image RHEL` dans l’appel à `az vm create`.

Pour les autres exigences système, consultez [configuration système requise pour SQL Server sur Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Installation de SQL Server

Pour configurer SQL Server sur RHEL, exécutez les commandes suivantes dans un Terminal Server pour installer le **mssql-serveur** package :

> [!IMPORTANT]
> Si vous avez déjà installé un CTP ou la version RC de SQL Server 2017, vous devez d’abord supprimer l’ancien référentiel avant d’inscrire un des référentiels de la disponibilité générale. Pour plus d’informations, consultez [modifier les référentiels à partir du référentiel d’aperçu dans le référentiel GA](sql-server-linux-change-repo.md).

1. Téléchargez le fichier de configuration de Microsoft SQL Server Red Hat référentiel :

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

   > [!NOTE]
   > Il s’agit de l’espace de stockage de mise à jour Cumulative (CU). Pour plus d’informations sur les options de votre référentiel et leurs différences, consultez [modifier les référentiels sources](sql-server-linux-setup.md#repositories).

1. Exécutez les commandes suivantes pour installer SQL Server :

   ```bash
   sudo yum install -y mssql-server
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
   
1. Pour autoriser les connexions à distance, ouvrez le port SQL Server sur le pare-feu sur RHEL. Le port de SQL Server par défaut est TCP 1433. Si vous utilisez **FirewallD** de votre pare-feu, vous pouvez utiliser les commandes suivantes :

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

À ce stade, SQL Server est en cours d’exécution sur votre ordinateur RHEL et est prêt à utiliser.

## <a id="tools"></a>Installer les outils de ligne de commande SQL Server

Pour créer une base de données, vous devez vous connecter avec un outil qui peut exécuter des instructions Transact-SQL sur le serveur SQL Server. Les étapes suivantes installer les outils de ligne de commande de SQL Server : [sqlcmd](../tools/sqlcmd-utility.md) et [bcp](../tools/bcp-utility.md).

1. Téléchargez le fichier de configuration du référentiel Microsoft Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```

1. Si vous aviez une version précédente de **mssql-tools** installé, supprimez tous les packages unixODBC plus anciens.

   ```bash
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. Exécutez les commandes suivantes pour installer **mssql-tools** avec le kit du développeur unixODBC.

   ```bash
   sudo yum install -y mssql-tools unixODBC-devel
   ```

1. Pour plus de commodité, ajoutez `/opt/mssql-tools/bin/` à votre **chemin d’accès** variable d’environnement. Cela vous permet d’exécuter les outils sans spécifier le chemin d’accès complet. Exécutez les commandes suivantes pour modifier la **chemin d’accès** des sessions de connexion et des sessions/non-connexion interactive :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

> [!TIP]
> **SQLCMD** est le seul outil pour la connexion à SQL Server pour exécuter des requêtes et d’effectuer les tâches de gestion et de développement. Incluent d’autres outils [SQL Server Management Studio](sql-server-linux-develop-use-ssms.md) et [Visual Studio Code](sql-server-linux-develop-use-vscode.md).

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]

