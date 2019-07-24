---
title: Options de configuration pour SQL Server sur l’arrimeur
description: Explorez les différentes façons d’utiliser et d’interagir avec les images de conteneur SQL Server 2017 et 2019 Preview dans docker. Cela comprend la conservation des données, la copie des fichiers et le dépannage.
author: vin-yu
ms.author: vinsonyu
ms.reviewer: vanto
ms.date: 01/17/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: d24bb3566195c71a3b62d16fab867ab5085404b7
ms.sourcegitcommit: d667fa9d6f1c8035f15fdb861882bd514be020d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68388378"
---
# <a name="configure-sql-server-container-images-on-docker"></a>Configurer SQL Server images de conteneur sur l’ancrage

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article explique comment configurer et utiliser l' [image de conteneur MSSQL-Server-Linux](https://hub.docker.com/_/microsoft-mssql-server) avec l’Assistant d’ancrage. Cette image est composée de SQL Server s’exécutant sur Linux basé sur Ubuntu 16.04. Elle peut être utilisée avec Docker Engine 1.8+ sur Linux ou sur Docker pour Mac/Windows.

> [!NOTE]
> Cet article se concentre spécifiquement sur l’utilisation de l’image MSSQL-Server-Linux. L’image Windows n’est pas couverte, mais vous pouvez en savoir plus à ce sujet sur la [page MSSQL-Server-Windows dockr Hub](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/).

## <a name="pull-and-run-the-container-image"></a>Extraire et exécuter l’image conteneur

Pour extraire et exécuter les images de conteneur d’ancrage pour SQL Server 2017 et SQL Server 2019 Preview, suivez les conditions préalables et les étapes décrites dans le Guide de démarrage rapide suivant:

- [Exécuter l’image de conteneur SQL Server 2017 avec l’ancrage](quickstart-install-connect-docker.md?view=sql-server-2017)
- [Exécuter l’image de conteneur SQL Server 2019 preview avec l’ancrage](quickstart-install-connect-docker.md?view=sql-server-ver15)

Cet article de configuration fournit des scénarios d’utilisation supplémentaires dans les sections suivantes.

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="rhel"></a>Exécuter des images de conteneur RHEL

Toute la documentation sur SQL Server images de conteneur Linux pointent vers des conteneurs Ubuntu. À partir de SQL Server version préliminaire 2019, vous pouvez utiliser des conteneurs basés sur Red Hat Enterprise Linux (RHEL). Remplacez le référentiel de conteneurs **MCR.Microsoft.com/MSSQL/Server:2019-CTP3.1-Ubuntu** par **MCR.Microsoft.com/MSSQL/RHEL/Server:2019-CTP3.1** dans toutes les commandes de l’ancrage.

Par exemple, la commande suivante extrait le dernier conteneur SQL Server 2019 Preview qui utilise RHEL:

```bash
sudo docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP3.1
```

```PowerShell
docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP3.1
```

::: moniker-end

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="production"></a>Exécuter des images de conteneur de production

Le Guide de démarrage rapide de la section précédente exécute la version gratuite de l’édition Developer de SQL Server à partir du Hub Dockr. La plupart des informations s’appliquent toujours si vous souhaitez exécuter des images de conteneur de production, telles que des éditions Enterprise, standard ou Web. Toutefois, il existe quelques différences qui sont décrites ici.

