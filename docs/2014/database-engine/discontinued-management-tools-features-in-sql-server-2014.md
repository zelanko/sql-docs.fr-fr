---
title: Supprimées de fonctionnalités dans SQL Server 2014 des outils d’administration | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 6e58acd0-73c5-4161-9fbc-8ea531bc681c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7c966c3e4388588810438d7e91a9ae0356ef60c3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48068389"
---
# <a name="discontinued-management-tools-features-in-sql-server-2014"></a>Fonctionnalités des outils d'administration supprimées dans SQL Server 2014
  Cette rubrique décrit les fonctionnalités des outils de gestion [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui ne sont plus disponibles dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="features-removed-in-includesscurrentincludessscurrent-mdmd"></a>Fonctionnalités supprimées dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 None  
  
## <a name="features-removed-in-includesssql11includessssql11-mdmd"></a>Fonctionnalités supprimées dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="sql-server-compact-edition"></a>SQL Server Compact Edition  
 L'éditeur de code SQL Server Compact Edition a été supprimé de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. La prise en charge de SQL Server Compact Edition a également été supprimée de l'Explorateur d'objets, de l'Explorateur de solutions et de l'Explorateur de modèles. Utilisez à la place les éditeurs Transact-SQL dans Service Pack 1 de Microsoft Visual Studio 2010 ou Webmatrix.  
  
### <a name="activex-subsystem-for-sql-server-agent"></a>Sous-système ActiveX de SQL Server Agent  
 Le sous-système ActiveX de SQL Server Agent a été supprimé de cette version. Il n'existe aucune fonctionnalité de remplacement.  
  
### <a name="spaddtask-spdeletetask-spupdatetask"></a>sp_addtask, sp_deletetask, sp_updatetask  
 Sp_addtask, sp_deletetask et sp_updatetask ont été supprimées de cette version. N'utilisez pas cette fonctionnalité dans les applications, qu'elles soient nouvelles ou mises à jour.  
  
### <a name="net-send-and-pager-notification"></a>Envoi réseau et notification de radiomessagerie  
 Envoi réseau et notification de radiomessagerie ont été supprimées de cette version. N'utilisez pas cette fonctionnalité dans les applications, qu'elles soient nouvelles ou mises à jour.  
  
### <a name="data-tier-applications"></a>Applications de la couche Données  
 Certaines fonctionnalités d'une application de la couche Données (DAC) présentes dans [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] ont été supprimées dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]. Toutefois, l'Infrastructure d'application de la couche Données (DACfx version 3.0) fournie avec [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] est compatible avec [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] jusqu'à [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] et avec [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)]. DAC version 3.0 n'est pas pris en charge dans les versions antérieures de [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] y compris [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] dans [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]. Les projets de base de données Visual Studio 2010 ne prennent pas en charge les packages DACPAC DAC 3.0 ni les packages d'exportation DAC (BACPAC) générés avec DACfx version 3.0 ou ultérieure.  
  
 Microsoft recommande l'utilisation de la dernière version disponible des projets de base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools.  
  
 L'API DACfx 3.0 et les outils [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] prennent en charge la lecture de fichiers DACPAC et BACPAC créés dans les versions précédentes des outils [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et de DACfx ; l'extraction de bases de données dans des fichiers DACPAC à partir de ces versions et le déploiement de bases de données dans les versions prises en charge de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] ou de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools.  
  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité descendante](../../2014/getting-started/backward-compatibility.md)  
  
  
