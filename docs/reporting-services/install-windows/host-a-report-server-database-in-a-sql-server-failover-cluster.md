---
title: Héberger une base de données du serveur de rapports dans un cluster de basculement SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7bd5f019-2857-452f-a023-cc3b9e93aec4
caps.latest.revision: 5
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 813a16c58fc592cf525831a1d461ca036f3a4649
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35322188"
---
# <a name="host-a-report-server-database-in-a-sql-server-failover-cluster"></a>Héberger une base de données du serveur de rapports dans un cluster de basculement SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge le clustering de basculement afin que vous puissiez utiliser plusieurs disques pour une ou plusieurs instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le clustering de basculement est assuré uniquement pour la base de données du serveur de rapports : vous ne pouvez pas exécuter le service Report Server dans le cadre d'un cluster de basculement.  
  
 Pour que vous puissiez héberger une base de données de serveur de rapports sur un cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le cluster doit avoir été préalablement installé et configuré. Vous pouvez alors sélectionner le cluster de basculement comme nom du serveur lorsque vous créez la base de données du serveur de rapports dans la page Installation de la base de données de l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Bien que le service Report Server ne puisse pas faire partie d'un environnement de cluster de basculement, vous pouvez installer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur un ordinateur sur lequel un cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé. Le serveur de rapports s'exécute indépendamment du cluster de basculement. Si vous installez un serveur de rapports sur un ordinateur appartenant à une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous n'êtes pas obligé d'utiliser le cluster de basculement pour la base de données du serveur de rapports ; vous pouvez recourir à une autre instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour héberger la base de données.  
  
## <a name="see-also"></a> Voir aussi  
 [Base de données du serveur de rapports &#40;SSRS en mode natif&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
 [Créer une base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-report-server-database.md)  
  
  
