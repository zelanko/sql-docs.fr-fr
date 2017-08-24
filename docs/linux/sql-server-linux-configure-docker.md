---
title: Options de configuration de SQL Server 2017 sur Docker | Documents Microsoft
description: "Explorer les différentes façons d’utilisation et d’interagir avec SQL Server 2017 les images de conteneur dans Docker. Cela inclut les données persistantes, copie de fichiers et de résolution des problèmes."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f87c28e4d2ba7689d422ccf2f1a903765a39f27a
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="configure-sql-server-2017-container-images-on-docker"></a>Configurer SQL Server 2017 les images de conteneur sur Docker

Cette rubrique explique comment configurer et utiliser le [image de conteneur de mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/) avec Docker. Cette image se compose de SQL Server est en cours d’exécution sur Linux basé sur Ubuntu 16.04. Il peut être utilisé avec le moteur Docker 1.8 + sur Linux ou sur Docker pour Mac et Windows.

> [!NOTE]
> Cette rubrique se concentre spécifiquement sur l’utilisation de l’image mssql-server-linux. L’image Windows n’est pas couverte, mais vous pouvez en savoir plus sur elle sur le [page du Hub Docker mssql-server-windows](https://hub.docker.com/r/microsoft/mssql-server-windows/).

## <a name="pull-and-run-the-container-image"></a>Extraire et exécuter l’image de conteneur

Pour extraire et exécuter la Docker image de conteneur pour SQL Server 2017, suivez les conditions préalables et les étapes du didacticiel de démarrage rapide suivants :

- [Exécuter l’image de SQL Server 2017 conteneur avec Docker](quickstart-install-connect-docker.md)

Cette rubrique de configuration fournit des connexions supplémentaires et des scénarios d’utilisation dans les sections ci-dessous.

## <a name="connect-and-query"></a>Se connecter et de requête

Vous pouvez vous connecter et de requêtes SQL Server dans un conteneur depuis l’extérieur du conteneur ou le conteneur. Les sections suivantes expliquent les deux scénarios. 

### <a name="tools-outside-the-container"></a>Outils en dehors du conteneur

Vous pouvez vous connecter à l’instance de SQL Server sur votre ordinateur Docker à partir de n’importe quel outil externe macOS, Windows ou Linux qui prend en charge les connexions SQL. Certains outils courants incluent :

- [Sqlcmd](sql-server-linux-setup-tools.md)
- [Code Visual Studio](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) sur Windows](sql-server-linux-develop-use-ssms.md)

L’exemple suivant utilise **sqlcmd** pour se connecter à SQL Server s’exécutant dans un conteneur Docker. L’adresse IP dans la chaîne de connexion est l’adresse IP de l’ordinateur hôte qui est en cours d’exécution du conteneur.

```bash
sqlcmd -S 10.3.2.4 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4 -U SA -P "<YourPassword>"
```

Si vous avez mappé un port de l’hôte qui n’a pas la valeur par défaut **1433**, ajoutez ce port pour la chaîne de connexion. Par exemple, si vous avez spécifié `-p 1400:1433` dans votre `docker run` de commandes, puis se connecter explicitement à spécifier le port 1400.

```bash
sqlcmd -S 10.3.2.4,1400 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1400 -U SA -P "<YourPassword>"
```

### <a name="tools-inside-the-container"></a>Outils de l’intérieur du conteneur

Démarrage de SQL Server 2017 CTP 2.0, le [les outils de ligne de SQL Server](sql-server-linux-setup-tools.md) sont inclus dans l’image de conteneur. Si vous attachez à l’image avec une invite de commandes interactive, vous pouvez exécuter les outils localement.

1. Utilisez la `docker exec -it` commande pour démarrer un shell bash interactive à l’intérieur de votre conteneur en cours d’exécution. Dans l’exemple suivant `e69e056c702d` est l’ID de conteneur.

    ```bash
    docker exec -it e69e056c702d "bash"
    ```

    > [!TIP]
    > Vous n’avez toujours spécifier l’id de conteneur entier. Vous devez uniquement spécifier suffisamment de caractères pour identifier de façon unique. Dans cet exemple, il peut être suffisant pour utiliser `e6` ou `e69` au lieu de l’id complet.

