---
title: Base de données du serveur de rapports n’est pas configurée (Conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: b964300c-b220-4244-9fa6-c0c6a57760f6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 813319309e489943cfdd94e13f300990b72e94be
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66092721"
---
# <a name="report-server-database-is-not-configured-upgrade-advisor"></a>La base de données du serveur de rapports n'est pas configurée (Conseiller de mise à niveau)
  La mise à niveau est bloquée en raison d'une configuration incomplète du serveur de rapports. La base de données du serveur de rapports n'est pas configurée.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Le programme d'installation peut uniquement mettre à niveau une instance du serveur de rapports entièrement configurée. Pour continuer, vous devez configurer la base de données de serveur de rapports, ou utiliser Microsoft Windows **le panneau de configuration** pour supprimer la fonctionnalité de serveur de rapports à partir de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation. Après avoir supprimé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous pouvez mettre à niveau d'autres composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="corrective-action"></a>Action corrective  
 Si vous n'avez pas configuré la base de données du serveur de rapports, celui-ci n'est pas opérationnel et doit être supprimé avant la mise à niveau.  
  
 Pour plus d’informations sur la désinstallation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , consultez [désinstaller Reporting Services 2012](https://technet.microsoft.com/library/hh479745.aspx\(v=sql.11\)). La rubrique explique comment désinstaller une version spécifique, les procédures des versions antérieures étant similaires.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Reporting Services &#40;Conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
