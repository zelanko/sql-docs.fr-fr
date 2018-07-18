---
title: Configurer les paramètres de SQL Server sur Linux | Microsoft Docs
description: Cet article décrit comment utiliser l’outil mssql-conf pour configurer les paramètres de SQL Server 2017 sur Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 06/22/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 06798dff-65c7-43e0-9ab3-ffb23374b322
ms.openlocfilehash: 3a919f19b0b1aaef4702ac9d6e456cb9c5cf1357
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982471"
---
# <a name="configure-sql-server-on-linux-with-the-mssql-conf-tool"></a>Configurer SQL Server sur Linux avec l’outil mssql-conf

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

**MSSQL-conf** est un script de configuration qui s’installe avec SQL Server 2017 pour Red Hat Enterprise Linux, SUSE Linux Enterprise Server et Ubuntu. Vous pouvez utiliser cet utilitaire pour définir les paramètres suivants :

|||
|---|---|
| [Agent](#agent) | Activer l’Agent SQL Server |
| [Classement](#collation) | Définir un nouveau classement pour SQL Server sur Linux. |
| [Commentaires des clients](#customerfeedback) | Choisissez ou non SQL Server envoie des commentaires à Microsoft. |
| [Profil de messagerie de base de données](#dbmail) | Définissez le profil de messagerie de base de données par défaut de SQL Server sur Linux |
| [Répertoire de données par défaut](#datadir) | Remplacez le répertoire par défaut pour les nouveaux fichiers de données de base de données SQL Server (.mdf). |
| [Répertoire de journal par défaut](#datadir) | Change le répertoire par défaut pour les nouveaux fichiers de journal (.ldf) de base de données SQL Server. |
| [Répertoire de fichier de base de données master par défaut](#masterdatabasedir) | Change le répertoire par défaut pour les fichiers de base de données master sur l’installation existante de SQL.|
| [Nom de fichier de base de données master par défaut](#masterdatabasename) | Modifie le nom des fichiers de base de données master. |
| [Répertoire de vidage par défaut](#dumpdir) | Remplacez le répertoire par défaut pour les nouvelles images mémoire et d’autres fichiers de résolution des problèmes. |
| [Répertoire de journal d’erreur par défaut](#errorlogdir) | Change le répertoire par défaut pour les nouveaux fichiers de journal des erreurs de SQL Server, la Trace de Profiler par défaut, XE de Session de contrôle d’intégrité système et Hekaton Session XE. |
| [Répertoire de sauvegarde par défaut](#backupdir) | Remplacez le répertoire par défaut pour les nouveaux fichiers de sauvegarde. |
| [Type de vidage](#coredump) | Choisissez le type de fichier de vidage de mémoire de vidage à collecter. |
| [Haute disponibilité](#hadr) | Activer les groupes de disponibilité. |
| [Répertoire d’Audit local](#localaudit) | Définir un répertoire à ajouter des fichiers d’Audit Local. |
| [Paramètres régionaux](#lcid) | Définir les paramètres régionaux pour SQL Server à utiliser. |
| [Limite de mémoire](#memorylimit) | Définir la limite de mémoire pour SQL Server. |
| [Port TCP](#tcpport) | Modifiez le port sur lequel SQL Server écoute les connexions. |
| [TLS](#tls) | Configurer la sécurité de niveau Transport. |
| [Indicateurs de trace](#traceflags) | Définir les indicateurs de trace qui va utiliser le service. |

> [!TIP]
> Certains de ces paramètres peuvent également être configuré avec les variables d’environnement. Pour plus d’informations, consultez [des paramètres de configuration de SQL Server avec les variables d’environnement](sql-server-linux-configure-environment-variables.md).

## <a name="usage-tips"></a>Conseils d’utilisation

* Pour les groupes de disponibilité AlwaysOn et les clusters de disque partagé, vous devez toujours apporter les mêmes modifications de configuration sur chaque nœud.

* Pour le scénario de cluster de disque partagé, n’essayez pas de redémarrer le **mssql-server** service pour appliquer les modifications. SQL Server s’exécute en tant qu’application. Au lieu de cela, de mettre la ressource puis en ligne et hors connexion.

* Ces exemples exécuter mssql-conf par spécifient le chemin d’accès complet : **/opt/mssql/bin/mssql-conf**. Si vous choisissez accéder à ce chemin d’accès au lieu de cela, exécutez mssql-conf dans le contexte du répertoire actif : **. / mssql-conf**.

## <a id="agent"></a> Activer l’Agent SQL Server

Le **sqlagent.enabled** définition active [Agent SQL Server](sql-server-linux-run-sql-server-agent-job.md). Par défaut, SQL Server Agent est désactivé. Si **sqlagent.enabled** n’est pas présent dans le fichier de paramètres mssql.conf, puis SQL Server en interne part du principe que SQL Server Agent est désactivé.

Pour modifier ces paramètres, utilisez les étapes suivantes :

1. Activer l’Agent SQL Server :

   ```bash
   sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
   ```

1. Redémarrez le service SQL Server :

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="collation"></a> Modifier le classement de SQL Server

Le **set-classement** option modifie la valeur de classement à l’un des classements pris en charge.

1. Première [sauvegarde des bases de données utilisateur](sql-server-linux-backup-and-restore-database.md) sur votre serveur.

1. Utilisez ensuite le [sp_detach_db](../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md) procédure stockée pour détacher les bases de données utilisateur.

1. Exécutez le **set-classement** option et suivez les invites :

   ```bash
   sudo /opt/mssql/bin/mssql-conf set-collation
   ```

1. L’utilitaire mssql-conf tente de modifier la valeur de classement spécifié et redémarrez le service. S’il existe des erreurs, il restaure le classement à la valeur précédente.

1. Restaurer vos sauvegardes de base de données utilisateur.

Pour obtenir la liste des classements pris en charge, exécutez le [sys.fn_helpcollations](../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md) fonction : `SELECT Name from sys.fn_helpcollations()`.

## <a id="customerfeedback"></a> Configurer les commentaires des clients

Le **telemetry.customerfeedback** changements de paramètre, si SQL Server envoie des commentaires à Microsoft ou non. Par défaut, cette valeur est définie **true** pour toutes les éditions. Pour modifier la valeur, exécutez les commandes suivantes :

> [!IMPORTANT]
> Vous ne pouvez pas désactiver les commentaires des clients gratuitement éditions de SQL Server, Express et Developer.

1. Exécutez le script mssql-conf en tant que root avec la **définir** commande **telemetry.customerfeedback**. L’exemple suivant désactive les commentaires des clients en spécifiant **false**.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.customerfeedback false
   ```

1. Redémarrez le service SQL Server :

   ```bash
   sudo systemctl restart mssql-server
   ```

Pour plus d’informations, consultez [commentaires des clients pour SQL Server sur Linux](sql-server-linux-customer-feedback.md) et [SQL Server Privacy Statement](http://go.microsoft.com/fwlink/?LinkID=868444).

## <a id="datadir"></a> Modifier l’emplacement de répertoire de données ou journal par défaut

Le **filelocation.defaultdatadir** et **filelocation.defaultlogdir** paramètres modifier l’emplacement où les nouvelle base de données et les fichiers journaux sont créés. Par défaut, cet emplacement est /var/opt/mssql/data. Pour modifier ces paramètres, utilisez les étapes suivantes :

1. Créer le répertoire cible pour la nouvelle base de données de données et les fichiers journaux. L’exemple suivant crée un nouveau **/tmp/data** directory :

   ```bash
   sudo mkdir /tmp/data
   ```

1. Modifier le propriétaire et le groupe du répertoire à la **mssql** utilisateur :

   ```bash
   sudo chown mssql /tmp/data
   sudo chgrp mssql /tmp/data
   ```

1. Mssql-conf permet de modifier le répertoire de données par défaut avec le **définir** commande :

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultdatadir /tmp/data
   ```

1. Redémarrez le service SQL Server :

   ```bash
   sudo systemctl restart mssql-server
   ```

1. Tous les fichiers de base de données pour les nouvelles bases de données seront désormais être stockés dans ce nouvel emplacement. Si vous souhaitez modifier l’emplacement des fichiers journaux (.ldf) de nouvelles bases de données, vous pouvez utiliser la commande « set » suivantes :

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultlogdir /tmp/log
   ```

1. Cette commande suppose également qu’un répertoire de journal/tmp/existe et qu’il est sous l’utilisateur et le groupe **mssql**.


## <a id="masterdatabasedir"></a> Modifier l’emplacement de répertoire de fichiers de base de données master par défaut

Le **filelocation.masterdatafile** et **filelocation.masterlogfile** définition modifie l’emplacement où le moteur SQL Server recherche les fichiers de base de données master. Par défaut, cet emplacement est /var/opt/mssql/data. 

Pour modifier ces paramètres, utilisez les étapes suivantes :

1. Créer le répertoire cible pour les nouveaux fichiers journaux des erreurs. L’exemple suivant crée un nouveau **/tmp/masterdatabasedir** directory :

   ```bash
   sudo mkdir /tmp/masterdatabasedir
   ```

1. Modifier le propriétaire et le groupe du répertoire à la **mssql** utilisateur :

   ```bash
   sudo chown mssql /tmp/masterdatabasedir
   sudo chgrp mssql /tmp/masterdatabasedir
   ```

1. Mssql-conf permet de modifier le répertoire de base de données master par défaut pour les fichiers journaux et de données master avec le **définir** commande :

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /tmp/masterdatabasedir/master.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterlogfile /tmp/masterdatabasedir/mastlog.ldf
   ```

1. Arrêtez le service SQL Server :

   ```bash
   sudo systemctl stop mssql-server
   ```

1. Déplacer le master.mdf et masterlog.ldf : 

   ```bash
   sudo mv /var/opt/mssql/data/master.mdf /tmp/masterdatabasedir/master.mdf 
   sudo mv /var/opt/mssql/data/mastlog.ldf /tmp/masterdatabasedir/mastlog.ldf
   ```

1. Démarrez le service SQL Server :

   ```bash
   sudo systemctl start mssql-server
   ```
   
> [!NOTE]
> Si SQL Server ne peut pas trouver les fichiers master.mdf et mastlog.ldf dans le répertoire spécifié, une copie basés sur des modèles de bases de données système sera automatiquement créée dans le répertoire spécifié, et SQL Server démarrera avec succès. Toutefois, métadonnées, telles que les bases de données utilisateur, les connexions serveur, des certificats de serveur, clés de chiffrement, les travaux de l’agent SQL ou ancien mot de passe de connexion SA ne seront pas mis à jour dans la base de données master. Vous devrez arrêter SQL Server et de déplacer votre ancien master.mdf mastlog.ldf vers le nouvel emplacement spécifié et de démarrage de SQL Server pour continuer à utiliser les métadonnées existantes. 


## <a id="masterdatabasename"></a> Modifier le nom des fichiers de base de données master.

Le **filelocation.masterdatafile** et **filelocation.masterlogfile** définition modifie l’emplacement où le moteur SQL Server recherche les fichiers de base de données master. Par défaut, cet emplacement est /var/opt/mssql/data. Pour modifier ces paramètres, utilisez les étapes suivantes :

1. Arrêtez le service SQL Server :

   ```bash
   sudo systemctl stop mssql-server
   ```

1. Mssql-conf permet de modifier les noms de base de données master attendu pour les fichiers journaux et de données master avec le **définir** commande :

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /var/opt/mssql/data/masternew.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.mastlogfile /var/opt/mssql/data /mastlognew.ldf
   ```

1. Modifier le nom des base de données master données et fichiers journaux 

   ```bash
   sudo mv /var/opt/mssql/data/master.mdf /var/opt/mssql/data/masternew.mdf
   sudo mv /var/opt/mssql/data/mastlog.ldf /var/opt/mssql/data/mastlognew.ldf
   ```

1. Démarrez le service SQL Server :

   ```bash
   sudo systemctl start mssql-server
   ```



## <a id="dumpdir"></a> Modifier l’emplacement par défaut du répertoire de vidage

Le **filelocation.defaultdumpdir** l’emplacement par défaut où la mémoire et les sauvegardes SQL sont générés chaque fois qu’un incident de changements de paramètre. Par défaut, ces fichiers sont générés dans /var/opt/mssql/log.

Pour configurer ce nouvel emplacement, utilisez les commandes suivantes :

1. Créer le répertoire cible pour les nouveaux fichiers de vidage. L’exemple suivant crée un nouveau **/tmp/dump** directory :

   ```bash
   sudo mkdir /tmp/dump
   ```

1. Modifier le propriétaire et le groupe du répertoire à la **mssql** utilisateur :

   ```bash
   sudo chown mssql /tmp/dump
   sudo chgrp mssql /tmp/dump
   ```

1. Mssql-conf permet de modifier le répertoire de données par défaut avec le **définir** commande :

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultdumpdir /tmp/dump
   ```

1. Redémarrez le service SQL Server :

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="errorlogdir"></a> Modifier l’emplacement directory par défaut des fichiers de journal des erreurs

Le **filelocation.errorlogfile** définition modifie l’emplacement où le nouveau journal des erreurs, la trace du Générateur de profils par défaut, la session de contrôle d’intégrité système XE et les fichiers de session XE Hekaton sont créés. Par défaut, cet emplacement est /var/opt/mssql/log. Le répertoire dans lequel le fichier errorlog SQL est défini devient le répertoire de journal par défaut pour les autres journaux.

Pour modifier ces paramètres :

1. Créer le répertoire cible pour les nouveaux fichiers journaux des erreurs. L’exemple suivant crée un nouveau **/tmp/logs** directory :

   ```bash
   sudo mkdir /tmp/logs
   ```

1. Modifier le propriétaire et le groupe du répertoire à la **mssql** utilisateur :

   ```bash
   sudo chown mssql /tmp/logs
   sudo chgrp mssql /tmp/logs
   ```

1. Mssql-conf permet de modifier le nom de fichier du journal des erreurs par défaut avec le **définir** commande :

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.errorlogfile /tmp/logs/errorlog
   ```

1. Redémarrez le service SQL Server :

   ```bash
   sudo systemctl restart mssql-server
   ```


## <a id="backupdir"></a> Modifier l’emplacement du répertoire de sauvegarde par défaut

Le **filelocation.defaultbackupdir** changements de paramètre de l’emplacement par défaut où les fichiers de sauvegarde sont générés. Par défaut, ces fichiers sont générés dans /var/opt/mssql/data.

Pour configurer ce nouvel emplacement, utilisez les commandes suivantes :

1. Créer le répertoire cible pour les nouveaux fichiers de sauvegarde. L’exemple suivant crée un nouveau **/tmp/backup** directory :

   ```bash
   sudo mkdir /tmp/backup
   ```

1. Modifier le propriétaire et le groupe du répertoire à la **mssql** utilisateur :

   ```bash
   sudo chown mssql /tmp/backup
   sudo chgrp mssql /tmp/backup
   ```

1. Mssql-conf permet de modifier le répertoire de sauvegarde par défaut avec la commande « set » :

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultbackupdir /tmp/backup
   ```

1. Redémarrez le service SQL Server :

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="coredump"></a> Spécifier les paramètres de vidage

Si une exception se produit dans un processus SQL Server, SQL Server crée une image mémoire.

Il existe deux options pour contrôler le type de mémoire vide que SQL Server collecte : **coredump.coredumptype** et **coredump.captureminiandfull**. Ils concernent les deux phases de la capture d’image mémoire principal. 

La première capture phase est contrôlée par le **coredump.coredumptype** paramètre, qui détermine le type de fichier de vidage généré au cours d’une exception. La deuxième phase est activé lorsque la **coredump.captureminiandfull** paramètre. Si **coredump.captureminiandfull** est défini sur true, le vidage de fichier spécifié par **coredump.coredumptype** est généré et un deuxième vidage minimal est également généré. Paramètre **coredump.captureminiandfull** false désactive la capture du deuxième tentative.

1. Décider s’il faut capturer les vidages sur incident mini-vidages et complètes avec le **coredump.captureminiandfull** paramètre.

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.captureminiandfull <true or false>
    ```

    Par défaut : **false**

1. Spécifiez le type de fichier dump avec le **coredump.coredumptype** paramètre.

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.coredumptype <dump_type>
    ```

    Par défaut : **miniplus**

    Le tableau suivant répertorie les possibles **coredump.coredumptype** valeurs.

    | Type | Description |
    |-----|-----|
    | **Mini** | Mini est le plus petit type de fichier de vidage. Il utilise les informations de système Linux pour déterminer les threads et les modules dans le processus. L’image mémoire contient uniquement les modules et les piles de threads d’environnement hôte. Il ne contient pas de références de mémoire indirect ou des variables globales. |
    | **miniplus** | MiniPlus est similaire à mini, mais il inclut la mémoire supplémentaire. Il comprend les mécanismes internes de SQLPAL et de l’environnement hôte, en ajoutant les régions de mémoire suivantes pour le vidage :</br></br> -Globals divers</br> -Toute la mémoire supérieures à 64 To</br> -All nommé trouvées dans des régions **$ / proc / pid/mappages**</br> -Mémoire indirecte des threads et de piles</br> -Informations sur le thread</br> -Associé du Teb et de Peb</br> -Module informations</br> -VMM et VAD arborescence |
    | **filtré** | Conception utilise filtré en fonction des soustraction où toute la mémoire dans le processus est incluse, sauf si spécifiquement exclus. La conception comprend les mécanismes internes de SQLPAL et de l’environnement hôte, à l’exclusion de certaines régions à partir de l’image mémoire.
    | **complet** | Complète un vidage de processus complet qui inclut toutes les régions se trouve dans **/proc / $pid/mappages**. Cela n’est pas contrôlé par **coredump.captureminiandfull** paramètre. |

## <a id="dbmail"></a> Définissez le profil de messagerie de base de données par défaut de SQL Server sur Linux

Le **sqlpagent.databasemailprofile** vous permet de définir le profil de messagerie de base de données par défaut pour les alertes par courrier électronique.

```bash
sudo /opt/mssq/bin/mssql-conf set sqlagent.databasemailprofile <profile_name>
```
## <a id="hadr"></a> Haute disponibilité

Le **hadr.hadrenabled** option active les groupes de disponibilité sur votre instance de SQL Server. La commande suivante active les groupes de disponibilité en définissant **hadr.hadrenabled** à 1. Vous devez redémarrer SQL Server pour le paramètre prenne effet.

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

Pour plus d’informations comment il est utilisé avec les groupes de disponibilité, consultez les deux rubriques suivantes.

- [Configurez toujours sur le groupe de disponibilité pour SQL Server sur Linux](sql-server-linux-availability-group-configure-ha.md)
- [Configurer le groupe de disponibilité avec échelle lecture pour SQL Server sur Linux](sql-server-linux-availability-group-configure-rs.md)

## <a id="localaudit"></a> Répertoire d’audit local du jeu

Le **telemetry.userrequestedlocalauditdirectory** paramètre Active l’Audit Local et vous permet de définir le répertoire où les journaux de l’Audit Local est créés.

1. Créez un répertoire cible pour les nouveaux journaux d’Audit Local. L’exemple suivant crée un nouveau **/tmp/audit** directory :

   ```bash
   sudo mkdir /tmp/audit
   ```

1. Modifier le propriétaire et le groupe du répertoire à la **mssql** utilisateur :

   ```bash
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
   ```

1. Exécutez le script mssql-conf en tant que root avec la **définir** commande **telemetry.userrequestedlocalauditdirectory**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
   ```

1. Redémarrez le service SQL Server :

   ```bash
   sudo systemctl restart mssql-server
   ```

Pour plus d’informations, consultez [commentaires des clients pour SQL Server sur Linux](sql-server-linux-customer-feedback.md).

## <a id="lcid"></a> Modifier les paramètres régionaux de SQL Server

Le **language.lcid** définition modifie les paramètres régionaux de SQL Server à un identificateur de langue prise en charge (LCID). 

1. L’exemple suivant modifie les paramètres régionaux à Français (1036) :

   ```bash
   sudo /opt/mssql/bin/mssql-conf set language.lcid 1036
   ```

1. Redémarrez le service SQL Server pour appliquer les modifications :

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="memorylimit"></a> Définir la limite de mémoire

Le **memory.memorylimitmb** définir les contrôles la quantité mémoire physique (en Mo) disponible pour SQL Server. La valeur par défaut est 80 % de la mémoire physique.

1. Exécutez le script mssql-conf en tant que root avec la **définir** commande **memory.memorylimitmb**. L’exemple suivant modifie la mémoire disponible pour SQL Server à 3,25 Go (3328 Mo).

   ```bash
   sudo /opt/mssql/bin/mssql-conf set memory.memorylimitmb 3328
   ```

1. Redémarrez le service SQL Server pour appliquer les modifications :

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="tcpport"></a> Modifier le port TCP

Le **network.tcpport** le port TCP où SQL Server écoute les connexions de changements de paramètre. Par défaut, ce port est défini sur 1433. Pour modifier le port, exécutez les commandes suivantes :

1. Exécutez le script mssql-conf en tant que root avec la commande « set » pour « network.tcpport » :

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.tcpport <new_tcp_port>
   ```

1. Redémarrez le service SQL Server :

   ```bash
   sudo systemctl restart mssql-server
   ```

1. Lors de la connexion à SQL Server maintenant, vous devez spécifier le port personnalisé avec une virgule (,) après le nom d’hôte ou adresse IP. Par exemple, pour vous connecter avec SQLCMD, vous utiliseriez la commande suivante :

   ```bash
   sqlcmd -S localhost,<new_tcp_port> -U test -P test
   ```

## <a id="tls"></a> Spécifiez les paramètres TLS

Les options suivantes configurent TLS pour une instance de SQL Server s’exécutant sur Linux.

|Option |Description |
|--- |--- |
|**Network.ForceEncryption** |Si 1, puis [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] force toutes les connexions soient chiffrés. Par défaut, cette option est 0. |
|**network.tlscert** |Le chemin d’accès absolu au certificat de fichiers qui [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilise pour TLS. Exemple : `/etc/ssl/certs/mssql.pem` le fichier de certificat doit être accessible par le compte mssql. Microsoft vous recommande de restreindre l’accès au fichier en utilisant `chown mssql:mssql <file>; chmod 400 <file>`. |
|**network.tlskey** |Le chemin d’accès absolu à la clé privée du fichier qui [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilise pour TLS. Exemple : `/etc/ssl/private/mssql.key` le fichier de certificat doit être accessible par le compte mssql. Microsoft vous recommande de restreindre l’accès au fichier en utilisant `chown mssql:mssql <file>; chmod 400 <file>`. |
|**Network.tlsprotocols** |Une liste séparée par des virgules de quels TLS protocoles sont autorisées par SQL Server. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tente toujours de négocier le protocole autorisé plus fort. Si un client ne prend pas en charge tous les protocoles autorisés, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] rejette la tentative de connexion.  Pour assurer la compatibilité, tous les protocoles pris en charge sont autorisées par défaut (1.2, 1.1, 1.0).  Si vos clients prennent en charge TLS 1.2, Microsoft vous recommande d’autoriser uniquement TLS 1.2. |
|**network.tlsciphers** |Spécifie les chiffrements autorisés par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour TLS. Cette chaîne doit être formatée par [format de liste de chiffrement de OpenSSL](https://www.openssl.org/docs/man1.0.2/apps/ciphers.html). En règle générale, vous ne devez pas modifier cette option. <br /> Par défaut, les chiffrements suivants sont autorisés : <br /> `ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA` |
| **network.kerberoskeytabfile** |Chemin d’accès au fichier keytab Kerberos |

Pour obtenir un exemple de l’aide des paramètres TLS, consultez [chiffrement des connexions à SQL Server sur Linux](sql-server-linux-encrypted-connections.md).

## <a id="traceflags"></a> Activer/désactiver les indicateurs de trace

Cela **l’indicateur de trace** option active ou désactive les indicateurs de trace pour le démarrage du service SQL Server. Pour activer/désactiver un indicateur de trace. Utilisez les commandes suivantes :

1. Activer un indicateur de trace à l’aide de la commande suivante. Par exemple, pour l’indicateur de trace 1234 :

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 1234 on
   ```

1. Vous pouvez activer plusieurs indicateurs de trace en les spécifiant séparément :

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 2345 3456 on
   ```

1. De la même façon, vous pouvez désactiver un ou plusieurs indicateurs de trace est activées en les spécifiant et en ajoutant le **hors** paramètre :

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 1234 2345 3456 off
   ```

1. Redémarrez le service SQL Server pour appliquer les modifications :

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="remove-a-setting"></a>Supprimer un paramètre

À annuler n’importe quel paramètre effectuées avec `mssql-conf set`, appelez **mssql-conf** avec la `unset` option et le nom du paramètre. Cette opération efface le paramètre, retourner efficacement à sa valeur par défaut.

1. L’exemple suivant efface le **network.tcpport** option.

   ```bash
   sudo /opt/mssql/bin/mssql-conf unset network.tcpport
   ```

1. Redémarrez le service SQL Server.

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="view-current-settings"></a>Afficher les paramètres actuels

Pour afficher les paramètres configurés, exécutez la commande suivante pour afficher le contenu de la **mssql.conf** fichier :

```bash
sudo cat /var/opt/mssql/mssql.conf
```

Notez que tous les paramètres ne pas indiqués dans ce fichier sont à l’aide de leurs valeurs par défaut. La section suivante fournit un exemple **mssql.conf** fichier.

## <a name="mssqlconf-format"></a>format de MSSQL.conf

Ce qui suit **/var/opt/mssql/mssql.conf** fichier fournit un exemple pour chaque paramètre. Vous pouvez utiliser ce format pour apporter manuellement des modifications à la **mssql.conf** de fichiers en fonction des besoins. Si vous modifiez manuellement le fichier, vous devez redémarrer SQL Server avant que les modifications soient appliquées. Pour utiliser le **mssql.conf** fichier avec Docker, vous devez disposer de Docker [conserver vos données](sql-server-linux-configure-docker.md). Tout d’abord ajouter un complète **mssql.conf** de fichiers à votre répertoire de l’hôte, puis exécutez le conteneur. Il en est un exemple dans [les commentaires des clients](sql-server-linux-customer-feedback.md).

```ini
[EULA]
accepteula = Y

[coredump]
captureminiandfull = true
coredumptype = full

[filelocation]
defaultbackupdir = /var/opt/mssql/data/
defaultdatadir = /var/opt/mssql/data/
defaultdumpdir = /var/opt/mssql/data/
defaultlogdir = /var/opt/mssql/data/

[hadr]
hadrenabled = 0

[language]
lcid = 1033

[memory]
memorylimitmb = 4096

[network]
forceencryption = 0
ipaddress = 10.192.0.0
kerberoskeytabfile = /var/opt/mssql/secrets/mssql.keytab
tcpport = 1401
tlscert = /etc/ssl/certs/mssql.pem
tlsciphers = ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA
tlskey = /etc/ssl/private/mssql.key
tlsprotocols = 1.2,1.1,1.0

[sqlagent]
databasemailprofile = default
errorlogfile = /var/opt/mssql/log/sqlagentlog.log
errorlogginglevel = 7

[telemetry]
customerfeedback = true
userrequestedlocalauditdirectory = /tmp/audit

[traceflag]
traceflag0 = 1204
traceflag1 = 2345
traceflag = 3456
```

## <a name="next-steps"></a>Étapes suivantes

Pour utiliser à la place des variables d’environnement pour effectuer certaines de ces modifications de configuration, consultez [des paramètres de configuration de SQL Server avec les variables d’environnement](sql-server-linux-configure-environment-variables.md).

Pour d’autres outils de gestion et les scénarios, consultez [gérer SQL Server sur Linux](sql-server-linux-management-overview.md).
