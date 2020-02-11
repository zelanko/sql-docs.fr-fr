---
title: La mise à niveau va remplacer le SQL Server Agent compte proxy de l’utilisateur par le UpgradedProxyAccount temporaire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
ms.assetid: cd2d08c3-4e56-4034-8b68-0c78df8b5471
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a82cbcc9ef1ab57279b44cc83509cb1efad855ca
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66091402"
---
# <a name="upgrading-will-change-the-sql-server-agent-user-proxy-account-to-the-temporary-upgradedproxyaccount"></a>La mise à niveau entraînera la modification du compte proxy utilisateur de l'Agent SQL Server en UpgradedProxyAccount temporaire
  Les plans de maintenance de base de données dans lesquels la copie des journaux de transaction est activée ne seront pas activés après la mise à niveau.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent  
  
## <a name="description"></a>Description  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit un nouvel ensemble de fonctions de copie des journaux de transaction qui ne sont pas directement compatibles avec les plans de maintenance de base de données.  
  
## <a name="corrective-action"></a>Action corrective  
 Les utilisateurs [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] dont les plans de maintenance de base de données contiennent des fonctions de copie des journaux de transaction doivent configurer la copie des journaux de transaction en utilisant les nouvelles fonctions. Pour plus d'informations, recherchez "copie des journaux de transaction" dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Agent catégorie de travaux d’envoi de journaux provoque l’échec de la mise à niveau](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)   
 [La copie des journaux de transaction ne s'exécutera pas après la mise à niveau](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)  
  
  
