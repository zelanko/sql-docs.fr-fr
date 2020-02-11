---
title: Type d’abonnement | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subscriptiontype.f1
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d936c1a1086f13d43bc38758f86a0ab80f757f7b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63249380"
---
# <a name="subscription-type"></a>Type d'abonnement
  La réplication de fusion propose deux types d’abonnement : serveur et client (référencés [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans les versions précédentes de, respectivement, global et local). Les abonnés disposant d'un abonnement serveur peuvent :  
  
-   republier des données à d'autres Abonnés ;  
  
-   agir en l'état d'autre partenaire de synchronisation ;  
  
-   résoudre des conflits d'après une liste de priorités que vous établissez.  
  
 La plupart des Abonnés n'ont pas besoin de cette fonctionnalité et peuvent passer par un abonnement client. Les abonnements client permettent en effet la détection et la résolution de conflits, mais dans ce cas de figure les Abonnés ne se voient pas affecter de priorité : le premier Abonné soumettant une modification à un serveur de publication bénéficie de la préférence de validité des données sur tout conflit pouvant se produire relatif à cette modification.  
  
> [!NOTE]  
>  Vous ne pouvez pas modifier le type d'un abonnement après sa création.  
  
## <a name="options"></a>Options  
 **Propriétés de l'abonnement**  
 Permet de sélectionner pour chaque Abonné la valeur **Client** ou **Serveur** dans la zone de liste déroulante de la colonne **Type d'abonnement** . Dans le cas d'Abonnés bénéficiant d'un abonnement serveur, vous devez saisir un nombre compris entre 0 et 99,99 dans la colonne **Priorité pour la résolution des conflits** : plus ce nombre est grand, plus la priorité de l'Abonné est forte.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [S'abonner à des publications](subscribe-to-publications.md)  
  
  