- Vous ne pouvez utiliser SQL Server dans un environnement de production que si vous disposez d’une licence valide. Vous pouvez vous procurer gratuitement [une licence de](https://go.microsoft.com/fwlink/?linkid=857693)production SQL Server Express. Les licences SQL Server Standard et Enterprise Edition sont disponibles via le programme de [licence en volume Microsoft](https://www.microsoft.com/licensing/default.aspx).


- L’image de conteneur du développeur peut également être configurée pour exécuter les éditions de production. Procédez comme suit pour exécuter les éditions de production:

Passez en revue les conditions requises et exécutez les procédures dans le Guide de [démarrage rapide](quickstart-install-connect-docker.md). Vous devez spécifier votre édition de production avec la variable d’environnement **MSSQL_PID** . L’exemple suivant montre comment exécuter la dernière image de conteneur SQL Server 2017 pour l’édition Enterprise:

```bash
docker run --name sqlenterprise \
      -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
      -e 'MSSQL_PID=Enterprise' -p 1433:1433 \
      -d store/microsoft/mssql-server-linux:2017-latest
```

```PowerShell
docker run --name sqlenterprise `
      -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
      -e "MSSQL_PID=Enterprise" -p 1433:1433 `
      -d "store/microsoft/mssql-server-linux:2017-latest"
 ```

> [!IMPORTANT]
> En passant la valeur **Y** à la variable d’environnement **ACCEPT_EULA** et une valeur d’édition à **MSSQL_PID**, vous exposez que vous disposez d’une licence valide et existante pour l’édition et la version de SQL Server que vous prévoyez d’utiliser. Vous acceptez également que votre utilisation de SQL Server logiciel s’exécutant dans une image de conteneur d’ancrage sera régie par les termes de votre licence SQL Server.

> [!NOTE]
> Pour obtenir la liste complète des valeurs possibles pour **MSSQL_PID**, consultez [configurer les paramètres de SQL Server avec des variables d’environnement sur Linux](sql-server-linux-configure-environment-variables.md).

::: moniker-end

## <a name="connect-and-query"></a>Se connecter et interroger

Vous pouvez vous connecter et interroger SQL Server dans un conteneur à partir de l’extérieur du conteneur ou à partir du conteneur. Les sections suivantes expliquent les deux scénarios. 

### <a name="tools-outside-the-container"></a>Outils en dehors du conteneur

Vous pouvez vous connecter à l’instance SQL Server sur votre machine Dockr à partir d’un outil Linux, Windows ou macOS externe qui prend en charge les connexions SQL. Certains outils courants sont les suivants:

- [sqlcmd](sql-server-linux-setup-tools.md)
- [Visual Studio Code](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) sur Windows](sql-server-linux-manage-ssms.md)

L’exemple suivant utilise **sqlcmd** pour se connecter à SQL Server s’exécutant dans un conteneur d’ancrage. L’adresse IP dans la chaîne de connexion est l’adresse IP de l’ordinateur hôte qui exécute le conteneur.

```bash
sqlcmd -S 10.3.2.4 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4 -U SA -P "<YourPassword>"
```

Si vous avez mappé un port hôte qui n’est pas le **1433**par défaut, ajoutez ce port à la chaîne de connexion. Par exemple, si vous avez `-p 1400:1433` spécifié dans `docker run` votre commande, connectez-vous en spécifiant explicitement le port 1400.

```bash
sqlcmd -S 10.3.2.4,1400 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1400 -U SA -P "<YourPassword>"
```

### <a name="tools-inside-the-container"></a>Outils à l’intérieur du conteneur

À partir de SQL Server version préliminaire 2017, les [outils en ligne de commande SQL Server](sql-server-linux-setup-tools.md) sont inclus dans l’image de conteneur. Si vous vous attachez à l’image avec une invite de commandes interactive, vous pouvez exécuter les outils localement.

1. Utilisez la commande `docker exec -it` pour démarrer un interpréteur de commandes bash interactif dans votre conteneur en cours d’exécution. Dans l’exemple `e69e056c702d` suivant, il s’agit de l’ID de conteneur.

    ```bash
    docker exec -it e69e056c702d "bash"
    ```

    > [!TIP]
    > Vous n’avez pas toujours besoin de spécifier l’ID de conteneur entier. Vous ne devez spécifier que suffisamment de caractères pour l’identifier de manière unique. Ainsi, dans cet exemple, il peut suffire d' `e6` utiliser `e69` ou plutôt que l’ID complet.

