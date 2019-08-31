---
title: Restauration d’une base de données Master-système de plateforme d’analyse (APS) | Microsoft Docs
description: Restaurez la base de données Master dans Analytics Platform System (APS).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 624e1199fb953945ae6476a1f935dded48508bab
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176138"
---
# <a name="restore-the-master-database-in-analytics-platform-system-aps"></a>Restaurer la base de données Master dans Analytics Platform System (APS)
La page maître de la **restauration** de la SQL Server PDW Configuration Manager vous permet de restaurer la base de données Master à partir d’une sauvegarde.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
> [!IMPORTANT]  
> Pour effectuer la restauration, SQL Server PDW devez supprimer la base de données Master active, qui contient les informations de sécurité de l’utilisateur et le catalogue de la base de données. Nous vous recommandons d’effectuer une sauvegarde de la base de données Master en cours avant d’effectuer la restauration.  
  
## <a name="to-restore-the-master-database"></a>Pour restaurer la base de données master  
  
1.  Lancez le Configuration Manager. Pour plus d’informations, consultez [lancer le &#40;système&#41;de plateforme Configuration Manager Analytics](launch-the-configuration-manager.md).  
  
2.  Dans le volet gauche de la Configuration Manager, cliquez sur **restaurer la base**de référence.  
  
3.  Sélectionnez la sauvegarde principale à restaurer.  
  
4.  Cliquez sur **Appliquer**.  
  
5.  Pour effectuer la restauration, SQL Server PDW arrête tous les services d’appliance et déconnecte tous les utilisateurs. Une fois la restauration terminée, SQL Server PDW redémarre les services de l’appliance.  
  
![Maître de restauration PDW d’appliance DWConfig](./media/restore-the-master-database/SQL_Server_PDW_DWConfig_ApplPDWRestore.png "SQL_Server_PDW_DWConfig_ApplPDWRestore")  
  
