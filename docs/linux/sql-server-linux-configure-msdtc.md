---
title: Comment configurer MSDTC sur Linux | Microsoft Docs
description: Cet article fournit une procédure pas à pas pour la configuration de MSDTC sur Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 7f8070b5910f5488d9aec9470adc088172d92ad1
ms.sourcegitcommit: df21af652d0906ade8cc9ca3985a7ba5569f0db6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "47049630"
---
# <a name="how-to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-on-linux"></a>Comment configurer Microsoft Distributed Transaction Coordinator (MSDTC) sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article décrit comment configurer Microsoft Distributed Transaction Coordinator (MSTDC) sur Linux. Prise en charge MSDTC sur Linux a été introduite dans SQL Server 2019 CTP 2.0.

## <a name="overview"></a>Vue d'ensemble

Les transactions distribuées sont activées sur SQL Server sur Linux en introduisant des fonctionnalités de mappeur de point de terminaison MSDTC et RPC dans SQL Server. Par défaut, un processus de mappage de point de terminaison RPC est à l’écoute sur le port 135 pour les demandes RPC entrantes et qui achemine vers les composants appropriés (par exemple, le service MSDTC). Un processus nécessite des privilèges de super utilisateur pour lier les ports connus (numéros de port inférieurs à 1024) sur Linux. Pour éviter le démarrage de SQL Server avec des privilèges racine pour le processus de mappeur de point de terminaison RPC, les administrateurs système doivent utiliser iptables pour créer la traduction NAT pour acheminer le trafic sur le port 135 au processus de mappage de point de terminaison RPC du serveur SQL.

SQL Server 2019 introduit deux paramètres de configuration pour l’utilitaire mssql-conf.

| paramètre de MSSQL-conf | Description |
|---|---|
| **Network.rpcport** | Le port TCP utilisé par le processus de mappeur de point de terminaison RPC lie à. |
| **Network.servertcpport** | Le port qui écoute le serveur MSDTC. Si ce n’est pas définie, le service MS DTC utilise un port éphémère aléatoire sur les redémarrages du service, et les exceptions de pare-feu devra être reconfigurées pour s’assurer que service MSDTC peut poursuivre la communication. |

