---
title: Options de configuration de SQL Server sur Docker | Microsoft Docs
description: Explorez les différentes façons d’utilisation et d’interagir avec SQL Server 2017 et 2019 images de conteneur d’aperçu dans Docker. Cela inclut la conservation des données, la copie de fichiers et le dépannage.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/17/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: 822fdbe60a9fe7740d2b7cb13ed9b8784e88945d
ms.sourcegitcommit: 0b0f5aba602732834c8439c192d95921149ab4c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67500027"
---
# <a name="configure-sql-server-container-images-on-docker"></a>Configurer des images de conteneur de SQL Server sur Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article explique comment configurer et utiliser le [image mssql-server-linux conteneur](https://hub.docker.com/_/microsoft-mssql-server) avec Docker. Cette image est composée de SQL Server s’exécutant sur Linux basé sur Ubuntu 16.04. Elle peut être utilisée avec Docker Engine 1.8+ sur Linux ou sur Docker pour Mac/Windows.

> [!NOTE]
> Cet article se concentre spécifiquement sur l’utilisation de l’image mssql-server-linux. L’image de Windows n’est pas couverte, mais vous pouvez en savoir plus sur la [page du Hub Docker mssql-server-windows](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/).

## <a name="pull-and-run-the-container-image"></a>Extraire et exécuter l’image conteneur

Pour extraire et exécuter le Docker images de conteneur pour la version préliminaire de SQL Server 2017 et SQL Server 2019, suivez les conditions préalables et les étapes décrites dans le Guide de démarrage rapide suivant :

- [Exécuter l’image de conteneur SQL Server 2017 avec Docker](quickstart-install-connect-docker.md?view=sql-server-2017)
- [Exécuter l’image de conteneur de version préliminaire de SQL Server 2019 avec Docker](quickstart-install-connect-docker.md?view=sql-server-ver15)

Cet article de la configuration fournit des scénarios d’utilisation supplémentaires dans les sections suivantes.

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="rhel"></a> Exécuter des images de conteneur basés sur RHEL

Toute la documentation sur les images de conteneur SQL Server Linux pointer vers les conteneurs basés sur Ubuntu. À compter de SQL Server 2019 preview, vous pouvez utiliser des conteneurs basés sur Red Hat Enterprise Linux (RHEL). Modifier le référentiel de conteneur à partir de **mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu** à **mcr.microsoft.com/mssql/rhel/server:2019-CTP3.1** dans toutes vos commandes docker.

Par exemple, la commande suivante extrait le dernier conteneur de version préliminaire de SQL Server 2019 qui utilise RHEL :

```bash
sudo docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP3.1
```

```PowerShell
docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP3.1
```

::: moniker-end

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="production"></a> Exécuter des images de conteneur de production

Le Guide de démarrage rapide dans la section précédente exécute l’édition développeur gratuite de SQL Server à partir de Docker Hub. La plupart des informations s’applique toujours si vous souhaitez exécuter des images de conteneur, telles que les éditions Enterprise, Standard ou Web de production. Toutefois, il existe quelques différences sont décrites ici.

- Vous pouvez uniquement utiliser SQL Server dans un environnement de production si vous avez une licence valide. Vous pouvez obtenir une licence de production de SQL Server Express gratuite [ici](https://go.microsoft.com/fwlink/?linkid=857693). Les licences SQL Server Standard et Enterprise Edition sont disponibles via [licence en Volume Microsoft](https://www.microsoft.com/licensing/default.aspx).


- L’image de conteneur de développeur peut être configuré pour exécuter les éditions de production. Utilisez les étapes suivantes pour exécuter les éditions de production :

Passez en revue la configuration requise et exécuter des procédures le [quickstart](quickstart-install-connect-docker.md). Vous devez spécifier votre édition de production avec le **MSSQL_PID** variable d’environnement. L’exemple suivant montre comment exécuter la dernière image de conteneur SQL Server 2017 pour la version Enterprise Edition :

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
> En passant la valeur **Y** à la variable d’environnement **ACCEPT_EULA** et une valeur d’édition à **MSSQL_PID**, vous manifestez que vous possédez une licence valide et existante pour l’édition et la version de SQL Server que vous souhaitez utiliser. Vous acceptez également que votre utilisation du logiciel de SQL Server s’exécutant dans une image de conteneur Docker est régie par les termes du contrat de licence SQL Server.

> [!NOTE]
> Pour obtenir la liste complète des valeurs possibles pour **MSSQL_PID**, consultez [des paramètres de configuration de SQL Server avec les variables d’environnement sur Linux](sql-server-linux-configure-environment-variables.md).

::: moniker-end

## <a name="connect-and-query"></a>Se connecter et interroger

Vous pouvez vous connecter et interroger SQL Server dans un conteneur depuis l’extérieur du conteneur ou le conteneur. Les sections suivantes expliquent les deux scénarios. 

### <a name="tools-outside-the-container"></a>Outils en dehors du conteneur

Vous pouvez vous connecter à l’instance de SQL Server sur votre machine Docker à partir de n’importe quel outil externe Linux, Windows ou macOS qui prend en charge les connexions SQL. Certains outils courants incluent :

- [sqlcmd](sql-server-linux-setup-tools.md)
- [Visual Studio Code](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) sur Windows](sql-server-linux-manage-ssms.md)

