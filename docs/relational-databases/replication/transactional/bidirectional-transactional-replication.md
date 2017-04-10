---
title: "R&#233;plication transactionnelle bidirectionnelle | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "réplication bidirectionnelle"
  - "réplication transactionnelle, réplication bidirectionnelle"
  - "réplication transactionnelle bidirectionnelle"
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
caps.latest.revision: 27
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 27
---
# R&#233;plication transactionnelle bidirectionnelle
  Une réplication transactionnelle bidirectionnelle est une topologie de réplication transactionnelle spécifique qui permet à deux serveurs d'échanger des modifications : chaque serveur publie des données puis s'abonne à une publication contenant les mêmes données provenant de l'autre serveur. Le **@loopback_detection** paramètre de [sp_addsubscription & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) est définie sur TRUE pour vous assurer que les modifications sont uniquement envoyées à l’abonné et n’entraînent pas la modification de leur renvoyée au serveur de publication.  
  
 Dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et versions ultérieures, cette topologie est également pris en charge par la réplication transactionnelle égal à égal, mais la réplication bidirectionnelle peut fournir de meilleures performances.  
  
## Voir aussi  
 [Réplication transactionnelle d'égal à égal](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  