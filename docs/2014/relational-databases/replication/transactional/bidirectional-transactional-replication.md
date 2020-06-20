---
title: Réplication transactionnelle bidirectionnelle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 57b18dde2e7134e0ba9eb6a9b2e8f5357d171a55
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85043188"
---
# <a name="bidirectional-transactional-replication"></a>réplication transactionnelle bidirectionnelle
  Une réplication transactionnelle bidirectionnelle est une topologie de réplication transactionnelle spécifique qui permet à deux serveurs d'échanger des modifications : chaque serveur publie des données puis s'abonne à une publication contenant les mêmes données provenant de l'autre serveur. Le **@loopback_detection** paramètre de [sp_addsubscription &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) a la valeur true pour garantir que les modifications sont envoyées uniquement à l’abonné et n’entraînent pas le renvoi de la modification au serveur de publication.  
  
 Dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et les versions ultérieures, cette topologie est également prise en charge par la réplication transactionnelle d'égal à égal, mais la réplication bidirectionnelle peut contribuer à améliorer les performances.  
  
## <a name="see-also"></a>Voir aussi  
 [Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md)  
  
  
