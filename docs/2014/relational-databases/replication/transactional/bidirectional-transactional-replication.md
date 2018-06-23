---
title: Réplication transactionnelle bidirectionnelle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
caps.latest.revision: 26
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 59817a189d1e52f7d4e8532c35fc024aa1745e3f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151879"
---
# <a name="bidirectional-transactional-replication"></a>réplication transactionnelle bidirectionnelle
  Une réplication transactionnelle bidirectionnelle est une topologie de réplication transactionnelle spécifique qui permet à deux serveurs d'échanger des modifications : chaque serveur publie des données puis s'abonne à une publication contenant les mêmes données provenant de l'autre serveur. Le paramètre **@loopback_detection** de [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) a la valeur TRUE pour garantir que les modifications sont uniquement envoyées à l’Abonné et ne renvoient pas la modification au serveur de publication.  
  
 Dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et les versions ultérieures, cette topologie est également prise en charge par la réplication transactionnelle d'égal à égal, mais la réplication bidirectionnelle peut contribuer à améliorer les performances.  
  
## <a name="see-also"></a>Voir aussi  
 [Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md)  
  
  
