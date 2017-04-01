---
title: "Propri&#233;t&#233;s du serveur de publication - Serveur de publication, Bases de donn&#233;es de publication | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.configdistwizard.pubproperties.pubdb.f1"
helpviewer_keywords: 
  - "Propriétés du serveur de publication (boîte de dialogue)"
ms.assetid: 574ea2e7-4e7b-4733-ab52-429ca93c7b0a
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Propri&#233;t&#233;s du serveur de publication - Serveur de publication, Bases de donn&#233;es de publication
  La page **Bases de données de publication** de la boîte de dialogue **Propriétés du serveur de publication** permet à un utilisateur dans le rôle serveur fixe **sysadmin** d'autoriser la réplication des bases de données. L’activation d’une base de données ne publie pas cette base de données ; au lieu de cela, il permet à un utilisateur le **db_owner** rôle de base de données fixe pour cette base de données créer une ou plusieurs publications sur la base de données.  
  
## Options  
 **Transactionnelle**  
 Activez cette case à cocher pour permettre aux utilisateurs dans le **db_owner** rôle fixe de base de données pour créer des publications de capture instantanée ou publications transactionnelles dans la base de données.  
  
 **Fusion**  
 Activez cette case à cocher pour permettre aux utilisateurs dans le **db_owner** rôle fixe de base de données pour créer des publications de fusion dans la base de données.  
  
## Voir aussi  
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Référence des propriétés de & #40 ; Réplication & #41 ;](../../relational-databases/replication/properties-reference-replication.md)  
  
  