2. Une fois dans le conteneur, connectez-vous localement avec sqlcmd. Notez que sqlcmd n’est pas dans le chemin d’accès par défaut. vous devez donc spécifier le chemin d’accès complet.

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
    ```

3. Lorsque vous avez terminé avec sqlcmd `exit`, tapez.

4. Lorsque vous avez terminé avec l’invite de commandes interactive `exit`, tapez. Le conteneur continue de s’exécuter une fois que vous avez quitté l’interpréteur de commandes bash interactif.

## <a name="run-multiple-sql-server-containers"></a>Exécuter plusieurs conteneurs de SQL Server

L’outil d’ancrage offre un moyen d’exécuter plusieurs conteneurs de SQL Server sur le même ordinateur hôte. Il s’agit de l’approche pour les scénarios qui requièrent plusieurs instances de SQL Server sur le même hôte. Chaque conteneur doit s’exposer lui-même sur un port différent.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

L’exemple suivant crée deux conteneurs SQL Server 2017 et les mappe aux ports **1401** et **1402** sur l’ordinateur hôte.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:2017-latest
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:2017-latest
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

L’exemple suivant crée deux conteneurs SQL Server 2019 Preview et les mappe aux ports **1401** et **1402** sur l’ordinateur hôte.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

::: moniker-end

Il existe maintenant deux instances de SQL Server s’exécutant dans des conteneurs distincts. Les clients peuvent se connecter à chaque instance de SQL Server à l’aide de l’adresse IP de l’hôte de l’ordinateur de la station d’accueil et du numéro de port du conteneur.

```bash
sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
sqlcmd -S 10.3.2.4,1402 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
sqlcmd -S 10.3.2.4,1402 -U SA -P "<YourPassword>"
```

## <a id="customcontainer"></a>Créer un conteneur personnalisé

Il est possible de créer votre propre [fichier dockerfile](https://docs.docker.com/engine/reference/builder/#usage) pour créer un conteneur de SQL Server personnalisé. Pour plus d’informations, consultez [une démonstration qui associe SQL Server et une application de nœud](https://github.com/twright-msft/mssql-node-docker-demo-app). Si vous créez votre propre fichier dockerfile, tenez compte du processus de premier plan, car ce processus contrôle la durée de vie du conteneur. Si elle se termine, le conteneur s’arrête. Par exemple, si vous souhaitez exécuter un script et démarrer SQL Server, assurez-vous que le processus de SQL Server est la commande la plus à droite. Toutes les autres commandes sont exécutées en arrière-plan. Cela est illustré dans la commande suivante à l’intérieur d’un fichier dockerfile:

```bash
/usr/src/app/do-my-sql-commands.sh & /opt/mssql/bin/sqlservr
```

Si vous avez inversé les commandes dans l’exemple précédent, le conteneur s’arrêtera à la fin du script do-my-sql-commands.sh.

## <a id="persist"></a>Rendre vos données persistantes

Vos modifications de configuration et fichiers de base de données SQL Server sont conservés dans le conteneur même si vous redémarrez le conteneur avec `docker stop` et. `docker start` Toutefois, si vous supprimez le conteneur `docker rm`avec, tout ce qui se trouve dans le conteneur est supprimé, y compris SQL Server et vos bases de données. La section suivante explique comment utiliser des **volumes de données** pour conserver les fichiers de votre base de données, même si les conteneurs associés sont supprimés.

> [!IMPORTANT]
> Par SQL Server, il est essentiel que vous compreniez la persistance des données dans l’ancrage. En plus de la description de cette section, consultez la documentation de l’ancrage pour [savoir comment gérer les données dans les conteneurs de l’ancrage](https://docs.docker.com/engine/tutorials/dockervolumes/).

### <a name="mount-a-host-directory-as-data-volume"></a>Monter un répertoire hôte en tant que volume de données

La première option consiste à monter un répertoire sur votre hôte en tant que volume de données dans votre conteneur. Pour ce faire, utilisez la `docker run` commande avec l' `-v <host directory>:/var/opt/mssql` indicateur. Cela permet de restaurer les données entre les exécutions de conteneur.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

::: moniker-end

Cette technique vous permet également de partager et d’afficher les fichiers sur l’ordinateur hôte en dehors de l’arrimeur.

> [!IMPORTANT]
> Le mappage du volume hôte pour l’ancrage sur Mac avec l’image SQL Server sur Linux n’est pas pris en charge pour l’instant. Utilisez à la place des conteneurs de volume de données. Cette restriction est spécifique au `/var/opt/mssql` répertoire. La lecture à partir d’un répertoire monté fonctionne bien. Par exemple, vous pouvez monter un répertoire hôte à l’aide de-v sur Mac et restaurer une sauvegarde à partir d’un fichier. bak résidant sur l’ordinateur hôte.

### <a name="use-data-volume-containers"></a>Utiliser des conteneurs de volume de données

La deuxième option consiste à utiliser un conteneur de volume de données. Vous pouvez créer un conteneur de volume de données en spécifiant un nom de volume à la place `-v` d’un répertoire hôte avec le paramètre. L’exemple suivant crée un volume de données partagé nommé **sqlvolume**.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```
::: moniker-end

