---
title: "Résoudre les problèmes de SQL Server sur Linux | Documents Microsoft"
description: "Fournit des conseils de dépannage pour l’utilisation de SQL Server 2017 sur Linux."
author: annashres
ms.author: anshrest
manager: jhubbard
ms.date: 05/08/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 99636ee8-2ba6-4316-88e0-121988eebcf9S
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 21b7d94bcf15e1ae2d99dd44f4b0030929b92111
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="troubleshoot-sql-server-on-linux"></a>Résoudre les problèmes de SQL Server sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

Ce document décrit comment résoudre les problèmes de Microsoft SQL Server est en cours d’exécution sur Linux ou dans un conteneur Docker. Lors du dépannage de SQL Server sur Linux, veuillez vous n’oubliez pas les limitations de cette version préliminaire privée. Vous trouverez une liste de ces éléments dans le [Notes de publication](sql-server-linux-release-notes.md).

## <a id="connection"></a>Résoudre les échecs de connexion
Si vous rencontrez des difficultés à se connecter à votre serveur SQL de Linux, il existe quelques éléments à vérifier. 

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
   > Une exception à cette technique relative aux machines virtuelles Azure. Pour les machines virtuelles Azure, [rechercher l’adresse IP publique de l’ordinateur virtuel dans le portail Azure](sql-server-linux-azure-virtual-machine.md#connect).

- Le cas échéant, vérifiez que vous avez ouvert le port SQL Server (1433 par défaut) sur le pare-feu.

- Pour les machines virtuelles Azure, vérifiez que vous avez un [règle de groupe de sécurité réseau pour le port de SQL Server par défaut](sql-server-linux-azure-virtual-machine.md#remote).

- Vérifiez que le nom d’utilisateur et un mot de passe ne contiennent pas de fautes de frappe ou espaces ni d’une casse incorrecte.

- Essayez de définir explicitement le numéro de port et de protocole avec le nom du serveur comme suit : **tcp:servername, 1433**.

- Problèmes de connectivité réseau peuvent également entraîner des délais d’attente et les erreurs de connexion. Après avoir vérifié vos informations de connexion et la connectivité réseau, recommencez l’opération.

## <a name="manage-the-sql-server-service"></a>Gérer le service SQL Server

Les sections suivantes montrent comment démarrer, arrêter, redémarrer et vérifier l’état du service SQL Server. 

### <a name="manage-the-mssql-server-service-in-red-hat-enterprise-linux-rhel-and-ubuntu"></a>Gérer le service mssql-serveur Red Hat Enterprise Linux (RHEL) et Ubuntu 

Vérifiez l’état de l’état du service SQL Server à l’aide de cette commande :

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

Vous pouvez obtenir l’ID de conteneur et d’état du dernier conteneur Docker de serveur SQL créé en exécutant la commande suivante (l’ID sera sous la colonne « ID de conteneur ») :

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
   
Les journaux de moteur SQL Server dans le fichier /var/opt/mssql/log/errorlog dans les installations de Linux et de Docker. Vous devez être en mode de 'super ' utilisateur à parcourir ce répertoire.

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

## <a name="common-issues"></a>Problèmes courants

1. Vous ne pouvez pas vous connecter à votre instance de SQL Server à distance.

   Consultez la section Dépannage de la rubrique, [se connecter à SQL Server sur Linux](#connection).

2. Erreur : Nom d’hôte doit être de 15 caractères ou moins.

   Il s’agit d’un problème connu qui se produit chaque fois que le nom de l’ordinateur qui tente d’installer le package Debian SQL Server est supérieur à 15 caractères. Il n’existe actuellement aucune solution de contournement autre que la modification du nom de l’ordinateur. Une façon d’effectuer cette opération est en modifiant le fichier de nom d’hôte et de redémarrer l’ordinateur. Les éléments suivants [guide du site Web](http://www.cyberciti.biz/faq/ubuntu-change-hostname-command/) Cela explique en détail.

3. La réinitialisation de mot de passe système (SA) d’administration.

   Si vous avez oublié le mot de passe d’administrateur système ou que vous devez le réinitialiser pour une raison quelconque, procédez comme suit.

   > [!NOTE]
   > Procédez comme suit arrêtez temporairement le service SQL Server.

   Journal dans le terminal de l’ordinateur hôte, exécutez les commandes suivantes, suivez les invites pour réinitialiser le mot de passe SA :

   ```bash
   sudo systemctl stop mssql-server
   sudo /opt/mssql/bin/mssql-conf setup
   ```

4. À l’aide de caractères spéciaux dans le mot de passe.

   Si vous utilisez des caractères dans le mot de passe du compte de connexion SQL Server, vous devrez peut-être d’échappement lors de leur utilisation dans le terminal Linux. Vous devez échapper la $ à tout moment à l’aide de la barre oblique vous l’utilisez dans un script de shell de commande/Terminal Server :

   Ne fonctionne pas :

   ```bash
   sudo sqlcmd -S myserver -U sa -P Test$$
   ```

   Fonctionnement :

   ```bash
   sqlcmd -S myserver -U sa -P Test\$\$
   ```

   Ressources : [des caractères spéciaux](http://tldp.org/LDP/abs/html/special-chars.html)
   [Escaping](http://tldp.org/LDP/abs/html/escapingsection.html)

## <a name="support"></a>Support technique

Prise en charge est disponible via la Communauté et surveillé par l’équipe d’ingénierie. Pour des questions spécifiques, utilisez les ressources suivantes :

- [Échange de pile DBA](https://dba.stackexchange.com/questions/tagged/sql-server): poser des questions d’administration de base de données
- [Dépassement de capacité de la pile](http://stackoverflow.com/questions/tagged/sql-server): poser des questions sur le développement
- [Forums MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver): poser des questions techniques
- [Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback): signaler des bogues et la fonctionnalité de demande
- [Reddit](https://www.reddit.com/r/SQLServer/): traitent de SQL Server
