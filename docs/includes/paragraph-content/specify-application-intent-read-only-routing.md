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
ms.sourcegitcommit: a98ed7872afc055c65aa9697d571f8b300f6eeb4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36313395"
---
## <a name="specifying-application-intent"></a>Spécification de l'intention d'application

Le mot clé **ApplicationIntent** peuvent être spécifiés dans votre chaîne de connexion. Les valeurs pouvant être assignés sont **ReadWrite** ou **ReadOnly**. La valeur par défaut est **ReadWrite**.

Lorsque **ApplicationIntent = ReadOnly**, le client demande un travail en lecture lors de la connexion. Le serveur applique l’intention au moment de la connexion et pendant une **utilisez** instruction de base de données.

Le **ApplicationIntent** (mot clé) ne fonctionne pas avec les bases de données héritées en lecture seule.  


#### <a name="targets-of-readonly"></a>Cibles d’en lecture seule

Quand une connexion choisit **ReadOnly**, la connexion est attribuée à une des configurations spéciales suivantes qui peuvent exister pour la base de données :

- [Always On](~/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)
    - Une base de données peut autoriser ou interdire les charges de travail en lecture sur la base de données AlwaysOn ciblée. Ce choix est contrôlé à l’aide de la **ALLOW_CONNECTIONS** clause de la **PRIMARY_ROLE** et **SECONDARY_ROLE** instructions Transact-SQL.

- [Géo-réplication](https://docs.microsoft.com/azure/sql-database/sql-database-geo-replication-overview)

- [Lire la montée en puissance parallèle](https://docs.microsoft.com/azure/sql-database/sql-database-read-scale-out)

Si aucun de ces cibles spéciales n’est disponible, la base de données est en lecture à partir de.

&nbsp;

Le **ApplicationIntent** mot-clé *routage en lecture seule*.


## <a name="read-only-routing"></a>Routage en lecture seule

Le routage en lecture seule est une fonctionnalité qui permet de garantir la disponibilité d'un réplica de base de données en lecture seule. Pour activer le routage en lecture seule, des éléments suivants s’appliquent :

- Vous devez vous connecter à un écouteur du groupe de disponibilité Always On.

- Dans la chaîne de connexion, le mot clé **ApplicationIntent** doit avoir la valeur **ReadOnly**.

- Le groupe de disponibilité doit être configuré par l'administrateur de base de données pour activer le routage en lecture seule.

Plusieurs connexions à l’aide de routage en lecture seule peuvent se connectent pas toutes au même réplica en lecture seule. Les modifications apportées à la synchronisation de base de données ou à la configuration du routage du serveur peuvent entraîner des connexions clientes à différents réplicas en lecture seule. Vous pouvez vous assurer que toutes les demandes en lecture seule se connectent au même réplica en lecture seule. Vérifiez ce sameness par *pas* en passant un écouteur de groupe de disponibilité pour le **Server** mot clé de chaîne de connexion. Au lieu de cela, spécifiez le nom de l'instance en lecture seule.

Peut être plus long que la connexion au principal de routage en lecture seule. L’attente plus long est, car le routage en lecture seule tout d’abord se connecte au principal et recherche le mieux secondaire lisible disponible. En raison de ces staps multiples, vous devez augmenter le délai de connexion au moins 30 secondes.

