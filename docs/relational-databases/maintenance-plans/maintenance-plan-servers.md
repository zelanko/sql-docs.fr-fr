---
title: Plan de maintenance (Serveurs) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.maint.servers.f1
- sql13.swb.maint.maintplanproperties.server.f1
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 758892ce93264618ee293e8a5de074ab2a513f11
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="maintenance-plan-servers"></a>Plan de maintenance (Serveurs)
  La boîte de dialogue **Serveurs** permet de sélectionner les serveurs sur lesquels vous souhaitez exécuter le plan de maintenance.  
  
 Pour créer un plan de maintenance multiserveur, vous devez configurer un environnement multiserveur contenant un serveur maître et un ou plusieurs serveurs cibles. Pour les plans de maintenance multiserveurs, le serveur local doit être configuré comme serveur maître. Dans les environnements multiserveurs, cette boîte de dialogue affiche le serveur maître **(local)** et tous les serveurs cibles correspondants. Un travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est créé pour le serveur local. Celui-ci est activé ou désactivé selon que vous avez sélectionné le serveur **(local)** . Si des serveurs cibles sont sélectionnés, un travail multiserveur est créé et téléchargé vers chacun des serveurs cibles sélectionnés. Si aucun serveur cible n'est sélectionné, le travail multiserveur est supprimé.  
  
## <a name="see-also"></a>Voir aussi  
 [Plans de maintenance](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Créer un environnement multi-serveur](http://msdn.microsoft.com/library/edc2b60d-15da-40a1-8ba3-f1d473366ee6)   
 [Créer un serveur maître](http://msdn.microsoft.com/library/05739a73-1fdf-4d9d-92a6-70f328380322)   
 [Créer un serveur cible](http://msdn.microsoft.com/library/13aabe2d-67fe-4c67-8d49-2928dd705b7a)  
  
  
