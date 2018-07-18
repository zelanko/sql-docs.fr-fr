---
title: La mise à niveau sera alors le compte Proxy de SQL Server Agent utilisateur le temporaire UpgradedProxyAccount | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
ms.assetid: cd2d08c3-4e56-4034-8b68-0c78df8b5471
caps.latest.revision: 18
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 14b79ad393db1360520e060b118c8a4e280e358b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37292089"
---
# <a name="upgrading-will-change-the-sql-server-agent-user-proxy-account-to-the-temporary-upgradedproxyaccount"></a>La mise à niveau entraînera la modification du compte proxy utilisateur de l'Agent SQL Server en UpgradedProxyAccount temporaire
  Les plans de maintenance de base de données dans lesquels la copie des journaux de transaction est activée ne seront pas activés après la mise à niveau.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit un nouvel ensemble de fonctions de copie des journaux de transaction qui ne sont pas directement compatibles avec les plans de maintenance de base de données.  
  
## <a name="corrective-action"></a>Action corrective  
 Les utilisateurs [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] dont les plans de maintenance de base de données contiennent des fonctions de copie des journaux de transaction doivent configurer la copie des journaux de transaction en utilisant les nouvelles fonctions. Pour plus d'informations, recherchez "copie des journaux de transaction" dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Catégorie de travaux SQL Server Agent journaux de transaction provoque l’échec mise à niveau](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)   
 [La copie des journaux de transaction ne s’exécute pas après la mise à niveau](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)  
  
  
