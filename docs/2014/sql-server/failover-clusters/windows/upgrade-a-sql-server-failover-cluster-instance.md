---
title: Mettre à niveau un Cluster de basculement SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- upgrading failover clusters
- clusters [SQL Server], upgrading
- failover clustering [SQL Server], upgrading
ms.assetid: daac41fe-7d0b-4f14-84c2-62952ad8cbfa
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a7a8d5f04808582bd56c106adce0df2c1f66aa77
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62913694"
---
# <a name="upgrade-a-sql-server-failover-cluster"></a>Mettre à niveau un cluster de basculement SQL Server
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge la mise à niveau du [!INCLUDE[ssDE](../../../includes/ssde-md.md)] et d'[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] à partir des clusters de basculement [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] et [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] séparément sur tous les nœuds de cluster de basculement.  
  
 Voici les détails de prise en charge :  
  
-   La mise à niveau est prise en charge par le biais de l'interface utilisateur et à partir de l'invite de commandes. Pour plus d’informations, consultez [Mettre à niveau une instance de cluster de basculement SQL Server &#40;programme d’installation&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md) et [Installer SQL Server 2014 à partir de l’invite de commandes](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
-   La mise à niveau à partir de [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] -vous pouvez exécuter la mise à niveau à partir de l’invite de commandes sur chaque nœud de cluster de basculement, ou à l’aide de l’interface utilisateur d’installation pour mettre à niveau chaque nœud du cluster. Si les fonctionnalités Recherche en texte intégral et Réplication n'existent pas sur l'instance mise à niveau, elles seront automatiquement installées, sans option pour les omettre.  
  
-   Installation de Service Packs - Vous devez appliquer les Service Packs et correctifs logiciels [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aux clusters de basculement [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] séparément sur tous les nœuds.  
  
-   Les scénarios suivants ne sont pas pris en charge :  
  
    -   Vous ne pouvez pas effectuer une migration à partir d'une instance autonome de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vers un cluster de basculement.  
  
    -   Vous ne pouvez pas ajouter de fonctionnalités à un cluster de basculement, par exemple ajouter le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] à un cluster de basculement existant [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] uniquement.  
  
    -   Vous ne pouvez pas rétrograder un nœud de cluster de basculement à une instance autonome.  
  
-   Pour plus d’informations, consultez [Instances de cluster de basculement AlwaysOn (SQL Server)](always-on-failover-cluster-instances-sql-server.md).  
  
## <a name="upgrading-a-includessnoversionincludesssnoversion-mdmd-multi-subnet-failover-cluster"></a>Mise à niveau d'un cluster de basculement de sous-réseaux multiples [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
 Vous ne pouvez pas mettre à niveau directement un non-sous-réseaux multiples [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de cluster de basculement à un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cluster de basculement de sous-réseaux multiples. Pour plus d’informations, consultez [Mettre à niveau une instance de cluster de basculement SQL Server &#40;programme d’installation&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mises à niveau de la version et de l'édition prises en charge](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [Mettre à niveau une Instance de Cluster de basculement SQL Server &#40;le programme d’installation&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md)   
 [Installer SQL Server 2014 à partir de l’invite de commandes](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)  
  
  
