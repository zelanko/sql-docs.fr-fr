---
title: Supprimer une instance de cluster de basculement
description: Suivez cette procédure pour désinstaller une instance de cluster de basculement SQL Server. Cet article contient des points importants que vous devez connaître avant de poursuivre.
ms.custom: seo-lt-2019
ms.date: 12/13/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], removing failover clustered instance
- failover clustering [SQL Server], removing failover clustered instance
- uninstalling failover clustered instances
- removing failover clustered instances
ms.assetid: bf63353b-69cf-4c5c-98ea-7b151e36537f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dba18abbd7eb5938b7f2fa4d0c3caff8d5d6f567
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85897669"
---
# <a name="remove-a-sql-server-failover-cluster-instance-setup"></a>Supprimer une instance de cluster de basculement SQL Server (programme d'installation)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Suivez cette procédure pour désinstaller une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  Pour mettre à jour ou supprimer un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , vous devez être un administrateur local autorisé à se connecter en tant que service sur tous les nœuds du cluster de basculement.  
  
 **Avant de commencer**  
  
 Prenez en compte les points importants suivants avant de désinstaller un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
-   Si [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client est désinstallé par accident, les ressources [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne pourront pas démarrer. Pour réinstaller [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, exécutez le programme d'installation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour installer les éléments requis de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   Si vous avez désinstallé un cluster de basculement comportant plusieurs ressources de cluster IP SQL, vous devez supprimer les ressources IP SQL supplémentaires à l'aide de l'administrateur de clusters.  
  
 Pour plus d’informations sur la syntaxe de l’invite de commandes, consultez [Installer SQL Server 2016 à partir de l’invite de commandes](../../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).  
  
### <a name="to-uninstall-a-ssnoversion-failover-cluster"></a>Pour désinstaller un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
1.  Pour désinstaller un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , utilisez la fonctionnalité Supprimer un nœud fournie par le programme d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour supprimer chaque nœud individuellement. Pour plus d’informations, consultez [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et lire les fichiers journaux d'installation de SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
