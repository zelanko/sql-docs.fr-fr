---
title: "Initialiser un abonnement | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "réplication de capture instantanée [SQL Server], initialisation des abonnements"
  - "réplication transactionnelle, initialisation des abonnements"
  - "initialisation des abonnements [réplication SQL Server]"
  - "abonnements [réplication SQL Server], initialisation"
  - "initialisation d’abonnements [réplication SQL Server], à propos de l’initialisation d’abonnements"
  - "réplication de fusion [réplication SQL Server], initialisation des abonnements"
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 32
---
# Initialiser un abonnement
  Les Abonnés dans une topologie de réplication doivent être initialisés, de façon à ce qu'ils aient une copie du schéma de chaque article de la publication à laquelle ils se sont abonnés et tous les objets de réplication requis, tels que des procédures stockées, des déclencheurs et des tables de métadonnées. De plus, l'Abonné reçoit généralement un jeu de données initial. La méthode d'initialisation par défaut utilise un instantané complet qui comprend le schéma, les objets de réplication et des données, mais les publications peuvent aussi être initialisées sans instantané complet.  
  
 Pour plus d’informations, consultez [initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md) et [initialiser un abonnement transactionnel sans instantané](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
  