---
title: Valider l’abonnement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.validateandresynch.f1
helpviewer_keywords:
- Validate Subscription dialog box
ms.assetid: 74bdf5e1-b886-4284-b5fb-332bf79ae083
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3bd29769b0ba4fd5d9a48fcef07181b7ac70f7c8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63255442"
---
# <a name="validate-subscription"></a>Valider l'abonnement
  Utilisez la boîte de dialogue **valider l’abonnement** pour indiquer qu’un abonnement à une publication de fusion doit être validé lors de la prochaine exécution de l’agent de fusion pour l’abonnement. Le résultat de la validation figure dans le Moniteur de réplication. Pour plus d'informations, voir [Validate Data at the Subscriber](validate-data-at-the-subscriber.md).  
  
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
 [Valider des données répliquées](validate-data-at-the-subscriber.md)  
  
  
