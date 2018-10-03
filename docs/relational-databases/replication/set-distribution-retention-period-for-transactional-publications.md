---
title: Définir la période de rétention de la distribution pour les publications transactionnelles | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
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
ms.openlocfilehash: 11ffd55e30a238c443ccd4d1dcbeff5f658cba5d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792077"
---
# <a name="set-distribution-retention-period-for-transactional-publications"></a>Définir la période de rétention de la distribution pour les publications transactionnelles
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Spécifiez les périodes de rétention de distribution minimale et maximale dans la boîte de dialogue **Propriétés de la base de données de distribution - \<Base_de_données_de_distribution>**. Vous pouvez y accéder à l’aide de la page **Général** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveur_de_distribution>**. Pour plus d’informations sur l’accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de distribution ou d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-distribution-retention-period"></a>Pour spécifier la période de rétention de la distribution  
  
1.  Dans la page **Général** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveur_de_distribution>**, cliquez sur le bouton des propriétés (**...**) de la base de données de distribution.  
  
2.  Pour spécifier la période de rétention de la distribution minimale, entrez une valeur dans la zone **Au moins** et pour définir la période de rétention de la distribution maximale, indiquez une valeur dans la zone **Mais pas plus de** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a> Voir aussi  
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)   
 [Expiration et désactivation des abonnements](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
