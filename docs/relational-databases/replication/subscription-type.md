---
title: "Type d’abonnement | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newsubwizard.subscriptiontype.f1
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0541842347278d70b5d759737bf0c37b1f91bfab
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="subscription-type"></a>Type d'abonnement
  La réplication de fusion propose deux types d'abonnements : l'abonnement serveur et l'abonnement client (connus dans les versions précédentes de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sous les noms respectifs d'abonnement global et abonnement local). Les abonnés disposant d'un abonnement serveur peuvent :  
  
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
 [Créer un abonnement par extraction](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [S’abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
