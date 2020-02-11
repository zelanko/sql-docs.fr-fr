---
title: Définir la période de rétention de la distribution pour les publications transactionnelles (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transaction retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: 9a98c53a-fea5-4235-b23d-6c69587c5676
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8c272cef68f1fc392aed05a3d8d45ab665674e39
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62676624"
---
# <a name="set-the-distribution-retention-period-for-transactional-publications-sql-server-management-studio"></a>définir la période de rétention de la distribution pour les publications transactionnelles (SQL Server Management Studio)
  Spécifiez les périodes de rétention de distribution minimale et maximale dans la boîte **de \<dialogue Propriétés de la base de données de distribution-DistributionDatabase>** . Vous pouvez y accéder à l’aide de la page **Général** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveur_de_distribution>**. Pour plus d’informations sur l’accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de distribution ou d’un serveur de publication](view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-distribution-retention-period"></a>Pour spécifier la période de rétention de la distribution  
  
1.  Sur la page **général** de la boîte de dialogue Propriétés du serveur de distribution **- \<>** du serveur de distribution, cliquez sur le bouton des propriétés (**...**) de la base de données de distribution.  
  
2.  Pour spécifier la période de rétention de la distribution minimale, entrez une valeur dans la zone **Au moins** et pour définir la période de rétention de la distribution maximale, indiquez une valeur dans la zone **Mais pas plus de** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la distribution](configure-distribution.md)   
 [Expiration et désactivation des abonnements](subscription-expiration-and-deactivation.md)  
  
  
