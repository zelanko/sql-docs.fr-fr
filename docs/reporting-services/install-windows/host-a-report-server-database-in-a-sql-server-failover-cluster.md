---
title: "Héberger une base de données du serveur de rapports dans un Cluster de basculement SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 03/30/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7bd5f019-2857-452f-a023-cc3b9e93aec4
caps.latest.revision: 5
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b14768db398059289f280ca610c8b93ca95c468f
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="host-a-report-server-database-in-a-sql-server-failover-cluster"></a>Héberger une base de données du serveur de rapports dans un cluster de basculement SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]fournit le clustering de basculement prise en charge afin que vous puissiez utiliser plusieurs disques pour un ou plusieurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances. Le clustering de basculement est assuré uniquement pour la base de données du serveur de rapports : vous ne pouvez pas exécuter le service Report Server dans le cadre d'un cluster de basculement.  
  
 Pour que vous puissiez héberger une base de données de serveur de rapports sur un cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le cluster doit avoir été préalablement installé et configuré. Vous pouvez alors sélectionner le cluster de basculement comme nom du serveur lorsque vous créez la base de données du serveur de rapports dans la page Installation de la base de données de l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Bien que le service Report Server ne puisse pas faire partie d'un environnement de cluster de basculement, vous pouvez installer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur un ordinateur sur lequel un cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé. Le serveur de rapports s'exécute indépendamment du cluster de basculement. Si vous installez un serveur de rapports sur un ordinateur appartenant à une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous n'êtes pas obligé d'utiliser le cluster de basculement pour la base de données du serveur de rapports ; vous pouvez recourir à une autre instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour héberger la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Base de données du serveur de rapports &#40; En Mode natif de SSRS &#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
 [Créer une base de données du serveur de rapports &#40; Gestionnaire de Configuration de SSRS &#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-report-server-database.md)  
  
  

