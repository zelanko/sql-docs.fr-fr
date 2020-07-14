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
ms.openlocfilehash: bc04a0b78c93666b4213acea3a1f59af5dc5b5fb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767657"
---
# <a name="set-the-history-retention-period-sql-server-management-studio"></a>définir la période de rétention de l'historique (SQL Server Management Studio)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Spécifiez la période de rétention de l’historique dans la page **Général** de la boîte de dialogue **Propriétés de la base de données de distribution - \<DistributionDatabase>** . Ce paramètre contrôle la durée de stockage de l'historique de l'Agent de réplication. Vous pouvez accéder à cette page via la page **Général** de la boîte de dialogue **Propriétés du serveur de distribution - \<Distributor>** . Pour plus d’informations sur l’accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de distribution ou d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-history-retention-period"></a>Pour spécifier la période de rétention de l'historique  
  
1.  Dans la page **Général** de la boîte de dialogue **Propriétés du serveur de distribution - \<Distributor>** , cliquez sur le bouton des propriétés ( **…** ) de la base de données de distribution.  
  
2.  Entrez une valeur dans la zone **Stocker l'historique des performances de réplication au moins chaque** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)  
  
  
