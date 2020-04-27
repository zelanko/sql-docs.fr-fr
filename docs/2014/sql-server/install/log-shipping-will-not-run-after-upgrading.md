---
title: L’envoi de journaux ne s’exécutera pas après la mise à niveau | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server]
ms.assetid: 6727cb7d-ac01-4972-a730-dbb7cdc29705
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 952a47eaa2028819908ef7e93326c31a289a0cc2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66093983"
---
# <a name="log-shipping-will-not-run-after-upgrading"></a>La copie des journaux de transaction ne s'exécutera pas après la mise à niveau
  Le Conseiller de mise à niveau a détecté que vous utilisez l'envoi de journaux. La fonctionnalité d'envoi de journaux de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] n'est pas compatible avec celle de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et ne peut pas être mise à niveau directement. Après avoir effectué la mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], reconfigurez l'envoi de journaux à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de procédures stockées.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Agent catégorie de travaux d’envoi de journaux provoque l’échec de la mise à niveau](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)   
 [La mise à niveau va remplacer le SQL Server Agent compte proxy de l’utilisateur par le UpgradedProxyAccount temporaire](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