> [!NOTE]
> Cette technique pour la création implicite d’un volume de données dans la commande Run ne fonctionne pas avec les versions antérieures de Dockr. Dans ce cas, utilisez les étapes explicites décrites dans la documentation de l’ancrage, [création et montage d’un conteneur de volume de données](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container).

Même si vous arrêtez et supprimez ce conteneur, le volume de données persiste. Vous pouvez l’afficher avec la `docker volume ls` commande.

```bash
docker volume ls
```

Si vous créez ensuite un autre conteneur avec le même nom de volume, le nouveau conteneur utilise le même SQL Server données contenues dans le volume.

Pour supprimer un conteneur de volume de données, `docker volume rm` utilisez la commande.

> [!WARNING]
> Si vous supprimez le conteneur de volume de données, toutes les données de SQL Server dans le conteneur sont *définitivement* supprimées.

### <a name="backup-and-restore"></a>Sauvegarde et restauration

Outre ces techniques de conteneur, vous pouvez également utiliser des techniques de sauvegarde et de restauration SQL Server standard. Vous pouvez utiliser des fichiers de sauvegarde pour protéger vos données ou déplacer les données vers une autre instance de SQL Server. Pour plus d’informations, consultez [sauvegarder et restaurer des bases de données SQL Server sur Linux](sql-server-linux-backup-and-restore-database.md).

> [!WARNING]
> Si vous créez des sauvegardes, assurez-vous de créer ou de copier les fichiers de sauvegarde en dehors du conteneur. Dans le cas contraire, si le conteneur est supprimé, les fichiers de sauvegarde sont également supprimés.

## <a name="execute-commands-in-a-container"></a>Exécuter des commandes dans un conteneur

Si vous disposez d’un conteneur en cours d’exécution, vous pouvez exécuter des commandes dans le conteneur à partir d’un terminal hôte.

Pour récupérer l’ID de conteneur, exécutez:

```bash
docker ps
```

Pour démarrer un terminal bash dans le conteneur, exécutez:

```bash
docker exec -it <Container ID> /bin/bash
```

Vous pouvez maintenant exécuter des commandes comme si vous les exécutiez sur le terminal à l’intérieur du conteneur. Quand vous avez terminé, tapez `exit`. Cela se termine dans la session de commande interactive, mais votre conteneur continue à s’exécuter.

## <a name="copy-files-from-a-container"></a>Copier des fichiers à partir d’un conteneur

Pour copier un fichier hors du conteneur, utilisez la commande suivante:

```bash
docker cp <Container ID>:<Container path> <host path>
```

**Exemple :**

```bash
docker cp d6b75213ef80:/var/opt/mssql/log/errorlog /tmp/errorlog
```

