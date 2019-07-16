---
title: Configurer les partages de dossier d’instantanés réplication SQL Server sur Linux
description: Cet article décrit comment configurer la réplication d’instantané dossier partages SQL Server sur Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6959b2073871f70fb33823b50419c208a23df2dd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093185"
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

[Concepts : Réplication SQL Server sur Linux](sql-server-linux-replication.md)

[Procédures stockées de réplication](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

