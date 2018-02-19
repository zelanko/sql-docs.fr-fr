---
title: "Résoudre les problèmes de SQL Server sur Linux | Documents Microsoft"
description: "Fournit des conseils de dépannage pour l’utilisation de SQL Server 2017 sur Linux."
author: annashres
ms.author: anshrest
manager: craigg
ms.date: 01/18/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 99636ee8-2ba6-4316-88e0-121988eebcf9S
ms.workload: On Demand
ms.openlocfilehash: f56806313075865c53cbd3fc1f80c0d132804c04
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="troubleshoot-sql-server-on-linux"></a>Résoudre les problèmes de SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ce document décrit comment résoudre les problèmes de Microsoft SQL Server s'exécutant sur Linux ou dans un conteneur Docker. Lors du dépannage de SQL Server sur Linux, n’oubliez pas de consulter les fonctionnalités prises en charge et les limitations connues dans les [notes de publication de SQL Server sur Linux](sql-server-linux-release-notes.md).

## <a id="connection"></a> Résoudre les échecs de connexion
Si vous rencontrez des difficultés pour vous connecter à votre serveur SQL de Linux, il existe quelques éléments à vérifier. 

- Vérifiez que le nom du serveur ou l’adresse IP est accessible à partir de votre ordinateur client.

   > [!TIP]
   > Pour rechercher l’adresse IP de votre machine Ubuntu, vous pouvez exécuter la commande ifconfig comme dans l’exemple suivant :
   >
   >   ```bash
   >   sudo ifconfig eth0 | grep 'inet addr'
   >   ```
   > Pour Red Hat, vous pouvez utiliser l’adresse ip, comme dans l’exemple suivant :
   >
   >   ```bash
   >   sudo ip addr show eth0 | grep "inet"
   >   ```
   > Une exception à cette technique relative aux machines virtuelles Azure. Pour les machines virtuelles Azure, [rechercher l’adresse IP publique de l’ordinateur virtuel dans le portail Azure](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine#connect).

- Le cas échéant, vérifiez que vous avez ouvert le port SQL Server (1433 par défaut) sur le pare-feu.

- Pour les machines virtuelles Azure, vérifiez que vous avez une [règle de groupe de sécurité réseau pour le port de SQL Server par défaut](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine#remote).

- Vérifiez que le nom d’utilisateur et un mot de passe ne contiennent pas de fautes de frappe ou espaces ni d’une casse incorrecte.

- Essayez de définir explicitement le numéro de port et de protocole avec le nom du serveur à l’exemple suivant : **tcp:servername, 1433**.

- Des problèmes de connectivité réseau peuvent également entraîner des délais d’attente et des erreurs de connexion. Après avoir vérifié vos informations de connexion et la connectivité réseau, recommencez l’opération.

## <a name="manage-the-sql-server-service"></a>Gérer le service SQL Server

Les sections suivantes montrent comment démarrer, arrêter, redémarrer et vérifier l’état du service SQL Server. 

### <a name="manage-the-mssql-server-service-in-red-hat-enterprise-linux-rhel-and-ubuntu"></a>Gérer le service mssql-serveur Red Hat Enterprise Linux (RHEL) et Ubuntu 

Vérifiez l’état du service SQL Server à l’aide de cette commande :

   ```bash
   sudo systemctl status mssql-server
   ```

Vous pouvez arrêter, démarrer ou redémarrer le service SQL Server en fonction des besoins à l’aide des commandes suivantes :

   ```bash
   sudo systemctl stop mssql-server
   sudo systemctl start mssql-server
   sudo systemctl restart mssql-server
   ```

### <a name="manage-the-execution-of-the-mssql-docker-container"></a>Gérer l’exécution du conteneur Docker mssql

Vous pouvez obtenir l’ID de conteneur et d’état du dernier conteneur Docker de serveur SQL créé en exécutant la commande suivante (l’ID est sous le **ID de conteneur** colonne) :

   ```bash
   sudo docker ps -l
   ```
   
Vous pouvez arrêter ou redémarrer le service SQL Server en fonction des besoins à l’aide des commandes suivantes :
   
   ```bash
   sudo docker stop <container ID>
   sudo docker restart <container ID>
   ```

> [!TIP]
> Pour obtenir des conseils de dépannage supplémentaires pour Docker, consultez [conteneurs dépannage de SQL Server Docker](sql-server-linux-configure-docker.md#troubleshooting).

## <a name="access-the-log-files"></a>Accéder aux fichiers journaux
   
Les journaux de moteur SQL Server dans le fichier /var/opt/mssql/log/errorlog dans les installations de Linux et de Docker. Vous devez être en mode de 'super utilisateur' pour parcourir ce répertoire.

Le programme d’installation enregistre ici : / var/opt/mssql/le programme d’installation-< horodatage qui représente la durée d’installation > vous pouvez parcourir les fichiers du journal des erreurs avec n’importe quel outil compatible UTF-16 comme « vim » ou « cat » comme suit : 

   ```bash
   sudo cat errorlog
   ```

Si vous préférez, vous pouvez également convertir les fichiers UTF-8 pour les lire avec « plus » ou « moins » avec la commande suivante :
   
   ```bash
   sudo iconv –f UTF-16LE –t UTF-8 <errorlog> -o <output errorlog file>
   ```
## <a name="extended-events"></a>Événements étendus

Événements étendus peuvent être interrogées via une commande SQL.  Plus d’informations sur les événements étendus sont accessibles [ici](https://technet.microsoft.com/en-us/library/bb630282.aspx):

## <a name="crash-dumps"></a>Vidages sur incident 

Recherchez les vidages dans le répertoire de journal dans Linux. Vérifiez dans le répertoire /var/opt/mssql/log pour Linux Core dumps (. tar.gz2 extension) ou SQL minidumps (extension .mdmp)

Pour les vidages 
   ```bash
   sudo ls /var/opt/mssql/log | grep .tar.gz2 
   ```

Pour les sauvegardes SQL 
   ```bash
   sudo ls /var/opt/mssql/log | grep .mdmp 
   ```
   
## <a name="start-sql-server-in-minimal-configuration-or-in-single-user-mode"></a>Démarrage de SQL Server dans une Configuration minimale ou en Mode mono-utilisateur

### <a name="start-sql-server-in-minimal-configuration-mode"></a>Démarrage de SQL Server en Mode Configuration minimale
Cette option est utile lorsqu'une valeur de configuration définie (espace mémoire insuffisant, par exemple) a empêché le serveur de démarrer.
  
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -f
   ```

### <a name="start-sql-server-in-single-user-mode"></a>Démarrage de SQL Server en Mode mono-utilisateur
Dans certaines circonstances, vous devrez peut-être démarrer une instance de SQL Server en mode mono-utilisateur à l’aide de l’option de démarrage -m. Vous pouvez par exemple vouloir modifier les options de configuration du serveur ou rétablir une base de données master ou une autre base de données système endommagées. Par exemple, vous souhaiterez modifier les options de configuration de serveur ou rétablir une base de données master endommagée ou une autre base de données système   

Démarrage de SQL Server en Mode mono-utilisateur
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -m
   ```

Démarrage de SQL Server en Mode mono-utilisateur avec SQLCMD
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -m SQLCMD
   ```
  
> [!WARNING]  
>  Démarrez SQL Server sur Linux avec l’utilisateur « mssql » afin d’éviter les problèmes de démarrage futurs. Exemple « sudo -u mssql /opt/mssql/bin/sqlservr [OPTIONS DE DÉMARRAGE] » 

Si vous avez démarré par inadvertance SQL Server avec un autre utilisateur, vous devez modifier la propriété des fichiers de base de données SQL Server à l’utilisateur 'mssql' avant de démarrer SQL Server avec systemd. Par exemple, exécutez la commande suivante pour modifier la propriété de tous les fichiers de base de données sous /var/opt/mssql à l’utilisateur « mssql »,

   ```bash
   chown -R mssql:mssql /var/opt/mssql/
   ```

## <a name="common-issues"></a>Problèmes courants

1. Impossible de se connecter à votre instance de SQL Server à distance.

   Consultez la section Dépannage de l’article, [se connecter à SQL Server sur Linux](#connection).

2. Erreur : Nom d’hôte doit être de 15 caractères ou moins.

   Il s’agit d’un problème connu qui se produit chaque fois que le nom de l’ordinateur qui tente d’installer le package Debian SQL Server est supérieur à 15 caractères. Il n’existe actuellement aucune solution de contournement autre que la modification du nom de l’ordinateur. Une façon d’effectuer cette opération est en modifiant le fichier de nom d’hôte et de redémarrer l’ordinateur. Les éléments suivants [guide du site Web](http://www.cyberciti.biz/faq/ubuntu-change-hostname-command/) Cela explique en détail.

3. La réinitialisation de mot de passe système (SA) d’administration.

   Si vous avez oublié le mot de passe d’administrateur système ou que vous devez le réinitialiser pour une raison quelconque, procédez comme suit.

   > [!NOTE]
   > Les étapes suivantes arrêter le service SQL Server temporairement.

   Se connecter dans le terminal de l’ordinateur hôte, exécutez les commandes suivantes, suivez les invites pour réinitialiser le mot de passe SA :

   ```bash
   sudo systemctl stop mssql-server
   sudo /opt/mssql/bin/mssql-conf setup
   ```

4. À l’aide de caractères spéciaux dans le mot de passe.

   Si vous utilisez des caractères dans le mot de passe du compte de connexion SQL Server, vous devrez peut-être d’échappement lors de leur utilisation dans le terminal Linux. Vous devez isoler le $ à tout moment à l’aide de la barre oblique vous l’utilisez dans un script de shell de commande/Terminal Server :

   Ne fonctionne pas :

   ```bash
   sudo sqlcmd -S myserver -U sa -P Test$$
   ```

   Fonctionne :

   ```bash
   sqlcmd -S myserver -U sa -P Test\$\$
   ```

   Ressources : [des caractères spéciaux](http://tldp.org/LDP/abs/html/special-chars.html)
   [Escaping](http://tldp.org/LDP/abs/html/escapingsection.html)

## <a name="support"></a>Support technique

Le support est disponible via la Communauté et surveillé par l’équipe d’ingénierie. Pour des questions spécifiques, utilisez les ressources suivantes :

- [Stack Exchange DBA](https://dba.stackexchange.com/questions/tagged/sql-server): Poser des questions sur l’administration de base de données
- [Stack Overflow](http://stackoverflow.com/questions/tagged/sql-server): Poser des questions sur le développement
- [Forums MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver): Poser des questions techniques
- [Envoyer des commentaires](https://feedback.azure.com/forums/908035-sql-server): signaler des bogues et la fonctionnalité de demande
- [Reddit](https://www.reddit.com/r/SQLServer/): Discuter de SQL Server
