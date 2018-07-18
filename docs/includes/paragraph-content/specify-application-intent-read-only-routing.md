---
title: inclure fichier
description: inclure fichier
services: sql-database
author: MightyPen
ms.service: sql-database
ms.topic: include
ms.date: 04/05/2018
ms.author: genemi
ms.custom: include file
ms.openlocfilehash: 842a7377bcd6bdcb649a78b2f31eb66de95bc5a3
ms.sourcegitcommit: 44e9bf62f2c75449c17753ed66bf85c43928dbd5
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37854391"
---
## <a name="specifying-application-intent"></a>Spécification de l'intention d'application

Le mot clé **ApplicationIntent** peut être spécifié dans votre chaîne de connexion. Les valeurs assignables sont **ReadWrite** ou **ReadOnly**. La valeur par défaut est **ReadWrite**.

Lorsque **ApplicationIntent = ReadOnly**, le client demande un travail en lecture lors de la connexion. Le serveur applique l’intention au moment de la connexion et pendant une **utilisez** instruction de base de données.

Le mot clé **ApplicationIntent** ne fonctionne pas avec les bases de données en lecture seule héritées.  


#### <a name="targets-of-readonly"></a>Cibles « ReadOnly »

Quand une connexion choisit **ReadOnly**, la connexion est attribuée à une des configurations spéciales suivantes qui peuvent exister pour la base de données :

- [Always On](~/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)
    - Une base de données peut autoriser ou interdire les charges de travail en lecture sur la base de données AlwaysOn ciblée. Ce choix est contrôlé à l’aide de la **ALLOW_CONNECTIONS** clause de le **PRIMARY_ROLE** et **SECONDARY_ROLE** instructions Transact-SQL.

- [Géo-réplication](https://docs.microsoft.com/azure/sql-database/sql-database-geo-replication-overview)

- [Scale-out en lecture](https://docs.microsoft.com/azure/sql-database/sql-database-read-scale-out)

Si aucune de ces cibles spéciales n’est disponible, la base de données standard est en lecture à partir de.

&nbsp;

Le **ApplicationIntent** mot-clé permet *routage en lecture seule*.


## <a name="read-only-routing"></a>Routage en lecture seule

Le routage en lecture seule est une fonctionnalité qui permet de garantir la disponibilité d'un réplica de base de données en lecture seule. Pour activer le routage en lecture seule, toutes les conditions suivantes s’appliquent :

- Vous devez vous connecter à un écouteur du groupe de disponibilité Always On.

- Dans la chaîne de connexion, le mot clé **ApplicationIntent** doit avoir la valeur **ReadOnly**.

- Le groupe de disponibilité doit être configuré par l'administrateur de base de données pour activer le routage en lecture seule.

Plusieurs connexions à l’aide de routage en lecture seule peuvent se connectent pas toutes au même réplica en lecture seule. Les modifications apportées à la synchronisation de base de données ou à la configuration du routage du serveur peuvent entraîner des connexions clientes à différents réplicas en lecture seule. Vous pouvez vous assurer que toutes les demandes en lecture seule se connectent au même réplica en lecture seule. Vérifiez cette similitude par *pas* en passant un écouteur de groupe de disponibilité pour le **Server** mot clé de chaîne de connexion. Au lieu de cela, spécifiez le nom de l'instance en lecture seule.

Peut prendre plu de la connexion au principal de routage en lecture seule. Le délai plus long est dû au fait que le routage en lecture seule se connecte d’abord à la base de données principale, puis recherche la meilleure base de données secondaire lisible disponible. En raison de ces staps plusieurs, vous devez augmenter le délai de connexion au moins 30 secondes.