L’exemple suivant utilise **sqlcmd** pour se connecter à SQL Server s’exécutant dans un conteneur Docker. L’adresse IP dans la chaîne de connexion est l’adresse IP de l’ordinateur hôte qui exécute le conteneur.

```bash
sqlcmd -S 10.3.2.4 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4 -U SA -P "<YourPassword>"
```

Si vous avez mappé un port d’hôte qui n’était pas la valeur par défaut **1433**, ajoutez ce port à la chaîne de connexion. Par exemple, si vous avez spécifié `-p 1400:1433` dans votre `docker run` commande, puis se connecter explicitement à spécifier le port 1400.

```bash
sqlcmd -S 10.3.2.4,1400 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1400 -U SA -P "<YourPassword>"
```

### <a name="tools-inside-the-container"></a>Outils de l’intérieur du conteneur

À partir de SQL Server 2017 preview, le [les outils de ligne de SQL Server](sql-server-linux-setup-tools.md) sont inclus dans l’image de conteneur. Si vous vous attachez à l’image avec une invite de commandes interactive, vous pouvez exécuter les outils localement.

1. Utilisez la commande `docker exec -it` pour démarrer un interpréteur de commandes bash interactif dans votre conteneur en cours d’exécution. Dans l’exemple suivant `e69e056c702d` est l’ID de conteneur.

    ```bash
    docker exec -it e69e056c702d "bash"
    ```

    > [!TIP]
    > Vous n’êtes pas obligé toujours spécifier l’id de l’intégralité du conteneur. Vous devez uniquement spécifier suffisamment de caractères pour identifier de manière unique. Dans cet exemple, elle peut donc être suffisant pour utiliser `e6` ou `e69` au lieu de l’id complet.

