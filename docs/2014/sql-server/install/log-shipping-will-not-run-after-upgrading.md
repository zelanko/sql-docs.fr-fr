---
title: Journaux de transaction ne sera ne pas exécuté après la mise à niveau | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server]
ms.assetid: 6727cb7d-ac01-4972-a730-dbb7cdc29705
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e56eff5064cf797e4acdfff10f346a43ee4210de
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63195082"
---
# <a name="log-shipping-will-not-run-after-upgrading"></a>La copie des journaux de transaction ne s'exécutera pas après la mise à niveau
  Le Conseiller de mise à niveau a détecté que vous utilisez l'envoi de journaux. La fonctionnalité d'envoi de journaux de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] n'est pas compatible avec celle de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et ne peut pas être mise à niveau directement. Après avoir effectué la mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], reconfigurez l'envoi de journaux à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de procédures stockées.  
  
## <a name="see-also"></a>Voir aussi  
 [Catégorie de travaux SQL Server Agent journaux de transaction provoque l’échec mise à niveau](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)   
 [La mise à niveau sera alors le compte Proxy de SQL Server Agent utilisateur le UpgradedProxyAccount temporaire](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