2. Une fois à l’intérieur du conteneur, se connecter localement avec sqlcmd. Notez que sqlcmd n’est pas dans le chemin d’accès par défaut, donc vous devez spécifier le chemin d’accès complet.

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
    ```

3. Lorsque vous avez terminé avec sqlcmd, tapez `exit`.

4. Lorsque vous avez terminé avec l’invite de commande interactive, tapez `exit`. Le conteneur se poursuit après avoir quitté l’interpréteur de commandes bash interactif.

## <a name="run-multiple-sql-server-containers"></a>Exécuter plusieurs conteneurs de SQL Server

Docker permet d’exécuter plusieurs conteneurs de SQL Server sur le même ordinateur hôte. Il s’agit de l’approche pour les scénarios qui requièrent plusieurs instances de SQL Server sur le même hôte. Chaque conteneur doit exposer lui-même sur un port différent.

L’exemple suivant crée deux conteneurs de SQL Server et les mappe aux ports **1401** et **1402** sur l’ordinateur hôte.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' --cap-add SYS_PTRACE -p 1401:1433 -d microsoft/mssql-server-linux
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' --cap-add SYS_PTRACE -p 1402:1433 -d microsoft/mssql-server-linux
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" --cap-add SYS_PTRACE -p 1401:1433 -d microsoft/mssql-server-linux
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" --cap-add SYS_PTRACE -p 1402:1433 -d microsoft/mssql-server-linux
```

Il existe désormais des deux instances de SQL Server en cours d’exécution dans des conteneurs. Les clients peuvent se connecter à chaque instance de SQL Server à l’aide de l’adresse IP de l’hôte Docker et le numéro de port pour le conteneur.

```bash
sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
sqlcmd -S 10.3.2.4,1402 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
sqlcmd -S 10.3.2.4,1402 -U SA -P "<YourPassword>"
```

## <a id="persist"></a>Conserver vos données

Vos modifications de configuration SQL Server et les fichiers de base de données sont rendues persistantes dans le conteneur même si vous redémarrez le conteneur avec `docker stop` et `docker start`. Toutefois, si vous supprimez le conteneur avec `docker rm`, tous les éléments dans le conteneur sont supprimé, y compris SQL Server et vos bases de données. La section suivante explique comment utiliser **des volumes de données** pour conserver vos fichiers de base de données, même si les conteneurs associées sont supprimées.