Pour plus d’informations sur ces paramètres et d’autres paramètres de MSDTC connexes, consultez [configurer SQL Server sur Linux avec l’outil mssql-conf](sql-server-linux-configure-mssql-conf.md#msdtc).

## <a name="supported-msdtc-configurations"></a>Configurations prises en charge de MSDTC

Les configurations de MSDTC suivantes sont prises en charge :

- OLE-TX transactions distribuées par rapport à SQL Server sur Linux pour les fournisseurs JDBC et ODBC.
- Transactions distribuées XA sont définies par rapport à SQL Server sur Linux à l’aide de fournisseurs JDBC.
- Transactions distribuées sur le serveur lié.

Pour les limitations et problèmes connus pour MSDTC dans CTP 2.0, consultez [notes de version pour SQL Server 2019 CTP sur Linux](sql-server-linux-release-notes-2019.md#msdtc).

## <a name="msdtc-configuration-steps"></a>Étapes de configuration de MSDTC

Il existe trois étapes pour configurer les fonctionnalités et communication de MSDTC. Si les étapes de configuration nécessaires ne sont pas effectuées, SQL Server n’active pas la fonctionnalité MSDTC.

- Configurer **network.rpcport** et **distributedtransaction.servertcpport** à l’aide de mssql-conf.
- Configurer le pare-feu pour autoriser la communication sur **rpcport**, **servertcpport**et le port 135.
- Configurer le routage de serveur Linux afin que la communication RPC sur le port 135 est redirigée vers SQL Server **network.rpcport**.

Les sections suivantes fournissent des instructions détaillées pour chaque étape.

## <a name="configure-rpc-and-msdtc-ports"></a>Configurer les ports RPC et MSDTC

Tout d’abord, configurez **network.rpcport** et **distributedtransaction.servertcpport** à l’aide de mssql-conf.

1. Mssql-conf permet de définir le **network.rpcport** valeur. L’exemple suivant définit à 13500.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.rpcport 13500
   ```

2. Définir le **distributedtransaction.servertcpport** valeur. L’exemple suivant définit à 51999.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set distributedtransaction.servertcpport 51999
   ```

3. Redémarrez SQL Server.

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="configure-the-firewall"></a>Configurer le pare-feu

L’étape finale consiste à configurer le pare-feu pour autoriser la communication sur **rpcport**, **servertcpport**et le port 135.  Ainsi, le processus MSDTC pour communiquer avec l’extérieur vers d’autres gestionnaires de transactions et les coordinateurs et le processus de mappage de point de terminaison RPC. Les étapes réelles pour cela varie selon votre distribution Linux et le pare-feu. 

L’exemple suivant montre comment créer ces règles sur Ubuntu.

```bash
sudo ufw allow from any to any port 51999 proto tcp
sudo ufw allow from any to any port 135 proto tcp
```

L’exemple suivant montre comment cela peut être fait sur Red Hat Enterprise Linux (RHEL) :

```bash
sudo firewall-cmd --zone=public --add-port=51999/tcp --permanent
sudo firewall-cmd --zone=public --add-port=135/tcp --permanent
sudo firewall-cmd --reload
```

Il est important de configurer le pare-feu avant de configurer le routage de port dans la section suivante. L’actualisation du pare-feu peut effacer les règles de routage de port dans certains cas.

## <a name="configure-port-routing"></a>Configurer le routage de port

Configurer la table de routage du serveur Linux afin que la communication RPC sur le port 135 est redirigée vers SQL Server **network.rpcport**. Les règles d’iptable ne sont pas persistant au cours des redémarrages, les commandes suivantes fournissent également des instructions permettant de restaurer les règles après un redémarrage.

1. Créer des règles de routage pour le port 135. Dans l’exemple suivant, le port 135 est dirigé vers le port RPC 13500, défini dans la section précédente. Remplacez `<ipaddress>` avec l’adresse IP de votre serveur.

   ```bash
   iptables -t nat -A PREROUTING -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL  \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   iptables -t nat -A OUTPUT -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   ```

   Le `--comment RpcEndPointMapper` paramètre dans les commandes précédentes facilite la gestion de ces règles dans les commandes ultérieures.

2. Afficher les règles de routage que vous avez créé avec la commande suivante :

   ```bash
   iptables -S -t nat | grep "RpcEndPointMapper"
   ```

3. Enregistrer les règles de routage dans un fichier sur votre ordinateur.

   ```bash
   iptables-save > /etc/iptables.conf
   ```

4. Pour recharger les règles après un redémarrage, ajoutez la commande suivante pour `/etc/rc.local` (pour Ubuntu or RHEL) ou `/etc/init.d/after.local` (pour SLES) :

   ```bash
   iptables-restore < /etc/iptables.conf
   ```

Le **iptables-enregistrer** et **iptables-restauration** commandes fournissent un mécanisme de base pour enregistrer et restaurer les entrées de tables d’adresses IP. En fonction de votre distribution Linux, il peut être plus avancée ou automatisée des options disponibles. Par exemple, une alternative Ubuntu est la **iptables persistant** package pour effectuer des entrées persistant. Ou pour Red Hat Enterprise Linux, vous pourrez peut-être utiliser le service de firewalld (via l’utilitaire de configuration de pare-feu-cmd avec – Ajouter-progression-port ou des options similaires) pour créer des règles au lieu d’utiliser iptables de réacheminement de port persistant.

> [!IMPORTANT]
> Les étapes précédentes supposent une adresse IP fixe. Si l’adresse IP de votre instance SQL Server change (en raison d’une intervention manuelle ou DHCP), vous devez supprimer et recréer les règles de routage. Si vous avez besoin de recréer ni de supprimer des règles de routage existantes, vous pouvez utiliser la commande suivante pour supprimer l’ancien `RpcEndPointMapper` règles :
> 
> ```bash
> iptables -S -t nat | grep "RpcEndPointMapper" | sed 's/^-A //' | while read rule; do iptables -t nat -D $rule; done
> ```

## <a name="verify"></a>Vérifier

À ce stade, SQL Server doit être en mesure de participer aux transactions distribuées. Pour vérifier que SQL Server est à l’écoute, exécutez le **netstat** commande (si vous utilisez RHEL, vous devrez d’abord installer le **net-tools** package) :

```bash
sudo netstat -tulpn | grep sqlservr
```

Vous devez voir une sortie similaire à ce qui suit :

```bash
tcp 0 0 0.0.0.0:1433 0.0.0.0:* LISTEN 13911/sqlservr
tcp 0 0 127.0.0.1:1434 0.0.0.0:* LISTEN 13911/sqlservr
tcp 0 0 0.0.0.0:13500 0.0.0.0:* LISTEN 13911/sqlservr
tcp 0 0 0.0.0.0:51999 0.0.0.0:* LISTEN 13911/sqlservr
tcp6 0 0 :::1433 :::* LISTEN 13911/sqlservr
tcp6 0 0 ::1:1434 :::* LISTEN 13911/sqlservr
tcp6 0 0 :::13500 :::* LISTEN 13911/sqlservr
tcp6 0 0 :::51999 :::* LISTEN 13911/sqlservr
```

Toutefois, après un redémarrage, SQL Server ne démarre pas à l’écoute sur le **servertcpport** jusqu'à ce que le premier de transaction distribuée. Dans ce cas, vous ne verriez pas SQL Server écoute sur le port 51999 dans cet exemple, jusqu'à ce que la première transaction distribuée.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur SQL Server sur Linux, consultez [SQL Server sur Linux](sql-server-linux-overview.md).
