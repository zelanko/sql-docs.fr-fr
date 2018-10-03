---
title: La réplication SQL Server sur Linux | Microsoft Docs
description: Cet article décrit la réplication SQL Server sur Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/20/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.workload: On Demand
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a6c4bad8947944d59208a0516e5950d36f64a84e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47734127"
---
# <a name="sql-server-replication-on-linux"></a>Réplication SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] introduit la réplication SQL Server pour les instances de SQL Server sur Linux.

Configurer la réplication sur Linux avec SQL Server Management Studio (SSMS) [procédures stockées de réplication](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

Une instance de SQL Server peut participer à n’importe quel rôle de réplication :

* Serveur de publication
* Serveur de distribution
* Abonné

Un schéma de réplication pouvez combiner des plateformes de système d’exploitation. Par exemple, un schéma de réplication peut utiliser des instances de SQL Server sur Linux pour le serveur de publication et serveur de distribution et les abonnés peuvent inclure des instances de SQL Server sur Windows.

Les instances de SQL Server sur Linux peuvent participer à n’importe quel type de réplication.

* Transactionnelle
* Fusion
* Snapshot

Pour plus d’informations sur la réplication, consultez [documentation de réplication SQL Server](../relational-databases/replication/sql-server-replication.md).

## <a name="supported-features"></a>Fonctionnalités prises en charge

Pour [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] les fonctionnalités de réplication suivantes sont prises en charge :

* Réplication d'instantané
* Réplication transactionnelle
* Réplication de fusion
* Réplication d’égal à égal
* Réplication avec des ports non-par défaut <!--Add link to explanation-->
* Réplication avec l’authentification AD
* Configurations de réplication entre Windows et Linux
* Mises à jour immédiates pour la réplication transactionnelle

## <a name="limitations"></a>Limitations

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] ne prend pas en charge les fonctionnalités suivantes :

* Abonnés de mise à jour immédiate

## <a name="next-steps"></a>Étapes suivantes

[Configurer la réplication de SQL Server sur Linux](sql-server-linux-replication-tutorial-tsql.md)

[Exemple : Configurer la réplication de SQL Server sur Linux](sql-server-linux-replication-configure.md)
