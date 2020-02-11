---
title: La base de données du serveur de rapports n’est pas configurée (conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: b964300c-b220-4244-9fa6-c0c6a57760f6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: bb5dd5968930319532a29ff7c3909c36af99b3a0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952107"
---
# <a name="report-server-database-is-not-configured-upgrade-advisor"></a>La base de données du serveur de rapports n'est pas configurée (Conseiller de mise à niveau)
  La mise à niveau est bloquée en raison d'une configuration incomplète du serveur de rapports. La base de données du serveur de rapports n'est pas configurée.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Mode natif &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] le mode SharePoint.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Le programme d'installation peut uniquement mettre à niveau une instance du serveur de rapports entièrement configurée. Pour continuer, vous devez soit configurer la base de données du serveur de rapports, soit utiliser le **panneau de configuration** Microsoft Windows pour supprimer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la fonctionnalité de serveur de rapports de l’installation. Après avoir supprimé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous pouvez mettre à niveau d'autres composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="corrective-action"></a>Action corrective  
 Si vous n'avez pas configuré la base de données du serveur de rapports, celui-ci n'est pas opérationnel et doit être supprimé avant la mise à niveau.  
  
 Pour plus d’informations sur la désinstallation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , consultez [désinstaller Reporting Services 2012](https://technet.microsoft.com/library/hh479745.aspx\(v=sql.11\)). La rubrique explique comment désinstaller une version spécifique, les procédures des versions antérieures étant similaires.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau de Reporting Services &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
