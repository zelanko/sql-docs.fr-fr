---
title: Journaux de transaction ne se n'exécutera pas après la mise à niveau | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- log shipping [SQL Server]
ms.assetid: 6727cb7d-ac01-4972-a730-dbb7cdc29705
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3187edcc72fca15e22644bcce107bf161dd0c645
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050963"
---
# <a name="log-shipping-will-not-run-after-upgrading"></a>La copie des journaux de transaction ne s'exécutera pas après la mise à niveau
  Le Conseiller de mise à niveau a détecté que vous utilisez l'envoi de journaux. La fonctionnalité d'envoi de journaux de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] n'est pas compatible avec celle de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et ne peut pas être mise à niveau directement. Après avoir effectué la mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], reconfigurez l'envoi de journaux à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de procédures stockées.  
  
## <a name="see-also"></a>Voir aussi  
 [Catégorie de travaux envoi de journaux SQL Server Agent journal entraîne la mise à niveau échoue](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)   
 [La mise à niveau modifiera le compte Proxy de SQL Server Agent utilisateur pour la UpgradedProxyAccount temporaire](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