2. Une fois dans le conteneur, connectez-vous localement avec sqlcmd. Notez que sqlcmd n’est pas dans le chemin d’accès par défaut, donc vous devez spécifier le chemin d’accès complet.

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
    ```

3. Lorsque vous avez terminé avec sqlcmd, tapez `exit`.

4. Lorsque vous avez terminé avec l’invite de commandes interactive, tapez `exit`. Le conteneur continue de s’exécuter une fois que vous avez quitté l’interpréteur de commandes bash interactif.

## <a name="run-multiple-sql-server-containers"></a>Exécutez plusieurs conteneurs de SQL Server

Docker fournit un moyen d’exécuter plusieurs conteneurs de SQL Server sur le même ordinateur hôte. Il s’agit de l’approche pour les scénarios qui requièrent plusieurs instances de SQL Server sur le même hôte. Chaque conteneur doit exposer elle-même sur un port différent.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

L’exemple suivant crée deux conteneurs de SQL Server 2017 et les mappe aux ports **1401** et **1402** sur l’ordinateur hôte.

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

L’exemple suivant crée deux conteneurs de version préliminaire de SQL Server 2019 et les mappe aux ports **1401** et **1402** sur l’ordinateur hôte.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

::: moniker-end

Maintenant il existe deux instances de SQL Server s’exécutant dans des conteneurs distincts. Les clients peuvent se connecter à chaque instance de SQL Server à l’aide de l’adresse IP de l’hôte Docker et le numéro de port pour le conteneur.

```bash
sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
sqlcmd -S 10.3.2.4,1402 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
sqlcmd -S 10.3.2.4,1402 -U SA -P "<YourPassword>"
```

## <a id="customcontainer"></a> Créer un conteneur personnalisé

Il est possible de créer vos propres [Dockerfile](https://docs.docker.com/engine/reference/builder/#usage) pour créer un conteneur de SQL Server personnalisé. Pour plus d’informations, consultez [une démonstration qui combine l’application SQL Server et une nœud](https://github.com/twright-msft/mssql-node-docker-demo-app). Si vous créez votre propre fichier Dockerfile, n’oubliez pas du processus de premier plan, car ce processus détermine la durée de vie du conteneur. Si elle est fermée, le conteneur va s’arrêter. Par exemple, si vous souhaitez exécuter un script et démarrer SQL Server, assurez-vous que le processus SQL Server est la commande la plus à droite. Toutes les autres commandes sont exécutées en arrière-plan. Ceci est illustré dans la commande suivante à l’intérieur d’un fichier Dockerfile :

```bash
/usr/src/app/do-my-sql-commands.sh & /opt/mssql/bin/sqlservr
```

Si vous avez annulée les commandes dans l’exemple précédent, le conteneur est arrêt lorsque le script-mon-sql-commands.sh est terminée.

## <a id="persist"></a> Conserver vos données

Vos modifications de configuration de SQL Server et les fichiers de base de données sont conservées dans le conteneur même si vous redémarrez le conteneur avec `docker stop` et `docker start`. Toutefois, si vous supprimez le conteneur avec `docker rm`, tous les éléments dans le conteneur sont supprimé, y compris SQL Server et vos bases de données. La section suivante explique comment utiliser **volumes de données** pour conserver vos fichiers de base de données, même si les conteneurs associés sont supprimés.

> [!IMPORTANT]
> Pour SQL Server, il est essentiel que vous compreniez persistance des données dans Docker. En plus de la discussion dans cette section, consultez la documentation de Docker sur [comment gérer les données dans des conteneurs Docker](https://docs.docker.com/engine/tutorials/dockervolumes/).

### <a name="mount-a-host-directory-as-data-volume"></a>Monter d’un répertoire de l’hôte en tant que volume de données

La première option consiste à monter d’un répertoire sur votre ordinateur hôte comme un volume de données dans votre conteneur. Pour ce faire, utilisez le `docker run` commande avec le `-v <host directory>:/var/opt/mssql` indicateur. Ainsi, les données à restaurer entre les exécutions de conteneur.

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

Cette technique vous permet également de partager et d’afficher les fichiers sur l’ordinateur hôte en dehors de Docker.

> [!IMPORTANT]
> Mappage de volume hôte pour Docker sur Mac avec SQL Server sur une image Linux n’est pas pris en charge pour l’instant. Utilisez à la place des conteneurs de volumes de données. Cette restriction est spécifique à la `/var/opt/mssql` directory. Lecture à partir d’un répertoire monté de fonctionne bien. Par exemple, vous pouvez monter un répertoire de l’hôte à l’aide de - v sur Mac et restaurer une sauvegarde à partir d’un fichier .bak qui réside sur l’ordinateur hôte.

### <a name="use-data-volume-containers"></a>Utiliser des conteneurs de volumes de données

La deuxième option consiste à utiliser un conteneur de volumes de données. Vous pouvez créer un conteneur de volumes de données en spécifiant un nom de volume au lieu d’un répertoire de l’hôte avec le `-v` paramètre. L’exemple suivant crée un volume de données partagé nommé **sqlvolume**.

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
> Cette technique pour la création d’un volume de données implicitement dans la commande d’exécution ne fonctionne pas avec les versions antérieures de Docker. Dans ce cas, suivez les étapes explicites décrites dans la documentation de Docker, [création et le montage d’un conteneur de volumes de données](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container).

Même si vous arrêtez et supprimez ce conteneur, le volume de données persiste. Vous pouvez l’afficher avec le `docker volume ls` commande.

```bash
docker volume ls
```

Si vous créez ensuite un autre conteneur portant le même nom de volume, le nouveau conteneur utilise les mêmes données de SQL Server contenues dans le volume.

Pour supprimer un conteneur de volumes de données, utilisez la `docker volume rm` commande.

> [!WARNING]
> Si vous supprimez le conteneur de volumes de données, toutes les données SQL Server dans le conteneur sont *définitivement* supprimé.

### <a name="backup-and-restore"></a>Sauvegarde et restauration

En plus de ces techniques de conteneur, vous pouvez également utiliser la sauvegarde de SQL Server standard et restaurer des techniques. Vous pouvez utiliser des fichiers de sauvegarde pour protéger vos données ou pour déplacer les données vers une autre instance de SQL Server. Pour plus d’informations, consultez [sauvegarde et restauration SQL Server databases sur Linux](sql-server-linux-backup-and-restore-database.md).

> [!WARNING]
> Si vous créez des sauvegardes, veillez à créer ou copier les fichiers de sauvegarde en dehors du conteneur. Sinon, si le conteneur est supprimé, les fichiers de sauvegarde sont également supprimés.

## <a name="execute-commands-in-a-container"></a>Exécuter des commandes dans un conteneur

Si vous avez un conteneur en cours d’exécution, vous pouvez exécuter des commandes dans le conteneur à partir d’un ordinateur hôte terminal.

Pour obtenir l’ID de conteneur exécutée :

```bash
docker ps
```

Pour démarrer un bash terminal dans l’exécution du conteneur :

```bash
docker exec -it <Container ID> /bin/bash
```

Vous pouvez maintenant exécuter des commandes comme s’exécutent sur un terminal à l’intérieur du conteneur. Quand vous avez terminé, tapez `exit`. Cela se termine dans la session de commande interactive, mais votre conteneur continue à s’exécuter.

## <a name="copy-files-from-a-container"></a>Copier des fichiers à partir d’un conteneur

Pour copier un fichier en dehors du conteneur, utilisez la commande suivante :

```bash
docker cp <Container ID>:<Container path> <host path>
```

**Exemple :**

```bash
docker cp d6b75213ef80:/var/opt/mssql/log/errorlog /tmp/errorlog
```

```PowerShell
docker cp d6b75213ef80:/var/opt/mssql/log/errorlog C:\Temp\errorlog
```

## <a name="copy-files-into-a-container"></a>Copiez les fichiers dans un conteneur

Pour copier un fichier dans le conteneur, utilisez la commande suivante :

```bash
docker cp <Host path> <Container ID>:<Container path>
```

**Exemple :**

```bash
docker cp /tmp/mydb.mdf d6b75213ef80:/var/opt/mssql/data
```

```PowerShell
docker cp C:\Temp\mydb.mdf d6b75213ef80:/var/opt/mssql/data
```
## <a id="tz"></a> Configurer le fuseau horaire

Pour exécuter SQL Server dans un conteneur Linux avec un fuseau horaire spécifique, vous devez configurer le **TZ** variable d’environnement. Pour rechercher la valeur de fuseau horaire approprié, exécutez le **tzselect** commande à partir d’une invite de commandes bash Linux :

```bash
tzselect
```

Après avoir sélectionné le fuseau horaire, **tzselect** affiche une sortie similaire à ce qui suit :

```bash
The following information has been given:

        United States
        Pacific

