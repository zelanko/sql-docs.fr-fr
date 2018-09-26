---
title: Comment utiliser des transactions distribuées avec SQL Server sur Docker | Microsoft Docs
description: Cet article explique comment utiliser Dprovides une procédure pas à pas pour la configuration de MSDTC sur Linux.
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
ms.openlocfilehash: 3242f0d074dc3c2f33fc83de4604a20bfdcbd64a
ms.sourcegitcommit: df21af652d0906ade8cc9ca3985a7ba5569f0db6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "47049403"
---
# <a name="how-to-use-distributed-transactions-with-sql-server-on-docker"></a>Comment utiliser des transactions distribuées avec SQL Server sur Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article explique comment configurer SQL Server sur Docker pour les transactions distribuées.

Images de conteneur à partir de SQL Server 2019 preview, prennent en charge le Microsoft MSDTC Distributed Transaction Coordinator () requis pour les transactions distribuées. Pour comprendre les exigences de communications pour MSDTC, consultez [comment configurer Microsoft Distributed Transaction Coordinator (MSDTC) sur Linux](sql-server-linux-configure-msdtc.md). Cet article explique les exigences particulières et les scénarios liés aux conteneurs de Docker SQL Server.

## <a name="configuration"></a>Configuration

Pour activer la transaction MSDTC dans des conteneurs pour docker, vous devez définir deux nouvelles variables d’environnement :

- **MSSQL_RPC_PORT**: le port TCP que le service mappeur de point de terminaison RPC lie à et écoute.  
- **MSSQL_DTC_TCP_PORT** le port que le service MSDTC est configuré pour écouter sur.

### <a name="pull-and-run"></a>Extraire et exécuter

L’exemple suivant montre comment utiliser ces variables d’environnement pour extraire et exécuter un conteneur configuré pour MSDTC. Cela lui permet de communiquer avec n’importe quelle application sur tous les hôtes.

```bash
docker run \
   -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
   -e 'MSSQL_RPC_PORT=13500' -e 'MSSQL_DTC_TCP_PORT=51000' \
   -p 51433:1433 -p 13500:13500 -p 51000:51000  \
   -d mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu
```

La commande suivante montre la même commande pour Docker sur Windows dans PowerShell :

```PowerShell
docker run `
   -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
   -e "MSSQL_RPC_PORT=13500" -e "MSSQL_DTC_TCP_PORT=51000" `
   -p 51433:1433 -p 13500:13500 -p 51000:51000 `
   -d "mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu"
```

Dans cette commande, le **mappeur de point de terminaison RPC** service a été lié au port 13500 et le **MSDTC** service a été lié au port 51000 au sein du réseau virtuel de docker. Communication de TDS SQL Server se produit sur le port 1433 dans le réseau virtuel de docker. Ces ports ont été exposées en externe à l’hôte en tant que port TDS 51433, port de mappeur de point de terminaison RPC 13500 et port MSDTC 51000.

> [!NOTE]
> Le mappeur de point de terminaison RPC et le port MSDTC n’ont pas à être le même sur l’hôte et le conteneur. Par conséquent, tandis que le port du mappeur de point de terminaison RPC a été configuré pour être 13500 sur le conteneur, il peut potentiellement être mappée pour le port 13501 ou tout autre port disponible sur le serveur hôte.

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

Si le conteneur docker participe aux transactions distribuées avec un serveur externe à l’hôte, l’hôte doit configurer le routage de port. Pour plus d’informations, consultez [configurer le routage de port](sql-server-linux-configure-msdtc.md#configure-port-routing).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur MSDTC sur Linux, consultez [comment configurer Microsoft Distributed Transaction Coordinator (MSDTC) sur Linux](sql-server-linux-configure-msdtc.md).