---
title: Initialiser un abonnement | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], initializing subscriptions
- transactional replication, initializing subscriptions
- initializing subscriptions [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], about initializing subscriptions
- merge replication [SQL Server replication], initializing subscriptions
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 03a1a83dfb41da68565170f832b3b4233cfa9622
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85716799"
---
# <a name="initialize-a-subscription"></a>Initialiser un abonnement
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Les Abonnés dans une topologie de réplication doivent être initialisés, de façon à ce qu'ils aient une copie du schéma de chaque article de la publication à laquelle ils se sont abonnés et tous les objets de réplication requis, tels que des procédures stockées, des déclencheurs et des tables de métadonnées. De plus, l'Abonné reçoit généralement un jeu de données initial. La méthode d'initialisation par défaut utilise un instantané complet qui comprend le schéma, les objets de réplication et des données, mais les publications peuvent aussi être initialisées sans instantané complet.  
  
 Pour plus d'informations, consultez [Initialize a Subscription with a Snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md) et [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
  
