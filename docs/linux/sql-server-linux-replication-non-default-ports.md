---
title: Configurer les partages de dossiers de captures instantanées Réplication SQL Server sur Linux
description: Cet article décrit comment configurer des partages de dossier de captures instantanées Réplication SQL Server sur Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6959b2073871f70fb33823b50419c208a23df2dd
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68093185"
---
# <a name="configure-replication-with-non-default-ports"></a>Configurer la réplication avec des ports autres que ceux par défaut

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Vous pouvez configurer la réplication avec des instances de SQL Server sur Linux qui écoutent sur n’importe quel port configuré avec le paramètre network.tcpport mssql-conf. Le port doit être ajouté au nom du serveur lors de la configuration si les conditions suivantes sont remplies :

1. La configuration de la réplication implique une instance de SQL Server sur Linux
2. Toute instance (Windows ou Linux) est à l’écoute sur un port autre que celui par défaut. 

Le nom de serveur d’une instance peut être trouvé en exécutant @@servername sur l’instance.

## <a name="examples"></a>Exemples

« Serveur1 » écoute sur le port 1500 sur Linux. Pour configurer « Serveur1 » pour la distribution, exécutez `sp_adddistributor` avec `@distributor`. Par exemple : 

```sql
exec sp_adddistributor @distributor = 'Server1,1500'
```

« Serveur1 » écoute sur le port 1500 sur Linux. Pour configurer un serveur de publication, exécutez `sp_adddistpublisher` avec `@publisher`. Par exemple :

```sql
exec sp_adddistpublisher @publisher = 'Server1,1500' ,  ,  
```

« Serveur2 » écoute sur le port 6549 sur Linux. Pour configurer « Serveur2 » en tant qu’abonné, exécutez `sp_addsubscription` avec `@subscriber`. Par exemple :

```sql
exec sp_addsubscription @subscriber = 'Server2,6549' ,  ,  
```

« Serveur3 » écoute le port 6549 sur Windows avec le nom de serveur Serveur3 et le nom d’instance MSSQL2017. Pour configurer « Serveur3 » en tant qu’abonné, exécutez `sp_addsubscription` avec `@subscriber`. Par exemple :

```sql
exec sp_addsubscription @subscriber = 'Server3/MSSQL2017,6549',  ,  
```

## <a name="next-steps"></a>Étapes suivantes

[Concepts : Réplication SQL Server sur Linux](sql-server-linux-replication.md)

[Procédures stockées de réplication](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