> [!IMPORTANT]
> Pour SQL Server, il est essentiel que vous compreniez persistance des données dans Docker. Outre la discussion dans cette section, consultez documentation de Docker sur [comment gérer les données dans des conteneurs Docker](https://docs.docker.com/engine/tutorials/dockervolumes/).

### <a name="mount-a-host-directory-as-data-volume"></a>Monter d’un répertoire de l’hôte en tant que volume de données

La première option consiste à monter d’un répertoire sur votre ordinateur hôte en tant qu’un volume de données dans votre conteneur. Pour ce faire, utilisez le `docker run` avec la `-v <host directory>:/var/opt/mssql` indicateur. Ainsi, les données à restaurer entre les exécutions de conteneur.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' --cap-add SYS_PTRACE -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" --cap-add SYS_PTRACE -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux
```

Cette technique vous permet également de partager et afficher les fichiers sur l’ordinateur hôte en dehors de Docker.

> [!IMPORTANT]
> Mappage du volume hôte pour Docker sur Mac avec SQL Server sur une image Linux n’est pas prise en charge pour l’instant. Utilisez à la place des conteneurs de volumes de données. Cette restriction est spécifique à la `/var/opt/msql` active. Lors de la lecture à partir d’un répertoire monté de fonctionne correctement. Par exemple, vous pouvez monter un répertoire de l’hôte à l’aide de – v sur Mac et restaurer une sauvegarde à partir d’un fichier .bak qui réside sur l’ordinateur hôte.

### <a name="use-data-volume-containers"></a>Utiliser des conteneurs de volumes de données

La deuxième option consiste à utiliser un conteneur de volume de données. Vous pouvez créer un conteneur de volume de données en spécifiant un nom de volume au lieu d’un répertoire de l’hôte avec le `-v` paramètre. L’exemple suivant crée un volume de données partagé nommé **sqlvolume**.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' --cap-add SYS_PTRACE -p 1433:1433 -v sqlvolume:/var/opt/mssql -d microsoft/mssql-server-linux
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" --cap-add SYS_PTRACE -p 1433:1433 -v sqlvolume:/var/opt/mssql -d microsoft/mssql-server-linux
```

> [!NOTE]
> Cette technique pour la création d’un volume de données implicitement dans la commande d’exécution ne fonctionne pas avec les versions antérieures de Docker. Dans ce cas, utilisez les étapes explicites dans la documentation de Docker, [création et le montage d’un conteneur de volume de données](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container).

Même si vous arrêtez et supprimez ce conteneur, le volume de données est conservé. Vous pouvez l’afficher avec le `docker volume ls` commande.

```bash
docker volume ls
```

Si vous créez ensuite un autre conteneur portant le même nom de volume, le nouveau conteneur utilise les mêmes données de SQL Server contenues dans le volume.

Pour supprimer un conteneur de volume de données, utilisez la `docker volume rm` commande.

> [!WARNING]
> Si vous supprimez le conteneur de volume de données, toutes les données de SQL Server dans le conteneur sont *définitivement* supprimé.

### <a name="backup-and-restore"></a>Sauvegarde et restauration
En plus de ces techniques de conteneur, vous pouvez également utiliser la sauvegarde de SQL Server standard et restaurer les techniques. Vous pouvez utiliser des fichiers de sauvegarde pour protéger vos données ou pour déplacer les données vers une autre instance de SQL Server. Pour plus d’informations, consultez [sauvegarde et restauration SQL Server databases sur Linux](sql-server-linux-backup-and-restore-database.md).

> [!WARNING]
> Si vous créez des sauvegardes, veillez à créer ou copier les fichiers de sauvegarde en dehors du conteneur. Sinon, si le conteneur est supprimé, les fichiers de sauvegarde sont également supprimés.

## <a name="execute-commands-in-a-container"></a>Exécuter des commandes dans un conteneur

Si vous avez un conteneur en cours d’exécution, vous pouvez exécuter des commandes dans le conteneur d’un hôte de Terminal Server.

Pour obtenir l’ID du conteneur exécuter :

```bash
docker ps
```

Pour démarrer un Terminal Server dans le conteneur d’exécuter un interpréteur de commandes :

```bash
docker exec -ti <Container ID> /bin/bash
```

Vous pouvez maintenant exécuter des commandes comme s’exécutent au niveau du terminal à l’intérieur du conteneur. Lorsque vous avez terminé, tapez `exit`. Il se termine dans la session de commande interactive, mais votre conteneur continue à s’exécuter.

## <a name="copy-files-from-a-container"></a>Copiez les fichiers à partir d’un conteneur

Pour copier un fichier hors du conteneur, utilisez la commande suivante :

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

## <a name="upgrade-sql-server-in-containers"></a>Mise à niveau SQL Server dans des conteneurs

Pour mettre à niveau de l’image de conteneur avec Docker, extraire la dernière version à partir du Registre. Utilisez la `docker pull` commande :

```bash
docker pull microsoft/mssql-server-linux:latest
```

Cela met à jour l’image de SQL Server pour les conteneurs de nouveau que vous créez, mais il ne met pas à jour SQL Server de tous les conteneurs en cours d’exécution. Pour ce faire, vous devez créer un conteneur avec la dernière image de conteneur de SQL Server et migrer vos données vers ce nouveau conteneur.

1. Tout d’abord, assurez-vous que vous utilisez l’un de le [techniques de persistance des données](#persist) pour votre conteneur de SQL Server existant.

2. Arrêtez le conteneur de SQL Server avec le `docker stop` commande.

3. Créer un nouveau conteneur de SQL Server avec `docker run` et spécifiez un répertoire hôte mappé ou un conteneur de volume de données. Le nouveau conteneur utilise désormais une nouvelle version de SQL Server avec vos données SQL Server existantes.

4. Vérifiez vos bases de données et les données dans le nouveau conteneur.

5. Éventuellement, supprimez l’ancien conteneur avec `docker rm`.

## <a id="troubleshooting"></a>Résolution des problèmes

Les sections suivantes fournissent des suggestions de dépannage pour SQL Server en cours d’exécution dans des conteneurs.

### <a name="docker-command-errors"></a>Erreurs de commande docker

Si vous obtenez des erreurs pour toute `docker` commandes, assurez-vous que le service docker est en cours d’exécution et essayez d’exécuter avec des autorisations élevées.

Par exemple, sur Linux, vous pouvez obtenir l’erreur suivante lors de l’exécution `docker` commandes :

```
Cannot connect to the Docker daemon. Is the docker daemon running on this host?
```

Si vous obtenez cette erreur sur Linux, essayez d’exécuter les mêmes commandes commençant par `sudo`. En cas d’échec, vérifiez que le service docker est en cours d’exécution et démarrez-le si nécessaire.

```bash
sudo systemctl status docker
sudo systemctl start docker
```

Sous Windows, vérifiez que vous démarrez PowerShell ou l’invite de commandes en tant qu’administrateur.

### <a name="sql-server-container-startup-errors"></a>Erreurs de démarrage du conteneur de SQL Server

Si le conteneur de SQL Server ne parvient pas à exécuter, essayez les tests suivants :

- Si vous obtenez une erreur telle que **' n’a pas pu créer de point de terminaison nom_conteneur sur le pont réseau. Erreur lors du démarrage du proxy : liaison de 0.0.0.0:1433 d’écoute tcp : adresse déjà en cours d’utilisation. »** , puis vous essayez de mapper le port 1433 du conteneur à un port qui est déjà en cours d’utilisation. Cela peut se produire si vous utilisez SQL Server localement sur l’ordinateur hôte. Il peut également se produire si vous démarrez les deux conteneurs de SQL Server et que vous essayez de mapper tous les deux sur le même port de l’hôte. Si cela se produit, utilisez le `-p` paramètre à mapper le port 1433 du conteneur à un port d’hôte différent. Par exemple : 

    ```bash
    docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' --cap-add SYS_PTRACE -p 1400:1433 -d microsoft/mssql-server-linux`.
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" --cap-add SYS_PTRACE -p 1400:1433 -d microsoft/mssql-server-linux`.
    ```

- Vérifiez s’il existe des messages d’erreur à partir du conteneur.

    ```bash
    docker logs e69e056c702d
    ```

- Vérifiez que la mémoire et disque minimale spécifiée dans le [exigences](#requirements) section de cette rubrique.

- Si vous utilisez un logiciel de gestion de conteneur, assurez-vous qu’il prend en charge les processus de conteneur qui s’exécutent en tant que racine. Le processus sqlservr dans le conteneur s’exécute en tant que racine.

- Examinez le [les journaux d’erreur et le programme d’installation de SQL Server](#errorlogs).

### <a name="sql-server-connection-failures"></a>Échecs de connexion SQL Server

Si vous ne peut pas se connecter à l’instance de SQL Server en cours d’exécution dans votre conteneur, essayez les tests suivants :

- Assurez-vous que votre conteneur de SQL Server est en cours d’exécution en examinant le **état** colonne de la `docker ps -a` sortie. Dans le cas contraire, utilisez `docker start <Container ID>` pour le démarrer.

- Si vous avez mappé à un port d’hôte non-par défaut (pas 1433), assurez-vous que vous spécifiez le port dans votre chaîne de connexion. Vous pouvez voir votre mappage de port dans le **PORTS** colonne de la `docker ps -a` sortie. Par exemple, la commande suivante établit une connexion sqlcmd à un conteneur à l’écoute sur le port 1401 :

    ```bash
    sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
    ```

    ```PowerShell
    sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
    ```

- Si vous avez utilisé `docker run` avec un volume de données mappé existant ou un conteneur de volumes de données, SQL Server ignore la valeur de `MSSQL_SA_PASSWORD`. Au lieu de cela, le mot de passe SA préconfiguré est utilisé à partir des données dans le volume de données ou le conteneur de volume de données SQL Server. Vérifiez que vous utilisez le mot de passe SA associé aux données que vous joignez à.

- Examinez le [les journaux d’erreur et le programme d’installation de SQL Server](#errorlogs).

### <a name="sql-server-availability-groups"></a>Groupes de disponibilité SQL Server

Si vous utilisez Docker avec groupes de disponibilité de SQL Server, il existe deux autres exigences.

- Mappez le port qui est utilisé pour la communication de réplica (valeur par défaut 5022). Par exemple, spécifier `-p 5022:5022` dans le cadre de votre `docker run` commande.

- Définir explicitement le nom d’hôte de conteneur avec le `-h YOURHOSTNAME` paramètre de la `docker run` commande. Ce nom d’hôte est utilisé lorsque vous configurez votre groupe de disponibilité. Si vous ne spécifiez pas avec `-h`, la valeur par défaut à l’ID de conteneur.

### <a id="errorlogs"></a>Journaux d’erreur et le programme d’installation de SQL Server

Vous pouvez examiner le programme d’installation de SQL Server et les journaux d’erreurs **/var/opt/mssql/log**. Si le conteneur n’est pas exécuté, d’abord démarrer le conteneur. Puis utilisez une invite de commandes interactive pour inspecter les journaux.

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

Prise en main SQL Server 2017 les images de conteneur sur Docker en passant par le [didacticiel de démarrage rapide](quickstart-install-connect-docker.md).

Consultez également le [référentiel GitHub de docker de mssql](https://github.com/Microsoft/mssql-docker) des ressources, des commentaires et problèmes connus.

