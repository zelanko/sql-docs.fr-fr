---
title: Restaurer la base de données Master
description: Restaurez la base de données Master dans Analytics Platform System (APS).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 6d122881f5283da86f66494ee2f049756d151551
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400454"
---
# <a name="restore-the-master-database-in-analytics-platform-system-aps"></a>Restaurer la base de données Master dans Analytics Platform System (APS)
La page maître de la **restauration** de la SQL Server PDW Configuration Manager vous permet de restaurer la base de données Master à partir d’une sauvegarde.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
> [!IMPORTANT]  
> Pour effectuer la restauration, SQL Server PDW devez supprimer la base de données Master active, qui contient les informations de sécurité de l’utilisateur et le catalogue de la base de données. Nous vous recommandons d’effectuer une sauvegarde de la base de données Master en cours avant d’effectuer la restauration.  
  
## <a name="to-restore-the-master-database"></a>Pour restaurer la base de données master  
  
1.  Lancez le Configuration Manager. Pour plus d’informations, consultez [la page lancement du&#41;Configuration Manager &#40;Analytics Platform System ](launch-the-configuration-manager.md).  
  
2.  Dans le volet gauche de la Configuration Manager, cliquez sur **restaurer la base**de référence.  
  
3.  Sélectionnez la sauvegarde principale à restaurer.  
  
4.  Cliquez sur **Appliquer**.  
  
5.  Pour effectuer la restauration, SQL Server PDW arrête tous les services d’appliance et déconnecte tous les utilisateurs. Une fois la restauration terminée, SQL Server PDW redémarre les services de l’appliance.  
  
![Restore master PDW des appliances DWConfig](./media/restore-the-master-database/SQL_Server_PDW_DWConfig_ApplPDWRestore.png "SQL_Server_PDW_DWConfig_ApplPDWRestore")  
  
