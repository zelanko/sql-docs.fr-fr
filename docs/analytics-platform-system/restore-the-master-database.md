---
title: "Restaurer la base de données Master (système de plateforme Analytique)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7870021a-0d89-422e-b8ea-1cc95b45c139
caps.latest.revision: "11"
ms.openlocfilehash: b82ef65734b6953c085436d5322e7bf42ef979b4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="restore-the-master-database"></a>Restaurer la base de données Master
Le **Restore Master** page du Gestionnaire de Configuration PDW SQL Server vous permet de restaurer la base de données master à partir d’une sauvegarde.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
> [!IMPORTANT]  
> Pour effectuer la restauration, SQL Server PDW doit supprimer la base de données principale actuelle, qui contient les informations de sécurité d’utilisateur et le catalogue de base de données. Nous vous recommandons d’effectuer une sauvegarde de la base de données principale actuelle avant d’effectuer la restauration.  
  
## <a name="to-restore-the-master-database"></a>Pour restaurer la base de données master  
  
1.  Lancez le Gestionnaire de Configuration. Pour plus d’informations, consultez [lance le Gestionnaire de Configuration &#40; Système de plateforme Analytique &#41; ](launch-the-configuration-manager.md).  
  
2.  Dans le volet gauche du Gestionnaire de Configuration, cliquez sur **Restore Master**.  
  
3.  Sélectionnez la sauvegarde de master à restaurer.  
  
4.  Cliquez sur **Appliquer**.  
  
5.  Pour effectuer la restauration, SQL Server PDW s’arrêter tous les services d’application et déconnecter tous les utilisateurs. Une fois la restauration terminée, SQL Server PDW redémarre les services d’application.  
  
![DWConfig Appliance Restore master PDW](./media/restore-the-master-database/SQL_Server_PDW_DWConfig_ApplPDWRestore.png "SQL_Server_PDW_DWConfig_ApplPDWRestore")  
  
