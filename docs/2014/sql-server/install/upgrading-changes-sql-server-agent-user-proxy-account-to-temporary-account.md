---
title: La mise à niveau modifiera le compte Proxy de SQL Server Agent utilisateur pour la temporaire UpgradedProxyAccount | Documents Microsoft
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
ms.assetid: cd2d08c3-4e56-4034-8b68-0c78df8b5471
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9bae867b97a9fc63b97506fd8900e68b670b8013
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039209"
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
 [Catégorie de travaux envoi de journaux SQL Server Agent journal entraîne la mise à niveau échoue](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)   
 [Envoi de journaux ne s’exécutera pas après la mise à niveau](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)  
  
  