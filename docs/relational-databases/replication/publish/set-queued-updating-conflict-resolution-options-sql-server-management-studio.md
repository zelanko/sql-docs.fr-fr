---
title: Définir des options de résolution des conflits de mise à jour en attente (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- queued updating subscriptions [SQL Server replication]
ms.assetid: bb6b6c71-42c7-421a-a0fa-d5594d27e35d
caps.latest.revision: 34
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e5f471a69c3c0c7693cd7eac27d04692c65b6111
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a>définir des options de résolution des conflits de mise à jour en attente (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Définissez les options de résolution des conflits pour les publications qui prennent en charge les abonnements avec mise à jour en attente, sur la page **Options d’abonnement** de la boîte de dialogue **Propriétés de la publication - \<Publication>**. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a>Pour définir les options de résolution des conflits de mise à jour en attente  
  
1.  Sur la page **Options d’abonnement** de la boîte de dialogue **Propriétés de la publication - \<Publication>**, sélectionnez l’une des valeurs ci-après pour l’option **Stratégie de résolution de conflit** :  
  
    -   **Conserver la modification apportée au serveur de publication**  
  
    -   **Conserver la modification apportée à l'abonné**  
  
    -   **Réinitialiser l'abonnement**  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a> Voir aussi  
 [Activer les abonnements de mise à jour pour les publications transactionnelles](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)   
 [Queued Updating Conflict Detection and Resolution](../../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)  
  
  