Therefore TZ='America/Los_Angeles' will be used.
```

Vous pouvez utiliser ces informations pour définir la variable d’environnement dans votre conteneur Linux. L’exemple suivant montre comment exécuter SQL Server dans un conteneur dans le `Americas/Los_Angeles` fuseau horaire :

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

## <a id="tags"></a> Exécuter une image de conteneur SQL Server spécifique

Il existe des scénarios où vous ne souhaiterez pas utiliser la dernière image de conteneur de SQL Server. Pour exécuter une image de conteneur SQL Server spécifique, utilisez les étapes suivantes :

1. Identifier le Docker **balise** pour la version que vous souhaitez utiliser. Pour afficher les légendes disponibles, consultez [la page du hub Docker mssql-server-linux](https://hub.docker.com/_/microsoft-mssql-server).

2. Extrayez l’image de conteneur de SQL Server avec la balise. Par exemple, pour extraire l’image de RC1, remplacez `<image_tag>` dans la commande suivante avec `rc1`.

   ```bash
   docker pull mcr.microsoft.com/mssql/server:<image_tag>
   ```

3. Pour exécuter un conteneur avec cette image, spécifiez le nom de balise dans le `docker run` commande. Dans la commande suivante, remplacez `<image_tag>` avec la version que vous souhaitez exécuter.

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

Ces étapes peuvent également servir à mettre à niveau d’un conteneur existant. Vous pourrez par exemple, pour restaurer ou rétrograder un conteneur en cours d’exécution pour le test ou de résolution des problèmes. Pour passer un conteneur en cours d’exécution, vous devez utiliser une technique de persistance pour le dossier de données. Suivez les mêmes étapes décrites dans le [mise à niveau de la section](#upgrade), mais vous spécifiez le nom de balise de l’ancienne version lorsque vous exécutez le nouveau conteneur.

## <a id="version"></a> Vérifier la version de conteneur

Si vous souhaitez connaître la version de SQL Server dans un conteneur docker en cours d’exécution, exécutez la commande suivante pour l’afficher. Remplacez `<Container ID or name>` avec le nom ou l’ID du conteneur cible. Remplacez `<YourStrong!Passw0rd>` avec le mot de passe SQL Server pour la connexion SA.

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

Vous pouvez également identifier la version de SQL Server et le numéro de build pour une image de conteneur docker cible. La commande suivante affiche les informations de version et de build de SQL Server pour le **microsoft/mssql-server-linux:2017-dernière** image. Pour ce faire, il exécute un nouveau conteneur avec une variable d’environnement **PAL_PROGRAM_INFO = 1**. Le conteneur obtenu se termine immédiatement et le `docker rm` commande le supprime.

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

Les commandes précédentes affichent des informations de version similaires à la sortie suivante :

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

## <a id="upgrade"></a> Mise à niveau SQL Server dans des conteneurs

Pour mettre à niveau de l’image de conteneur avec Docker, commencez par identifier la balise pour la version pour votre mise à niveau. Extraire cette version à partir du Registre avec le `docker pull` commande :

```bash
docker pull mcr.microsoft.com/mssql/server:<image_tag>
```

Cela met à jour l’image de SQL Server pour les nouveaux conteneurs que vous créez, mais il ne met pas à jour SQL Server de tous les conteneurs en cours d’exécution. Pour ce faire, vous devez créer un conteneur avec la dernière image de conteneur de SQL Server et migrer vos données vers ce nouveau conteneur.

1. Assurez-vous que vous utilisez l’une de le [techniques de persistance de données](#persist) pour votre conteneur de SQL Server existant. Cela vous permet de démarrer un conteneur de nouveau avec les mêmes données.

1. Arrêter le conteneur de SQL Server avec le `docker stop` commande.

1. Créer un nouveau conteneur de SQL Server avec `docker run` et spécifiez un répertoire de l’hôte mappé ou un conteneur de volumes de données. Veillez à utiliser la balise spécifique pour votre mise à niveau de SQL Server. Le nouveau conteneur utilise désormais une nouvelle version de SQL Server avec vos données SQL Server existantes.

   > [!IMPORTANT]
   > Mise à niveau est uniquement prise en charge entre la disponibilité générale, RC1 et RC2 pour l’instant.

1. Vérifiez vos bases de données et les données dans le nouveau conteneur.

1. Si vous le souhaitez, supprimez l’ancien conteneur avec `docker rm`.

## <a id="troubleshooting"></a> Dépannage

Les sections suivantes fournissent des suggestions de dépannage pour SQL Server en cours d’exécution dans des conteneurs.

### <a name="docker-command-errors"></a>Erreurs de commande docker

Si vous obtenez des erreurs pour toute `docker` commandes, assurez-vous que le service docker est en cours d’exécution et essayez d’exécuter avec des autorisations élevées.

Par exemple, sur Linux, vous pouvez obtenir l’erreur suivante lors de l’exécution `docker` commandes :

```
Cannot connect to the Docker daemon. Is the docker daemon running on this host?
```

Si vous obtenez cette erreur sur Linux, essayez d’exécuter les mêmes commandes précédés `sudo`. Si cette tentative échoue, vérifiez que le service docker est en cours d’exécution et démarrez-le si nécessaire.

```bash
sudo systemctl status docker
sudo systemctl start docker
```

Sur Windows, vérifiez que vous lancez PowerShell ou l’invite de commandes en tant qu’administrateur.

### <a name="sql-server-container-startup-errors"></a>Erreurs de démarrage du conteneur SQL Server

Si le conteneur de SQL Server ne parvient pas à exécuter, essayez les tests suivants :

- Si vous obtenez une erreur comme **' n’a pas pu créer le point de terminaison CONTAINER_NAME pont réseau. Erreur lors du démarrage du proxy : liaison de 0.0.0.0:1433 d’écoute tcp : adresses déjà en cours d’utilisation. »** , puis vous essayez de mapper le port 1433 du conteneur à un port qui est déjà en cours d’utilisation. Cela peut se produire si vous utilisez SQL Server localement sur l’ordinateur hôte. Il peut également se produire si vous démarrez deux conteneurs de SQL Server et que vous essayez de les mapper à la fois sur le même port d’hôte. Si cela se produit, utilisez le `-p` paramètre à mapper le port 1433 du conteneur à un port d’hôte différent. Exemple : 

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

- Vérifiez s’il existe des messages d’erreur à partir du conteneur.

    ```bash
    docker logs e69e056c702d
    ```

- Assurez-vous que vous remplissez la mémoire et disque minimale spécifiée dans le [conditions préalables](quickstart-install-connect-docker.md#requirements) section de l’article de démarrage rapide.

- Si vous utilisez un logiciel de gestion de conteneur, assurez-vous qu’il prend en charge les processus de conteneur qui s’exécutent en tant que racine. Le processus sqlservr dans le conteneur s’exécute en tant que racine.

- Examinez le [les journaux d’installation et d’erreur SQL Server](#errorlogs).

### <a name="enable-dump-captures"></a>Activer les captures de vidage

Si le processus SQL Server échoue à l’intérieur du conteneur, vous devez créer un nouveau conteneur avec **SYS_PTRACE** activé. Cette opération ajoute la fonctionnalité de Linux pour effectuer le suivi d’un processus, ce qui est nécessaire pour la création d’un fichier de vidage sur une exception. Le fichier de vidage peut être utilisé par le support technique pour aider à résoudre le problème. La suivante commande docker run permet cette fonctionnalité.

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

### <a name="sql-server-connection-failures"></a>Échecs de connexion SQL Server

Si vous ne pouvez pas vous connecter à l’instance de SQL Server en cours d’exécution dans votre conteneur, essayez les tests suivants :

- Assurez-vous que votre conteneur de SQL Server est en cours d’exécution en examinant le **état** colonne de la `docker ps -a` sortie. Dans le cas contraire, utilisez `docker start <Container ID>` pour le démarrer.

- Si vous avez mappé à un port d’hôte non-par défaut (1433 pas), assurez-vous que vous spécifiez le port dans votre chaîne de connexion. Vous pouvez voir votre mappage de port dans le **PORTS** colonne de la `docker ps -a` sortie. Par exemple, la commande suivante établit une connexion sqlcmd dans un conteneur à l’écoute sur le port 1401 :

    ```bash
    sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
    ```

    ```PowerShell
    sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
    ```

- Si vous avez utilisé `docker run` avec un volume de données mappée existant ou un conteneur de volumes de données, SQL Server ignore la valeur de `MSSQL_SA_PASSWORD`. Au lieu de cela, le mot de passe SA préconfiguré est utilisé à partir des données dans le volume de données ou d’un conteneur de volumes de données SQL Server. Vérifiez que vous utilisez le mot de passe SA associé aux données que vous joignez à.

- Examinez le [les journaux d’installation et d’erreur SQL Server](#errorlogs).

### <a name="sql-server-availability-groups"></a>Groupes de disponibilité SQL Server

Si vous utilisez Docker avec des groupes de disponibilité de SQL Server, il existe deux spécifications supplémentaires.

- Mapper le port qui est utilisé pour la communication de réplica (valeur par défaut 5022). Par exemple, spécifier `-p 5022:5022` dans le cadre de votre `docker run` commande.

- Définir explicitement le nom d’hôte de conteneur avec la `-h YOURHOSTNAME` paramètre de la `docker run` commande. Ce nom d’hôte est utilisé lorsque vous configurez votre groupe de disponibilité. Si vous ne le spécifiez avec `-h`, les valeurs par défaut à l’ID de conteneur.

### <a id="errorlogs"></a> Journaux de configuration et des erreurs de SQL Server

Vous pouvez consulter le programme d’installation de SQL Server et des journaux des erreurs **/var/opt/mssql/log**. Si le conteneur n’est pas en cours d’exécution, tout d’abord démarrer le conteneur. Puis utilisez une invite de commandes interactive pour examiner les journaux.

```bash
docker start e69e056c702d
docker exec -it e69e056c702d "bash"
```

À partir de la session d’interpréteur de commandes à l’intérieur de votre conteneur, exécutez les commandes suivantes :

```bash
cd /var/opt/mssql/log
cat setup*.log
cat errorlog
```

> [!TIP]
> Si vous avez monté un répertoire de l’hôte à **/var/opt/mssql** lorsque vous avez créé votre conteneur, vous pouvez consulter à la place de la **journal** sous-répertoire sur le chemin d’accès mappé sur l’ordinateur hôte.

## <a name="next-steps"></a>Étapes suivantes

Prise en main des images de conteneur SQL Server 2017 sur Docker en passant par le [quickstart](quickstart-install-connect-docker.md).

Consultez également le [du référentiel GitHub mssql-docker](https://github.com/Microsoft/mssql-docker) pour les ressources, des commentaires et problèmes connus.

[Explorez la haute disponibilité pour les conteneurs de SQL Server](sql-server-linux-container-ha-overview.md)
