---
title: Comment configurer MSDTC sur Linux | Microsoft Docs
description: Cet article fournit une procédure pas à pas pour la configuration de MSDTC sur Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 2bcf87b91423ae7aa79ae6a5194aa8fc31ca71c9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66713267"
---
# <a name="how-to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-on-linux"></a>Comment configurer Microsoft Distributed Transaction Coordinator (MSDTC) sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article décrit comment configurer Microsoft Distributed Transaction Coordinator (MSTDC) sur Linux. Prise en charge MSDTC sur Linux a été introduite dans la version préliminaire de SQL Server 2019.

## <a name="overview"></a>Vue d'ensemble

Les transactions distribuées sont activées sur SQL Server sur Linux en introduisant des fonctionnalités de mappeur de point de terminaison MSDTC et RPC dans SQL Server. Par défaut, un processus de mappage de point de terminaison RPC est à l’écoute sur le port 135 pour les demandes RPC entrantes et fournit des informations de composants inscrits pour les requêtes distantes. Demandes à distance peuvent utiliser les informations retournées par le mappeur de point de terminaison pour communiquer avec les composants RPC inscrits, tels que les services MSDTC. Un processus nécessite des privilèges de super utilisateur pour lier les ports connus (numéros de port inférieurs à 1024) sur Linux. Pour éviter le démarrage de SQL Server avec des privilèges racine pour le processus de mappeur de point de terminaison RPC, les administrateurs système doivent utiliser iptables pour créer la traduction d’adresses réseau pour acheminer le trafic sur le port 135 au processus de mappage de point de terminaison RPC du serveur SQL.

SQL Server 2019 introduit deux paramètres de configuration pour l’utilitaire mssql-conf.

| mssql-conf setting | Description |
|---|---|
| **network.rpcport** | Le port TCP utilisé par le processus de mappeur de point de terminaison RPC lie à. |
| **distributedtransaction.servertcpport** | Le port qui écoute le serveur MSDTC. Si ce n’est pas définie, le service MS DTC utilise un port éphémère aléatoire sur les redémarrages du service, et exceptions de pare-feu doit être reconfigurées pour vous assurer que service MSDTC peut poursuivre la communication. |

