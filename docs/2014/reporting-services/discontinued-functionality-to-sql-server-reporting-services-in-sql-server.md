---
title: Fonctionnalités supprimées de SQL Server Reporting Services dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- discontinued functionality [Reporting Services]
- Reporting Services, backward compatibility
- Rsactivate.exe
- unsupported features [Reporting Services]
ms.assetid: d529cc96-3483-480b-9bfc-bd28b1d0ef52
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ec97f47c87abed0a3fd650632458bf4ba956e985
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48100219"
---
# <a name="discontinued-functionality-to-sql-server-reporting-services-in-sql-server-2014"></a>Fonctionnalités supprimées dans SQL Server Reporting Services dans SQL Server 2014
  Cette rubrique décrit les fonctionnalités de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] qui ne sont plus disponibles dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Elle n'inclut pas les annonces relatives à la cessation de la prise en charge pour des versions spécifiques du système d'exploitation ou de [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Services (IIS). Pour plus d’informations sur la configuration système requise, consultez [Hardware and Software Requirements for Installing SQL Server 2014](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
 Dans cette rubrique :  
  
-   [Fonctionnalités supprimées dans SQL Server 2014 Reporting Services](#bkmk_sql14)  
  
-   [Fonctionnalités supprimées dans SQL Server 2012 Reporting Services](#bkmk_rc0)  
  
-   [Fonctionnalités supprimées dans SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Fonctionnalités supprimées dans Reporting Services  
 Aucune fonctionnalité [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] n'a été supprimée dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
##  <a name="bkmk_rc0"></a> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Fonctionnalités supprimées dans Reporting Services  
 Cette section décrit les fonctionnalités [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] supprimées dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
 Aucune fonctionnalité [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] n'a été supprimée dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
##  <a name="bkmk_kj"></a> Fonctionnalités supprimées dans SQL Server 2008 R2 Reporting Services  
 Cette section décrit les fonctionnalités supprimées dans [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  SQL Server 2008 R2 étant une mise à niveau de version secondaire de SQL Server 2008, nous vous recommandons d'examiner également le contenu de la section SQL Server 2008.  
  
### <a name="64-bit-platform-support"></a>Support de plate-forme 64 bits  
 À compter de [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] composant n’est plus prend en charge que les serveurs Itanium qui exécutent Windows Server 2003 ou Windows Server 2003 R2. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] continue à prendre en charge d’autres systèmes d’exploitation 64 bits, y compris Windows Server 2008 pour systèmes Itanium et Windows Server 2008 R2 pour les systèmes Itanium. Pour effectuer une mise à niveau vers [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] à partir d'une installation [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] avec [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sur une édition de système Itanium de Windows Server 2003 ou Windows Server 2003 R2, vous devez commencer par mettre à niveau le système d'exploitation.  
  
### <a name="data-source-credentials-in-url-access"></a>Informations d'identification de la source de données dans l'accès URL  
 Les chaînes de paramètres d'accès URL *dsu:datasourcename=value* et *dsp:datasourcename=value* ont été supprimées. Dans les versions antérieures, ces chaînes de paramètres sont stockées en texte brut dans le cache de navigateur, ce qui n'est pas sécurisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles sont les nouveautés &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Changements de comportement apportés à SQL Server Reporting Services dans SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [Fonctions dépréciées de SQL Server Reporting Services dans SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)  
  
  
