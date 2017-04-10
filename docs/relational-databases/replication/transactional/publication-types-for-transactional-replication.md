---
title: "Types de publication pour la r&#233;plication transactionnelle | Microsoft Docs"
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
  - "réplication transactionnelle, publications"
ms.assetid: ad66aa34-3e37-401e-a6a1-fc1514eb6d50
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 32
---
# Types de publication pour la r&#233;plication transactionnelle
  La réplication transactionnelle propose trois types de publication :  
  
|Type de publication|Description|  
|----------------------|-----------------|  
|Publication transactionnelle standard|Adaptée aux topologies dans lesquelles toutes les données de l'Abonné sont en lecture seule (la réplication transactionnelle ne l'applique pas sur l'Abonné).<br /><br /> Les publications transactionnelles standard sont créées par défaut lorsque vous utilisez Transact-SQL ou Replication Management Objects. Lorsque vous utilisez l’Assistant Nouvelle Publication, ils sont créés en sélectionnant **publication transactionnelle** sur la **Type de Publication** page.<br /><br /> Pour plus d’informations sur la création de publications, consultez [publier des données et des objets de base de données](../../../relational-databases/replication/publish/publish-data-and-database-objects.md).|  
|Publication transactionnelle dans une topologie d'égal à égal|Les caractéristiques de ce type de publication sont les suivantes :<br /><br /> -Chaque emplacement possède des données identiques et est à la fois un serveur de publication et un abonné.<br /><br /> -La même ligne ne peut être modifiée qu’à un seul emplacement à la fois.<br /><br /> -Cette topologie convient surtout aux environnements serveur exigeant une disponibilité élevée et des possibilités d’évolutivité en lecture.<br /><br /> <br /><br /> Pour plus d’informations, consultez [égal à la réplication transactionnelle](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).|  
  
## Voir aussi  
 [Réplication transactionnelle](../../../relational-databases/replication/transactional/transactional-replication.md)  
  
  