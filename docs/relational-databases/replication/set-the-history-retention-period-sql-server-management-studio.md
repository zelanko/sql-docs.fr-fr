---
title: Définir la période de conservation de l’historique (SSMS)
description: Découvrez comment définir la période de conservation de l’historique de la base de données de distribution dans SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
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
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 6f9ada00c3166637ca1c5721b17ed950df58a4e2
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76287196"
---
# <a name="set-the-history-retention-period-sql-server-management-studio"></a>définir la période de rétention de l'historique (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Spécifiez la période de rétention de l’historique sur la page **Général** de la boîte de dialogue **Propriétés de la base de données de distribution - \<BasededonnéesDistribution>** . Ce paramètre contrôle la durée de stockage de l'historique de l'Agent de réplication. Vous pouvez accéder à cette page via la page **Général** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveurdedistribution>** . Pour plus d’informations sur l’accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de distribution ou d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-history-retention-period"></a>Pour spécifier la période de rétention de l'historique  
  
1.  Dans la page **Général** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveur_de_distribution>** , cliquez sur le bouton des propriétés ( **...** ) de la base de données de distribution.  
  
2.  Entrez une valeur dans la zone **Stocker l'historique des performances de réplication au moins chaque** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)  
  
  
