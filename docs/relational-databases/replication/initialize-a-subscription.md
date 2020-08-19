---
description: Initialiser un abonnement
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
ms.openlocfilehash: 562a0cf16f677c9306df82b9e2618a793752ed93
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88423593"
---
# <a name="initialize-a-subscription"></a>Initialiser un abonnement
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Les Abonnés dans une topologie de réplication doivent être initialisés, de façon à ce qu'ils aient une copie du schéma de chaque article de la publication à laquelle ils se sont abonnés et tous les objets de réplication requis, tels que des procédures stockées, des déclencheurs et des tables de métadonnées. De plus, l'Abonné reçoit généralement un jeu de données initial. La méthode d'initialisation par défaut utilise un instantané complet qui comprend le schéma, les objets de réplication et des données, mais les publications peuvent aussi être initialisées sans instantané complet.  
  
 Pour plus d'informations, consultez [Initialize a Subscription with a Snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md) et [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
  
