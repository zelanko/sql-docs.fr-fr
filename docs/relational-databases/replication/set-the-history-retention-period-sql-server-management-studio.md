---
title: Définir la période de rétention de l’historique (SQL Server Management Studio) | Microsoft Docs
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
- history retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: c288daab-5181-4d4b-ba2a-8a147098e758
caps.latest.revision: 36
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1cace65ed509d98eb164128a85866631d2e15f3e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="set-the-history-retention-period-sql-server-management-studio"></a>définir la période de rétention de l'historique (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Spécifiez la période de rétention de l’historique sur la page **Général** de la boîte de dialogue **Propriétés de la base de données de distribution - \<BasededonnéesDistribution>**. Ce paramètre contrôle la durée de stockage de l'historique de l'Agent de réplication. Vous pouvez accéder à cette page via la page **Général** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveurdedistribution>**. Pour plus d’informations sur l’accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de distribution ou d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-history-retention-period"></a>Pour spécifier la période de rétention de l'historique  
  
1.  Dans la page **Général** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveurdedistribution>**, cliquez sur le bouton des propriétés (**…**) de la base de données de distribution.  
  
2.  Entrez une valeur dans la zone **Stocker l'historique des performances de réplication au moins chaque** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a> Voir aussi  
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)  
  
  
