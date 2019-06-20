---
title: Restaurer la base de données master - Analytique Platform System | Microsoft Docs
description: Restaurer la base de données master d’Analytique Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 184184f332225e76e152c2d909cfff788b4fea91
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62678428"
---
# <a name="restore-the-master-database-in-analytics-platform-system"></a>Restaurer la base de données master d’Analytique Platform System
Le **Restore Master** page du Gestionnaire de Configuration PDW SQL Server vous permet de restaurer la base de données master à partir d’une sauvegarde.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
> [!IMPORTANT]  
> Pour effectuer la restauration, SQL Server PDW doit supprimer la base de données master actuelle, qui contient les informations de sécurité d’utilisateur et le catalogue de base de données. Nous vous recommandons d’effectuer une sauvegarde de la base de données master actuelle avant d’effectuer la restauration.  
  
## <a name="to-restore-the-master-database"></a>Pour restaurer la base de données master  
  
1.  Lancez le Gestionnaire de Configuration. Pour plus d’informations, consultez [lancer le Gestionnaire de Configuration &#40;Analytique Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Dans le volet gauche du Gestionnaire de Configuration, cliquez sur **Restore Master**.  
  
3.  Sélectionnez la sauvegarde de master à restaurer.  
  
4.  Cliquez sur **Appliquer**.  
  
5.  Pour effectuer la restauration, SQL Server PDW arrête de tous les services d’appliance et déconnectez tous les utilisateurs. Une fois la restauration terminée, SQL Server PDW redémarre les services de l’appliance.  
  
![DWConfig Appliance Restore master PDW](./media/restore-the-master-database/SQL_Server_PDW_DWConfig_ApplPDWRestore.png "SQL_Server_PDW_DWConfig_ApplPDWRestore")  
  