```PowerShell
docker cp d6b75213ef80:/var/opt/mssql/log/errorlog C:\Temp\errorlog
```

## <a name="copy-files-into-a-container"></a>Copier des fichiers dans un conteneur

Pour copier un fichier dans le conteneur, utilisez la commande suivante:

```bash
docker cp <Host path> <Container ID>:<Container path>
```

**Exemple :**

```bash
docker cp /tmp/mydb.mdf d6b75213ef80:/var/opt/mssql/data
```

```PowerShell
docker cp C:\Temp\mydb.mdf d6b75213ef80:/var/opt/mssql/data
```
## <a id="tz"></a>Configurer le fuseau horaire

Pour exécuter SQL Server dans un conteneur Linux avec un fuseau horaire spécifique, configurez la variable d’environnement **TZ** . Pour trouver la valeur de fuseau horaire appropriée, exécutez la commande **tzselect** à partir d’une invite bash Linux:

```bash
tzselect
```

Après avoir sélectionné le fuseau horaire, **tzselect** affiche une sortie similaire à ce qui suit:

```bash
The following information has been given:

        United States
        Pacific

Therefore TZ='America/Los_Angeles' will be used.
```

Vous pouvez utiliser ces informations pour définir la même variable d’environnement dans votre conteneur Linux. L’exemple suivant montre comment exécuter SQL Server dans un conteneur dans le `Americas/Los_Angeles` fuseau horaire:

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
   -p 1433:1433 --name sql1 \
   -e 'TZ=America/Los_Angeles'\
   -d mcr.microsoft.com/mssql/server:2017-latest 
```

```PowerShell
sudo docker run -e 'ACCEPT_EULA=Y' -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
   -p 1433:1433 --name sql1 `
   -e "TZ=America/Los_Angeles" `
   -d mcr.microsoft.com/mssql/server:2017-latest 
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
   -p 1433:1433 --name sql1 \
   -e 'TZ=America/Los_Angeles'\
   -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

```PowerShell
sudo docker run -e 'ACCEPT_EULA=Y' -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
   -p 1433:1433 --name sql1 `
   -e "TZ=America/Los_Angeles" `
   -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```
::: moniker-end

## <a id="tags"></a>Exécuter une image de conteneur SQL Server spécifique

Il existe des scénarios dans lesquels il est possible que vous ne souhaitiez pas utiliser la dernière image de conteneur SQL Server. Pour exécuter une image de conteneur SQL Server spécifique, procédez comme suit:

