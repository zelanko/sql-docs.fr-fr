---
title: Catégorie de travaux de copie des journaux de l’Agent SQL Server provoque l’échec de la mise à niveau | Documents Microsoft
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
- log shipping [SQL Server Agent]
- job categories [SQL Server Agent]
ms.assetid: ef05ce53-c6ce-42ec-9df8-46c951626424
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 47d7d5024d234478b8b54e3c05b3c22335758782
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051196"
---
# <a name="sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail"></a>La catégorie affectée à l'opération de copie des journaux de transaction de l'Agent SQL Server provoque l'échec de la mise à niveau
  Le processus de mise à niveau échouera si une catégorie de travail de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent nommée Copie des journaux de transactions existe.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="description"></a>Description  
 Il y a une catégorie de travail système nommée Copie des journaux de transactions. Si une installation en cours de mise à niveau contient déjà une catégorie de travail créée par l'utilisateur, nommée Copie des journaux de transaction, vous devez la renommer avant de procéder à la mise à niveau ; sinon, le processus de mise à niveau échouera.  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi de journaux ne s’exécutera pas après la mise à niveau](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)   
 [La mise à niveau modifiera le compte Proxy de SQL Server Agent utilisateur pour la UpgradedProxyAccount temporaire](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [Problèmes de mise à niveau de SQL Server Agent](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  