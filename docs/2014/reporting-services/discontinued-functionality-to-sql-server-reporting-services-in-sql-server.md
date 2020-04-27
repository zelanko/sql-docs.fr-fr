---
title: Fonctionnalités supprimées
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: 14a5a6e38d4c9fcf306436374d80dd1c1c08b27e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67413042"
---
# <a name="discontinued-functionality-in-sql-server-reporting-services-ssrs"></a>Fonctionnalités supprimées dans SQL Server Reporting Services (SSRS)

  Cette rubrique décrit les fonctionnalités de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] qui ne sont plus disponibles dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Elle n'inclut pas les annonces relatives à la cessation de la prise en charge pour des versions spécifiques du système d'exploitation ou de [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Services (IIS). Pour plus d’informations sur la configuration système requise, consultez [configurations matérielle et logicielle requises pour l’installation de SQL Server 2014](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
 Dans cette rubrique :  
  
- [SQL Server 2014 Reporting Services fonctionnalité abandonnée](#bkmk_sql14)  
  
- [Fonctionnalités supprimées dans SQL Server 2012 Reporting Services](#bkmk_rc0)  
  
- [Fonctionnalités supprimées dans SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="sssql14-reporting-services-discontinued-functionality"></a><a name="bkmk_sql14"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services les fonctionnalités supprimées

 Aucune fonctionnalité [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] n'a été supprimée dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
##  <a name="sssql11-reporting-services-discontinued-functionality"></a><a name="bkmk_rc0"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services les fonctionnalités supprimées

 Cette section décrit les fonctionnalités [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] supprimées dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
 Aucune fonctionnalité [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] n'a été supprimée dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
##  <a name="sql-server-2008-r2-reporting-services-discontinued-functionality"></a><a name="bkmk_kj"></a>SQL Server 2008 R2 Reporting Services fonctionnalité abandonnée

 Cette section décrit les fonctionnalités supprimées [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]dans.  
  
> [!NOTE]  
> SQL Server 2008 R2 étant une mise à niveau de version secondaire de SQL Server 2008, nous vous recommandons d'examiner également le contenu de la section SQL Server 2008.
  
### <a name="64-bit-platform-support"></a>Support de plate-forme 64 bits

 À partir de [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], le composant [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne prend plus en charge les serveurs Itanium qui exécutent Windows Server 2003 ou Windows Server 2003 R2. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]continue à prendre en charge d’autres systèmes d’exploitation 64 bits, y compris Windows Server 2008 pour les systèmes Itanium et les WINDOWS SERVER 2008 R2 pour les systèmes Itanium. Pour effectuer une mise à niveau vers [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] à partir d’une installation [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] avec [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sur une édition de système Itanium de Windows Server 2003 ou Windows Server 2003 R2, vous devez commencer par mettre à niveau le système d’exploitation.  
  
### <a name="data-source-credentials-in-url-access"></a>Informations d'identification de la source de données dans l'accès URL

 Les chaînes de paramètres d'accès URL *dsu:datasourcename=value* et *dsp:datasourcename=value* ont été supprimées. Dans les versions antérieures, ces chaînes de paramètres sont stockées en texte brut dans le cache de navigateur, ce qui n'est pas sécurisé.  
  
## <a name="next-steps"></a>Étapes suivantes

 - [Nouveautés &#40;Reporting Services&#41;](what-s-new-reporting-services.md)
 - [Changements de comportement apportés à SQL Server Reporting Services dans SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)
 - [Fonctions déconseillées dans SQL Server Reporting Services dans SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)