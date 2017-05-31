---
title: "Abonnements pouvant être mis à jour | Microsoft Docs"
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
- sql13.rep.newsubwizard.updatablesubscriptions.f1
ms.assetid: 8e9a13a0-6b24-47c6-9d83-3cbaf08f673d
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8d9a0e7625d424dea66291cc8b9707d1bd660820
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="updatable-subscriptions"></a>Abonnements pouvant être mis à jour
  Avec la réplication transactionnelle, les données répliquées doivent être traitées en lecture seule. Toutefois, vous pouvez modifier les données répliquées au niveau d'un abonné [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant des abonnements pouvant être mis à jour. Si vous devez modifier des données sur l'Abonné, vous pouvez choisir l'une des options suivantes selon vos besoins.  
  
|Type d'abonnement pouvant être mis à jour|Spécifications|  
|---------------------------------|------------------|  
|Mise à jour immédiate|Le serveur de publication et l'Abonné doivent être connectés pour mettre à jour les données sur l'Abonné.|  
|Mise à jour en attente|Le serveur de publication et l'Abonné n'ont pas besoin d'être connectés pour mettre à jour les données sur l'Abonné. Les mises à jour peuvent être effectuées hors ligne et synchronisées ensuite entre le serveur de publication et l'Abonné.|  
  
## <a name="options"></a>Options  
 **Répliquer les modifications de l'Abonné**  
 Activez la case à cocher dans la colonne **Répliquer** pour chaque abonné qui doit pouvoir effectuer des mises à jour. Pour les abonnés qui peuvent effectuer des mises à jour, sélectionnez l'option appropriée dans la zone de liste déroulante de la colonne **Valider sur le serveur de publication** :  
  
-   Sélectionnez **Enregistrer les modifications simultanément** pour un abonnement mis à jour immédiatement.  
  
-   Sélectionnez **Mettre les modifications en file d'attente et valider dès que possible** pour un abonnement mis à jour en file d'attente.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un abonnement par extraction](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Créer un abonnement par émission de données](../../relational-databases/replication/create-a-push-subscription.md)   
 [S’abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [Abonnements pouvant être mis à jour pour la réplication transactionnelle](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
