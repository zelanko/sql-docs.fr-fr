---
title: Valider l’abonnement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.validateandresynch.f1
helpviewer_keywords:
- Validate Subscription dialog box
ms.assetid: 74bdf5e1-b886-4284-b5fb-332bf79ae083
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8f561cba91981d1b435fab07dcf746f55e30b44d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48131089"
---
# <a name="validate-subscription"></a>Valider l'abonnement
  Utilisez la boîte de dialogue **Valider l'abonnement** pour indiquer qu'un abonnement à une publication de fusion doit être validée lors de la prochaine exécution de l'Agent de fusion de l'abonnement. Le résultat de la validation figure dans le Moniteur de réplication. Pour plus d'informations, voir [Validate Data at the Subscriber](validate-data-at-the-subscriber.md).  
  
 Vous pouvez également valider tous les abonnements à une publication de fusion en cliquant avec le bouton droit de la souris sur une publication dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et en cliquant sur **Valider tous les abonnements**.  
  
## <a name="options"></a>Options  
 **Date de la dernière tentative de validation**  
 Date de la dernière session de l'Agent de fusion qui incluait la validation d'abonnement, que la validation ait abouti ou non.  
  
 **Date de la dernière validation réussie**  
 Date de la dernière session de l'Agent de fusion qui incluait une validation d'abonnement réussie.  
  
 **Valider cet abonnement**  
 Sélectionnez cette option pour valider l'abonnement.  
  
 **Options**  
 Cliquez pour accéder à la boîte de dialogue **Options de validation d'abonnement** qui permet d'indiquer si vous voulez utiliser la validation du nombre de lignes ou la validation de somme de contrôle.  
  
## <a name="see-also"></a>Voir aussi  
 [Valider des données répliquées](validate-replicated-data.md)  
  
  