1. Identifiez la **balise** d’ancrage pour la version que vous souhaitez utiliser. Pour afficher les balises disponibles, consultez [la page du Hub de l’ancrage MSSQL-Server-Linux](https://hub.docker.com/_/microsoft-mssql-server).

2. Extrayez l’image de conteneur SQL Server avec la balise. Par exemple, pour extraire l’image RC1, remplacez `<image_tag>` dans la commande suivante par `rc1`.

   ```bash
   docker pull mcr.microsoft.com/mssql/server:<image_tag>
   ```

3. Pour exécuter un nouveau conteneur avec cette image, spécifiez le nom de la `docker run` balise dans la commande. Dans la commande suivante, remplacez `<image_tag>` par la version que vous souhaitez exécuter.

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

Vous pouvez également utiliser ces étapes pour rétrograder un conteneur existant. Par exemple, vous souhaiterez peut-être restaurer ou rétrograder un conteneur en cours d’exécution à des fins de dépannage ou de test. Pour rétrograder un conteneur en cours d’exécution, vous devez utiliser une technique de persistance pour le dossier de données. Suivez les mêmes étapes que celles décrites dans la [section mise à niveau](#upgrade), mais spécifiez le nom de balise de l’ancienne version lorsque vous exécutez le nouveau conteneur.

## <a id="version"></a>Vérifier la version du conteneur

Si vous souhaitez connaître la version de SQL Server dans un conteneur d’ancrage en cours d’exécution, exécutez la commande suivante pour l’afficher. Remplacez `<Container ID or name>` par l’ID ou le nom du conteneur cible. Remplacez `<YourStrong!Passw0rd>` par le mot de passe SQL Server pour la connexion sa.

```bash
sudo docker exec -it <Container ID or name> /opt/mssql-tools/bin/sqlcmd \
   -S localhost -U SA -P '<YourStrong!Passw0rd>' \
   -Q 'SELECT @@VERSION'
```

```PowerShell
docker exec -it <Container ID or name> /opt/mssql-tools/bin/sqlcmd `
   -S localhost -U SA -P "<YourStrong!Passw0rd>" `
   -Q 'SELECT @@VERSION'
```

Vous pouvez également identifier la version SQL Server et le numéro de build d’une image de conteneur d’ancrage cible. La commande suivante affiche la version SQL Server et les informations de build de l’image **Microsoft/MSSQL-Server-Linux: 2017-latest** . Pour ce faire, il exécute un nouveau conteneur avec une variable d’environnement **PAL_PROGRAM_INFO = 1**. Le conteneur résultant s’arrête instantanément et la commande `docker rm` le supprime.

```bash
sudo docker run -e PAL_PROGRAM_INFO=1 --name sqlver \
   -ti mcr.microsoft.com/mssql/server:2017-latest && \
   sudo docker rm sqlver
```

```PowerShell
docker run -e PAL_PROGRAM_INFO=1 --name sqlver `
   -ti mcr.microsoft.com/mssql/server:2017-latest; `
   docker rm sqlver
```

Les commandes précédentes affichent des informations de version semblables à la sortie suivante:

```Text
sqlservr
  Version 14.0.3029.16
  Build ID ee3d3882f1c48a7a7e590a620153012eaedc2f37143d485df945a079b9d4eeea
  Build Type release
  Git Version 65d42c4
  Built at Sat Jun 16 01:20:11 GMT 2018

PAL
  Build ID 60cfcb134bbae96d311f6a4f56aeb5a685b3809de80bcb61ec587a8f58b555eb
  Build Type release
  Git Version 21a4c11
  Built at Sat Jun 16 01:18:53 GMT 2018

Packages
  system.sfp                    6.2.9200.1,21a4c1178,
  system.common.sfp             10.0.15063.540
  system.certificates.sfp       6.2.9200.1,21a4c1178,
  system.netfx.sfp              4.6.1590.0
  secforwarderxplat.sfp         14.0.3029.16
  sqlservr.sfp                  14.0.3029.16
  sqlagent.sfp                  14.0.3029.16
```

## <a id="upgrade"></a>Mettre à niveau SQL Server dans les conteneurs

Pour mettre à niveau l’image de conteneur avec l’ancrage, commencez par identifier la balise pour la mise à niveau. Extrayez cette version à partir du `docker pull` Registre à l’aide de la commande:

```bash
docker pull mcr.microsoft.com/mssql/server:<image_tag>
```

Cela met à jour l’image de SQL Server pour les nouveaux conteneurs que vous créez, mais elle ne met pas à jour SQL Server dans les conteneurs en cours d’exécution. Pour ce faire, vous devez créer un nouveau conteneur avec la dernière SQL Server image de conteneur et migrer vos données vers ce nouveau conteneur.

1. Assurez-vous que vous utilisez l’une des techniques de persistance des [données](#persist) pour votre conteneur de SQL Server existant. Cela vous permet de démarrer un nouveau conteneur avec les mêmes données.

1. Arrêtez le conteneur SQL Server à l' `docker stop` aide de la commande.

1. Créez un conteneur de SQL Server avec `docker run` et spécifiez un répertoire hôte mappé ou un conteneur de volume de données. Veillez à utiliser la balise spécifique pour votre mise à niveau SQL Server. Le nouveau conteneur utilise désormais une nouvelle version de SQL Server avec vos données SQL Server existantes.

   > [!IMPORTANT]
   > La mise à niveau est uniquement prise en charge entre RC1, RC2 et GA pour l’instant.

1. Vérifiez vos bases de données et vos données dans le nouveau conteneur.

1. Si vous le souhaitez, supprimez l' `docker rm`ancien conteneur avec.

## <a id="troubleshooting"></a> Dépannage

Les sections suivantes fournissent des suggestions de dépannage pour l’exécution de SQL Server dans des conteneurs.

### <a name="docker-command-errors"></a>Erreurs de commande de l’ancreur

Si vous recevez des erreurs pour `docker` toutes les commandes, assurez-vous que le service d’ancrage est en cours d’exécution et essayez d’exécuter avec des autorisations élevées.

Par exemple, sur Linux, vous pouvez obtenir l’erreur suivante lors de `docker` l’exécution des commandes:

```
Cannot connect to the Docker daemon. Is the docker daemon running on this host?
```

Si vous recevez cette erreur sur Linux, essayez d’exécuter les mêmes commandes précédées `sudo`de. En cas d’échec, vérifiez que le service d’ancrage est en cours d’exécution et démarrez-le si nécessaire.

```bash
sudo systemctl status docker
sudo systemctl start docker
```

Sur Windows, vérifiez que vous lancez PowerShell ou votre invite de commandes en tant qu’administrateur.

### <a name="sql-server-container-startup-errors"></a>Erreurs de démarrage du conteneur SQL Server

Si le conteneur SQL Server ne parvient pas à s’exécuter, essayez les tests suivants:

- Si vous recevez une erreur telle que **«échec de la création d’un point de terminaison CONTAINER_NAME sur le pont réseau. Erreur lors du démarrage du proxy: écouter TCP 0.0.0.0:1433 liaison: adresse déjà utilisée.** , vous essayez de mapper le port de conteneur 1433 à un port qui est déjà en cours d’utilisation. Cela peut se produire si vous exécutez SQL Server localement sur l’ordinateur hôte. Cela peut également se produire si vous démarrez deux conteneurs SQL Server et que vous essayez de les mapper tous les deux sur le même port hôte. Dans ce cas, utilisez le `-p` paramètre pour mapper le port de conteneur 1433 sur un port d’hôte différent. Exemple : 

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1400:1433 -d mcr.microsoft.com/mssql/server:2017-latest`.
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1400:1433 -d mcr.microsoft.com/mssql/server:2017-latest`.
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu`.
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu`.
```

::: moniker-end

- Si vous obtenez une erreur telle que **«l’autorisation a été refusée lors de la tentative de connexion au socket du démon de l’arrimeur sur Unix:///var/run/docker.sock: Obtenir http://%2Fvar%2Frun%2Fdocker.sock/v1.30tdout=1&tail=all: un accès à distance UNIX/var/run/docker.sock: Connect:** autorisation refusée lors de la tentative de démarrage d’un conteneur, ajoutez votre utilisateur au groupe Ancrable dans Ubuntu. Ensuite, déconnectez-vous et reconnectez-vous, car cette modification affecte les nouvelles sessions. 

   ```bash
    usermod -aG docker $USER
    ```
- Vérifiez si des messages d’erreur s’affichent dans le conteneur.

    ```bash
    docker logs e69e056c702d
    ```

- Assurez-vous que vous respectez les exigences minimales en matière de mémoire et de disque spécifiées dans la section [conditions préalables](quickstart-install-connect-docker.md#requirements) de l’article démarrage rapide.

- Si vous utilisez un logiciel de gestion de conteneur, assurez-vous qu’il prend en charge les processus de conteneur s’exécutant en tant qu’utilisateur racine. Le processus sqlservr dans le conteneur s’exécute en tant qu’utilisateur racine.

- Passez en revue les [journaux d’installation et d’erreurs de SQL Server](#errorlogs).

### <a name="enable-dump-captures"></a>Activer les captures de vidage

Si le processus de SQL Server échoue à l’intérieur du conteneur, vous devez créer un nouveau conteneur avec **SYS_PTRACE** activé. Cela ajoute la fonctionnalité Linux pour suivre un processus, ce qui est nécessaire pour créer un fichier de vidage sur une exception. Le fichier dump peut être utilisé par la prise en charge pour aider à résoudre le problème. La commande d’exécution de l’ancreur suivante active cette fonctionnalité.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

::: moniker-end

### <a name="sql-server-connection-failures"></a>SQL Server les échecs de connexion

Si vous ne pouvez pas vous connecter à l’instance SQL Server s’exécutant dans votre conteneur, essayez les tests suivants:

- Assurez-vous que votre conteneur SQL Server est en cours d'  exécution en consultant la `docker ps -a` colonne État de la sortie. Si ce n’est `docker start <Container ID>` pas le cas, utilisez pour le démarrer.

- Si vous avez mappé à un port hôte non défini par défaut (pas 1433), assurez-vous que vous spécifiez le port dans votre chaîne de connexion. Vous pouvez voir votre mappage de port dans la colonne **ports** de `docker ps -a` la sortie. Par exemple, la commande suivante connecte sqlcmd à un conteneur qui écoute sur le port 1401:

    ```bash
    sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
    ```

    ```PowerShell
    sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
    ```

- Si vous avez `docker run` utilisé avec un volume de données ou un conteneur de volume de données mappé existant, SQL Server ignore la valeur de. `MSSQL_SA_PASSWORD` Au lieu de cela, le mot de passe utilisateur préconfiguré est utilisé à partir des données de SQL Server dans le conteneur de volume de données ou de données. Vérifiez que vous utilisez le mot de passe SA associé aux données auxquelles vous êtes attaché.

- Passez en revue les [journaux d’installation et d’erreurs de SQL Server](#errorlogs).

### <a name="sql-server-availability-groups"></a>SQL Server les groupes de disponibilité

Si vous utilisez l’arrimeur avec des groupes de disponibilité SQL Server, il y a deux exigences supplémentaires.

- Mappez le port utilisé pour la communication de réplica (5022 par défaut). Par exemple, spécifiez `-p 5022:5022` dans le cadre de votre `docker run` commande.

- Définissez explicitement le nom d’hôte du conteneur `-h YOURHOSTNAME` avec le paramètre `docker run` de la commande. Ce nom d’hôte est utilisé lorsque vous configurez votre groupe de disponibilité. Si vous ne le spécifiez `-h`pas avec, l’ID du conteneur est utilisé par défaut.

### <a id="errorlogs"></a>SQL Server les journaux d’installation et d’erreurs

Vous pouvez consulter les journaux d’installation et d’erreurs de SQL Server dans **/var/opt/MSSQL/LOG**. Si le conteneur n’est pas en cours d’exécution, démarrez d’abord le conteneur. Utilisez ensuite une invite de commandes interactive pour inspecter les journaux.

```bash
docker start e69e056c702d
docker exec -it e69e056c702d "bash"
```

À partir de la session bash à l’intérieur de votre conteneur, exécutez les commandes suivantes:

```bash
cd /var/opt/mssql/log
cat setup*.log
cat errorlog
```

> [!TIP]
> Si vous avez monté un répertoire hôte sur **/var/opt/MSSQL** lorsque vous avez créé votre conteneur, vous pouvez à la place l’examiner dans le sous-répertoire du **Journal** sur le chemin d’accès mappé sur l’ordinateur hôte.

## <a name="next-steps"></a>Étapes suivantes

Bien démarrer avec les images de conteneur SQL Server 2017 sur l’arrimeur en passant par le [démarrage rapide](quickstart-install-connect-docker.md).

Consultez également le [référentiel GitHub MSSQL-dockr](https://github.com/Microsoft/mssql-docker) pour les ressources, les commentaires et les problèmes connus.

[Explorez la haute disponibilité des conteneurs SQL Server](sql-server-linux-container-ha-overview.md)
