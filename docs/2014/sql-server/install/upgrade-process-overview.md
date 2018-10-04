---
title: Vue d’ensemble du processus de mise à niveau | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server
- Upgrade Advisor [SQL Server], process description
- SQL Server Upgrade Advisor, process description
- upgrade process [Upgrade Advisor]
ms.assetid: f77ffbab-a195-4124-acce-9c538f7ca9ce
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e95a30c813ad2d72313a0e470136d650ea9686a0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48207159"
---
# <a name="upgrade-process-overview"></a>Vue d'ensemble du processus de mise à niveau
  Cette rubrique fournit des informations sur les meilleures pratiques concernant le Conseiller de mise à niveau [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et un résumé du processus recommandé pour effectuer une mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="upgrade-process"></a>Processus de mise à niveau  
 Les serveurs qui exécutent [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] peuvent être mis à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Alors que certains composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent être mis à niveau sur place, d'autres doivent être migrés et d'autres encore ont été remplacés par de nouveaux composants. Par exemple, depuis [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) remplace les services DTS (Data Transformation Services) et DTS n'est plus pris en charge dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Lorsque vous formulez votre plan de mise à niveau, vous devez peut-être planifier la mise à jour de vos packages DTS actuels en packages [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 Le Conseiller de mise à niveau vous permet d'évaluer les installations, les composants et les fichiers connexes actuels de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour identifier les problèmes connus qui pourront éventuellement se manifester pendant ou après la mise à niveau ou la migration vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Quelques-unes de ces problèmes connus bloquent la [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mise à niveau. Dans le rapport du Conseiller de mise à niveau, ces problèmes sont identifiés comme des blocages de la mise à niveau. Si vous n'avez pas traité les blocages de mise à niveau avant d'exécuter le programme d'installation, le programme d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] se ferme et vous recommande d'exécuter le Conseiller de mise à niveau pour identifier les problèmes spécifiques qui bloquent la mise à niveau.  
  
 Avant d'effectuer la mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], nous vous recommandons de sauvegarder vos données et paramètres système et de prendre les mesures stratégiques répertoriées dans les instructions opérationnelles définies pour votre organisation. Exécutez les opérations suivantes pour réaliser la mise à niveau :  
  
1.  Consultez [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).  
  
2.  Sauvegardez les données et les paramètres système.  
  
3.  Exécutez le Conseiller de mise à niveau.  
  
     Le Conseiller de mise à niveau ne modifie pas vos données ni vos paramètres sur votre ordinateur.  
  
4.  Examinez les problèmes identifiés dans le rapport du Conseiller de mise à niveau.  
  
5.  Résolvez tous les problèmes de blocage qui vous empêcheraient d'effectuer la mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
6.  Résolvez tous les autres problèmes antérieurs à la mise à niveau.  
  
7.  Exécutez le Conseiller de mise à niveau pour vérifier que tous les problèmes connus ont été traités.  
  
8.  Exécutez le programme d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
9. Résolvez tous les problèmes postérieurs à la mise à niveau et à la migration.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécutez le Conseiller de mise à niveau &#40;Interface utilisateur&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)   
 [À l’aide de rapports](../../../2014/sql-server/install/using-reports.md)   
 [Utilisation du Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
