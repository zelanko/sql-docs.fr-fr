---
title: Configurer les partages de dossier d’instantanés réplication SQL Server sur Linux | Microsoft Docs
description: Cet article décrit comment configurer la réplication d’instantané dossier partages SQL Server sur Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 9/24/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.workload: On Demand
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: dae79e05ff7f92e9e93543fd3540b5a2b019e255
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47850097"
---
# <a name="configure-replication-with-non-default-ports"></a>Configurer la réplication avec les ports par défaut

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Vous pouvez configurer la réplication avec SQL Server sur les instances de Linux à l’écoute sur n’importe quel port configuré avec le paramètre de mssql-conf network.tcpport. Le port doit être ajouté au nom du serveur lors de la configuration si les conditions suivantes sont remplies :

1. Configuration de la réplication implique une instance de SQL Server sur Linux
2. N’importe quelle instance (Windows ou Linux) est à l’écoute sur un port non défini par défaut. 

Vous trouverez le nom du serveur d’une instance en cours d’exécution @@servername sur l’instance.

## <a name="examples"></a>Exemples

« Server1 » est à l’écoute sur le port 1500 sur Linux. Pour configurer les « Server1 » pour la distribution, exécutez `sp_adddistributor` avec `@distributor`. Exemple : 

```sql
exec sp_adddistributor @distributor = 'Server1,1500'
```

« Server1 » est à l’écoute sur le port 1500 sur Linux. Pour configurer un serveur de publication du serveur de distribution, exécutez `sp_adddistpublisher` avec `@publisher`. Exemple :

```sql
exec sp_adddistpublisher @publisher = 'Server1,1500' ,  ,  
```

'Server2' écoute sur le port 6549 sur Linux. Pour configurer « Serveur2 » en tant qu’abonné, exécutez `sp_addsubscription` avec `@subscriber`. Exemple :

```sql
exec sp_addsubscription @subscriber = 'Server2,6549' ,  ,  
```

'Server3' écoute sur le port 6549 sur Windows avec le nom du serveur de Server3 et nom de l’instance de MSSQL2017. Pour configurer « Server3 » en tant qu’abonné, exécutez le `sp_addsubscription` avec `@subscriber`. Exemple :

```sql
exec sp_addsubscription @subscriber = 'Server3/MSSQL2017,6549',  ,  
```

## <a name="next-steps"></a>Étapes suivantes

[Concepts : Réplication de SQL Server sur Linux](sql-server-linux-replication.md)

[Procédures stockées de réplication](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

