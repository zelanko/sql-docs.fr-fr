---
title: SQL Server Agent catégorie de travaux d’envoi de journaux provoque l’échec de la mise à niveau | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
- job categories [SQL Server Agent]
ms.assetid: ef05ce53-c6ce-42ec-9df8-46c951626424
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7145d846657613b50706ebe75c9832f40f49383e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66092038"
---
# <a name="sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail"></a>La catégorie affectée à l'opération de copie des journaux de transaction de l'Agent SQL Server provoque l'échec de la mise à niveau
  Le processus de mise à niveau échouera si une catégorie de travail de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent nommée Copie des journaux de transactions existe.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="description"></a>Description  
 Il y a une catégorie de travail système nommée Copie des journaux de transactions. Si une installation en cours de mise à niveau contient déjà une catégorie de travail créée par l'utilisateur, nommée Copie des journaux de transaction, vous devez la renommer avant de procéder à la mise à niveau ; sinon, le processus de mise à niveau échouera.  
  
## <a name="see-also"></a>Voir aussi  
 [L’envoi de journaux ne s’exécutera pas après la mise à niveau](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)   
 [La mise à niveau va remplacer le SQL Server Agent compte proxy de l’utilisateur par le UpgradedProxyAccount temporaire](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [Problèmes de mise à niveau de l'Agent SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
