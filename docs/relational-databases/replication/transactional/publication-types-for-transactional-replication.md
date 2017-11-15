---
title: "Types de publication pour la réplication transactionnelle | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transactional replication, publications
ms.assetid: ad66aa34-3e37-401e-a6a1-fc1514eb6d50
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 600d56835d5b80513a7bd1ce5098acda22c1ed26
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="publication-types-for-transactional-replication"></a>Types de publication pour la réplication transactionnelle
  La réplication transactionnelle propose trois types de publication :  
  
|Type de publication|Description|  
|----------------------|-----------------|  
|Publication transactionnelle standard|Adaptée aux topologies dans lesquelles toutes les données de l'Abonné sont en lecture seule (la réplication transactionnelle ne l'applique pas sur l'Abonné).<br /><br /> Les publications transactionnelles standard sont créées par défaut lorsque vous utilisez Transact-SQL ou Replication Management Objects. Lorsque vous utilisez l'Assistant Nouvelle publication, elles sont créées par la sélection de l'option **Publication transactionnelle** dans la page **Type de publication** .<br /><br /> Pour plus d’informations sur la création de publications, consultez [Publier des données et des objets de base de données](../../../relational-databases/replication/publish/publish-data-and-database-objects.md).|  
|Publication transactionnelle dans une topologie d'égal à égal|Les caractéristiques de ce type de publication sont les suivantes :<br /><br /> -Chaque emplacement possède des données identiques et est à la fois un serveur de publication et un abonné.<br /><br /> -La même ligne ne peut être modifiée qu’à un seul emplacement à la fois.<br /><br /> -Cette topologie convient surtout aux environnements serveur exigeant une disponibilité élevée et des possibilités d’évolutivité en lecture.<br /><br /> <br /><br /> Pour plus d'informations, consultez [Peer-to-Peer Transactional Replication](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication transactionnelle](../../../relational-databases/replication/transactional/transactional-replication.md)  
  
  
