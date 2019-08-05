---
title: Définir la période de rétention de l’historique (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- history retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: c288daab-5181-4d4b-ba2a-8a147098e758
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 9a33317c8f430a3665c47e94441e8f78c68085c6
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768380"
---
# <a name="set-the-history-retention-period-sql-server-management-studio"></a>définir la période de rétention de l'historique (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Spécifiez la période de rétention de l’historique sur la page **Général** de la boîte de dialogue **Propriétés de la base de données de distribution - \<BasededonnéesDistribution>** . Ce paramètre contrôle la durée de stockage de l'historique de l'Agent de réplication. Vous pouvez accéder à cette page via la page **Général** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveurdedistribution>** . Pour plus d’informations sur l’accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de distribution ou d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-history-retention-period"></a>Pour spécifier la période de rétention de l'historique  
  
1.  Dans la page **Général** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveurdedistribution>** , cliquez sur le bouton des propriétés ( **…** ) de la base de données de distribution.  
  
2.  Entrez une valeur dans la zone **Stocker l'historique des performances de réplication au moins chaque** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)  
  
  
