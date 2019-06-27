---
title: Comment utiliser des transactions distribuées avec SQL Server sur Docker | Microsoft Docs
description: Cet article explique comment utiliser Dprovides une procédure pas à pas pour la configuration de MSDTC sur Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 09/25/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 1e38c1cf0fb82c70f57a1648619d584b06281cba
ms.sourcegitcommit: 65ceea905030582f8d89e75e97758abf3b1f0bd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400057"
---
# <a name="how-to-use-distributed-transactions-with-sql-server-on-docker"></a>Comment utiliser des transactions distribuées avec SQL Server sur Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article explique comment configurer des conteneurs Linux de SQL Server sur Docker pour les transactions distribuées.

Images de conteneur à partir de SQL Server 2019 preview, prennent en charge le Microsoft MSDTC Distributed Transaction Coordinator () requis pour les transactions distribuées. Pour comprendre les exigences de communications pour MSDTC, consultez [comment configurer Microsoft Distributed Transaction Coordinator (MSDTC) sur Linux](sql-server-linux-configure-msdtc.md). Cet article explique les exigences particulières et les scénarios liés aux conteneurs de Docker SQL Server.

## <a name="configuration"></a>Configuration

Pour activer la transaction MSDTC dans des conteneurs pour docker, vous devez définir deux nouvelles variables d’environnement :

- **MSSQL_RPC_PORT**: le port TCP que le service mappeur de point de terminaison RPC lie à et écoute.  
- **MSSQL_DTC_TCP_PORT**: le port que le service MSDTC est configuré pour écouter sur.

### <a name="pull-and-run"></a>Extraire et exécuter

L’exemple suivant montre comment utiliser ces variables d’environnement pour extraire et exécuter un seul conteneur de SQL Server configuré pour MSDTC. Cela lui permet de communiquer avec n’importe quelle application sur tous les hôtes.

```bash
docker run \
   -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
   -e 'MSSQL_RPC_PORT=135' -e 'MSSQL_DTC_TCP_PORT=51000' \
   -p 51433:1433 -p 135:135 -p 51000:51000  \
   -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

> [!IMPORTANT]
> La commande précédente fonctionne uniquement pour Docker en cours d’exécution sur Linux. Docker sur Windows, l’hôte Windows écoute déjà sur le port 135. Vous pouvez supprimer le `-p 135:135` paramètre pour Docker sur Windows, mais il présente quelques limitations. Le conteneur obtenu, ne peut pas être utilisé pour les transactions distribuées qui impliquent l’hôte ; Il peut uniquement participer à des transactions distribuées entre les conteneurs docker sur l’ordinateur hôte.

Dans cette commande, le **mappeur de point de terminaison RPC** service a été lié au port 135 et le **MSDTC** service a été lié au port 51000 au sein du réseau virtuel de docker. Communication de TDS SQL Server se produit sur le port 1433 dans le réseau virtuel de docker. Ces ports ont été exposées en externe à l’hôte en tant que port TDS 51433, port de mappeur de point de terminaison RPC 135 et le port MSDTC 51000.

> [!NOTE]
> Le mappeur de point de terminaison RPC et le port MSDTC n’ont pas à être identique sur l’hôte et le conteneur. Par conséquent, tandis que le port du mappeur de point de terminaison RPC a été configuré pour être 135 sur le conteneur, il peut potentiellement être mappée pour le port 13501 ou tout autre port disponible sur le serveur hôte.

## <a name="configure-the-firewall"></a>Configurer le pare-feu

Afin de communiquer avec et via l’hôte, vous devez également configurer le pare-feu sur le serveur hôte pour les conteneurs. Ouvrez le pare-feu pour tous les ports que docker conteneur expose pour la communication externe. Dans l’exemple précédent, il s’agit des ports 135, 51433 et 51000. Voici les ports sur l’hôte lui-même et pas les ports qu'auxquels elles sont mappées à dans le conteneur. Par conséquent, si le point de terminaison RPC est le port mappeur 51000 du conteneur a été mappé au port hôte 51001, port puis 51001 (pas 51000) doit être ouvert dans le pare-feu pour la communication avec l’hôte.  

L’exemple suivant montre comment créer ces règles sur Ubuntu.

```bash
sudo ufw allow from any to any port 51433 proto tcp
sudo ufw allow from any to any port 51000 proto tcp
sudo ufw allow from any to any port 135 proto tcp
```

L’exemple suivant montre comment cela peut être fait sur Red Hat Enterprise Linux (RHEL) :

```bash
sudo firewall-cmd --zone=public --add-port=51999/tcp --permanent
sudo firewall-cmd --zone=public --add-port=51433/tcp --permanent
sudo firewall-cmd --zone=public --add-port=135/tcp --permanent
sudo firewall-cmd --reload
```

## <a name="configure-port-routing-on-the-host"></a>Configurer le routage de port sur l’hôte

Dans l’exemple précédent, car un seul conteneur Docker mappe le port RPC 135 pour le port 135 sur l’ordinateur hôte, les transactions distribuées avec l’hôte devraient désormais fonctionner sans configuration supplémentaire. Notez qu’il est possible d’utiliser directement le port 135 dans le conteneur, étant donné que SQL Server s’exécute avec des privilèges élevés dans un conteneur. Pour SQL Server en dehors d’un conteneur, un autre port éphémère doit être utilisé et le trafic au port 135 doit ensuite être acheminé vers ce port.

Toutefois, si vous l’avez fait décidez mapper le port du conteneur 135 à un autre port sur l’hôte, telles que 13500, vous devez configurer le routage de port sur l’ordinateur hôte. Ainsi, le conteneur docker à participer aux transactions distribuées avec l’hôte et avec d’autres serveurs externes. Pour plus d’informations, consultez [configurer le routage de port](sql-server-linux-configure-msdtc.md#configure-port-routing).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur MSDTC sur Linux, consultez [comment configurer Microsoft Distributed Transaction Coordinator (MSDTC) sur Linux](sql-server-linux-configure-msdtc.md).