Pour plus d’informations sur ces paramètres et d’autres paramètres de MSDTC connexes, consultez [configurer SQL Server sur Linux avec l’outil mssql-conf](sql-server-linux-configure-mssql-conf.md#msdtc).

## <a name="supported-msdtc-configurations"></a>Configurations prises en charge de MSDTC

Les configurations de MSDTC suivantes sont prises en charge :

- OLE-TX transactions distribuées par rapport à SQL Server sur Linux pour des fournisseurs ODBC.
- Transactions distribuées XA sont définies par rapport à SQL Server sur Linux à l’aide de fournisseurs JDBC et ODBC. Pour les transactions XA à effectuer à l’aide du fournisseur ODBC, vous devez utiliser le pilote Microsoft ODBC pour SQL Server version 17.3 ou ultérieure.
- Transactions distribuées sur le serveur lié.

Pour les limitations et problèmes connus pour MSDTC en version préliminaire, consultez [notes de version préliminaire de SQL Server 2019 sur Linux](sql-server-linux-release-notes-2019.md#msdtc).

## <a name="msdtc-configuration-steps"></a>Étapes de configuration de MSDTC

Il existe trois étapes pour configurer les fonctionnalités et communication de MSDTC. Si les étapes de configuration nécessaires ne sont pas effectuées, SQL Server n’active pas la fonctionnalité MSDTC.

- Configurer **network.rpcport** et **distributedtransaction.servertcpport** à l’aide de mssql-conf.
- Configurer le pare-feu pour autoriser la communication sur **distributedtransaction.servertcpport** et le port 135.
- Configurer le routage de serveur Linux afin que la communication RPC sur le port 135 est redirigée vers SQL Server **network.rpcport**.

Les sections suivantes fournissent des instructions détaillées pour chaque étape.

## <a name="configure-rpc-and-msdtc-ports"></a>Configurer les ports RPC et MSDTC

Tout d’abord, configurez **network.rpcport** et **distributedtransaction.servertcpport** à l’aide de mssql-conf. Cette étape si spécifiques à SQL Server et communs à toutes les distributions prises en charge.

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

La deuxième étape consiste à configurer le pare-feu pour autoriser la communication sur **servertcpport** et le port 135.  Ainsi, le processus MSDTC pour communiquer avec l’extérieur vers d’autres gestionnaires de transactions et les coordinateurs et le processus de mappage de point de terminaison RPC. Les étapes réelles pour cela varie selon votre distribution Linux et le pare-feu. 

L’exemple suivant montre comment créer ces règles sur **Ubuntu**.

```bash
sudo ufw allow from any to any port 51999 proto tcp
sudo ufw allow from any to any port 135 proto tcp
```

L’exemple suivant montre comment cela peut être fait sur **Red Hat Enterprise Linux (RHEL)** :

```bash
sudo firewall-cmd --zone=public --add-port=51999/tcp --permanent
sudo firewall-cmd --zone=public --add-port=135/tcp --permanent
sudo firewall-cmd --reload
```

Il est important de configurer le pare-feu avant de configurer le routage de port dans la section suivante. L’actualisation du pare-feu peut effacer les règles de routage de port dans certains cas.

## <a name="configure-port-routing"></a>Configurer le routage de port

Configurer la table de routage du serveur Linux afin que la communication RPC sur le port 135 est redirigée vers SQL Server **network.rpcport**. Mécanisme de configuration de distribution différente de réacheminement de port peut différer. Les sections suivantes fournissent des conseils pour Ubuntu, SUS Enterprise Linux (SLES) et Red Hat Enterprise Linux (RHEL).

### <a name="port-routing-in-ubuntu-and-sles"></a>Routage de port dans Ubuntu et SLES

Ubuntu et SLES n’utilisent pas le **firewalld** service, **iptable** règles sont un mécanisme efficace pour obtenir le routage de port. Le **iptable** règles ne sont pas persistant au cours des redémarrages, donc les commandes suivantes fournissent également des instructions permettant de restaurer les règles après un redémarrage.

1. Créer des règles de routage pour le port 135. Dans l’exemple suivant, le port 135 est dirigé vers le port RPC 13500, défini dans la section précédente. Remplacez `<ipaddress>` avec l’adresse IP de votre serveur.

   ```bash
   sudo iptables -t nat -A PREROUTING -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL  \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   sudo iptables -t nat -A OUTPUT -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   ```

   Le `--comment RpcEndPointMapper` paramètre dans les commandes précédentes facilite la gestion de ces règles dans les commandes ultérieures.

2. Afficher les règles de routage que vous avez créé avec la commande suivante :

   ```bash
   sudo iptables -S -t nat | grep "RpcEndPointMapper"
   ```

3. Enregistrer les règles de routage dans un fichier sur votre ordinateur.

   ```bash
   sudo iptables-save > /etc/iptables.conf
   ```

4. Pour recharger les règles après un redémarrage, ajoutez la commande suivante pour `/etc/rc.local` (pour Ubuntu) ou `/etc/init.d/after.local` (pour SLES) :

   ```bash
   iptables-restore < /etc/iptables.conf
   ```

   > [!NOTE]
   > Vous devez disposer des privilèges de superutilisateur (sudo) pour pouvoir modifier le **rc.local** ou **after.local** fichiers.

Le **iptables-enregistrer** et **iptables-restauration** des commandes, ainsi qu’avec `rc.local` / `after.local` configuration de démarrage, fournissent un mécanisme de base pour enregistrer et restaurer des tables d’adresses IP entrées. En fonction de votre distribution Linux, il peut être plus avancée ou automatisée des options disponibles. Par exemple, une alternative Ubuntu est la **iptables persistant** package pour effectuer des entrées persistant.

> [!IMPORTANT]
> Les étapes précédentes supposent une adresse IP fixe. Si l’adresse IP de votre instance SQL Server change (en raison d’une intervention manuelle ou DHCP), vous devez supprimer et recréer les règles de routage si elles ont été créées avec iptables. Si vous avez besoin de recréer ni de supprimer des règles de routage existantes, vous pouvez utiliser la commande suivante pour supprimer l’ancien `RpcEndPointMapper` règles :
> 
> ```bash
> sudo iptables -S -t nat | grep "RpcEndPointMapper" | sed 's/^-A //' | while read rule; do iptables -t nat -D $rule; done
> ```

### <a name="port-routing-in-rhel"></a>Routage dans RHEL de port

Dans les distributions qui utilisent **firewalld** service, telles que Red Hat Enterprise Linux, le même service peut être utilisé pour les deux ouvrant le port sur le serveur et le réacheminement de port interne. Par exemple, sur Red Hat Enterprise Linux, vous devez utiliser **firewalld** service (via **pare-feu-cmd** utilitaire de configuration avec `-add-forward-port` ou des options similaires) pour créer et gérer le port permanent règles de transfert au lieu d’utiliser iptables.

```bash
sudo firewall-cmd --permanent --add-forward-port=port=135:proto=tcp:toport=13500
sudo firewall-cmd --reload
```

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

## <a name="configure-authentication-on-rpc-communication-for-msdtc"></a>Configurer l’authentification sur la communication RPC pour MSDTC

MSDTC pour SQL Server sur Linux n’utilise pas l’authentification sur la communication RPC par défaut. Toutefois, lorsque l’ordinateur hôte est joint à un domaine Active Directory (AD), il est possible de configurer MSDTC pour utiliser la communication RPC authentifiée à l’aide suivant **mssql-conf** paramètres :

| Paramètre | Description |
|---|---|
| **distributedtransaction.allowonlysecurerpccalls**          | Configurer des appels RPC sécurisés uniquement pour les transactions distribuées. |
| **distributedtransaction.fallbacktounsecurerpcifnecessary** | Configurer la sécurité que RPC uniquement appelle pour les transactions distribuées. |
| **distributedtransaction.turnoffrpcsecurity**               | Activez ou désactivez la sécurité RPC pour les transactions distribuées. |

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur SQL Server sur Linux, consultez [SQL Server sur Linux](sql-server-linux-overview.md).
