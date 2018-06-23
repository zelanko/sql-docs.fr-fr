---
title: Définir des options de résolution des conflits de mise à jour en attente (SQL Server Management Studio) | Microsoft Docs
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
- conflict resolution [SQL Server replication], queued updating subscriptions
- queued updating subscriptions [SQL Server replication]
ms.assetid: bb6b6c71-42c7-421a-a0fa-d5594d27e35d
caps.latest.revision: 32
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: d4b372dc750822d965474d93d40ff7911cf0cf7c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045342"
---
# <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a>définir des options de résolution des conflits de mise à jour en attente (SQL Server Management Studio)
  Définissez les options de résolution des conflits pour les publications qui prennent en charge les abonnements avec mise à jour en attente, sur la page **Options d’abonnement** de la boîte de dialogue **Propriétés de la publication - \<Publication>**. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](view-and-modify-publication-properties.md).  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a>Pour définir les options de résolution des conflits de mise à jour en attente  
  
1.  Sur la page **Options d’abonnement** de la boîte de dialogue **Propriétés de la publication - \<Publication>**, sélectionnez l’une des valeurs ci-après pour l’option **Stratégie de résolution de conflit** :  
  
    -   **Conserver la modification apportée au serveur de publication**  
  
    -   **Conserver la modification apportée à l'abonné**  
  
    -   **Réinitialiser l'abonnement**  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Activer les abonnements de mise à jour pour les publications transactionnelles](enable-updating-subscriptions-for-transactional-publications.md)   
 [Queued Updating Conflict Detection and Resolution](../transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)  
  
  