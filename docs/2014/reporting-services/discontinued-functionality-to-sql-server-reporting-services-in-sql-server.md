---
title: Fonctionnalités de SQL Server Reporting Services dans SQL Server 2014 supprimées | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- discontinued functionality [Reporting Services]
- Reporting Services, backward compatibility
- Rsactivate.exe
- unsupported features [Reporting Services]
ms.assetid: d529cc96-3483-480b-9bfc-bd28b1d0ef52
caps.latest.revision: 47
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 627e8fe70de053c0cd53cc24c77438549c794e76
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139751"
---
# <a name="discontinued-functionality-to-sql-server-reporting-services-in-sql-server-2014"></a>Fonctionnalités supprimées dans SQL Server Reporting Services dans SQL Server 2014
  Cette rubrique décrit les fonctionnalités de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] qui ne sont plus disponibles dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Elle n'inclut pas les annonces relatives à la cessation de la prise en charge pour des versions spécifiques du système d'exploitation ou de [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Services (IIS). Pour plus d’informations sur la configuration système requise, consultez [matérielle et logicielle requise pour l’installation de SQL Server 2014](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
 Dans cette rubrique :  
  
-   [SQL Server 2014 Reporting Services fonctionnalités supprimées](#bkmk_sql14)  
  
-   [SQL Server 2012 Reporting Services fonctionnalités supprimées](#bkmk_rc0)  
  
-   [SQL Server 2008 R2 Reporting Services fonctionnalités supprimées](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services fonctionnalités supprimées  
 Aucune fonctionnalité [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] n'a été supprimée dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
##  <a name="bkmk_rc0"></a> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services fonctionnalités supprimées  
 Cette section décrit les fonctionnalités [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] supprimées dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
 Aucune fonctionnalité [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] n'a été supprimée dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
##  <a name="bkmk_kj"></a> SQL Server 2008 R2 Reporting Services fonctionnalités supprimées  
 Cette section décrit abandonnées dans [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  SQL Server 2008 R2 étant une mise à niveau de version secondaire de SQL Server 2008, nous vous recommandons d'examiner également le contenu de la section SQL Server 2008.  
  
### <a name="64-bit-platform-support"></a>Support de plate-forme 64 bits  
 À compter de [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] composant n’est plus prise en charge que les serveurs basés sur Itanium exécutant Windows Server 2003 ou Windows Server 2003 R2. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] continue à prendre en charge d’autres systèmes d’exploitation 64 bits, y compris Windows Server 2008 pour systèmes Itanium et Windows Server 2008 R2 pour les systèmes Itanium. Pour effectuer une mise à niveau vers [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] à partir d'une installation [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] avec [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sur une édition de système Itanium de Windows Server 2003 ou Windows Server 2003 R2, vous devez commencer par mettre à niveau le système d'exploitation.  
  
### <a name="data-source-credentials-in-url-access"></a>Informations d'identification de la source de données dans l'accès URL  
 Les chaînes de paramètres d'accès URL *dsu:datasourcename=value* et *dsp:datasourcename=value* ont été supprimées. Dans les versions antérieures, ces chaînes de paramètres sont stockées en texte brut dans le cache de navigateur, ce qui n'est pas sécurisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles sont les nouveautés &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Changements de comportement SQL Server Reporting Services dans SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [Fonctionnalités déconseillées dans SQL Server Reporting Services dans SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)  
  
  