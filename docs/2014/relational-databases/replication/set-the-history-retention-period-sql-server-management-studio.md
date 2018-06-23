---
title: Définir la période de rétention de l’historique (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- history retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: c288daab-5181-4d4b-ba2a-8a147098e758
caps.latest.revision: 34
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: bc2bed6e9f65245168ec9fac3160345e80371d62
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039746"
---
# <a name="set-the-history-retention-period-sql-server-management-studio"></a>définir la période de rétention de l'historique (SQL Server Management Studio)
  Spécifiez la période de rétention de l’historique sur la page **Général** de la boîte de dialogue **Propriétés de la base de données de distribution - \<BasededonnéesDistribution>**. Ce paramètre contrôle la durée de stockage de l'historique de l'Agent de réplication. Vous pouvez accéder à cette page via la page **Général** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveurdedistribution>**. Pour plus d’informations sur l’accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de distribution ou d’un serveur de publication](view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-history-retention-period"></a>Pour spécifier la période de rétention de l'historique  
  
1.  Dans la page **Général** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveurdedistribution>**, cliquez sur le bouton des propriétés (**…**) de la base de données de distribution.  
  
2.  Entrez une valeur dans la zone **Stocker l'historique des performances de réplication au moins chaque** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la distribution](configure-distribution.md)  
  
  