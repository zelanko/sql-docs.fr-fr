---
title: Réplication SQL Server sur Linux
description: Cet article décrit la réplication SQL Server sur Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 10/17/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b049866d9752485cb1b9eb609404a3bd86f28a41
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68065195"
---
# <a name="sql-server-replication-on-linux"></a>Réplication SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] introduit la réplication SQL Server pour les instances SQL Server sur Linux.

Configurez la réplication sur Linux avec les [procédures stockées de réplication](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md) de SQL Server Management Studio (SSMS).

Une instance de SQL Server peut participer à n’importe quel rôle de réplication :

* Serveur de publication
* Serveur de distribution
* Abonné

Un schéma de réplication peut combiner et faire correspondre des plateformes de systèmes d’exploitation. Par exemple, un schéma de réplication peut inclure une instance de SQL Server sur Linux pour le serveur de publication et le serveur de distribution, et les abonnés incluent des instances de SQL Server sur Windows et Linux.

Les instances de SQL Server sur Linux peuvent participer à n’importe quel type de réplication.

* Transactionnelle
* Fusion
* Snapshot

Pour plus d’informations sur la réplication, consultez la [documentation sur la réplication SQL Server](../relational-databases/replication/sql-server-replication.md).

## <a name="supported-features"></a>Fonctionnalités prises en charge

Pour [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)], les fonctionnalités de réplication suivantes sont prises en charge :

* Réplication d'instantané
* Réplication transactionnelle
* Réplication de fusion
* Réplication d’égal à égal
* Réplication avec des ports autres que les ports par défaut <!--Add link to explanation-->
* Réplication avec authentification AD
* Configurations de réplication sur Windows et Linux
* Mises à jour immédiates pour la réplication transactionnelle

## <a name="limitations"></a>Limitations

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] ne prend pas en charge les fonctionnalités suivantes :

* Mise à jour immédiate des abonnés
* Publication Oracle

## <a name="next-steps"></a>Étapes suivantes

[Configurer la réplication SQL Server sur Linux](sql-server-linux-replication-tutorial-tsql.md)

[Exemple : Configurer la réplication SQL Server sur Linux](sql-server-linux-replication-configure.md)
