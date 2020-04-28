---
title: Microsoft SharePoint 2007 est installé (conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6f1da295-d9b7-4948-99d3-ebd3587337c6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 84672ddf6a9b2912f3d53eef8d40727369376ba5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "71952091"
---
# <a name="microsoft-sharepoint-2007-is-installed-upgrade-advisor"></a>Microsoft SharePoint 2007 installé (Conseiller de mise à niveau)
  Le Conseiller de mise à niveau a détecté une version non prise en charge d'un produit ou d'une technologie SharePoint.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Mode SharePoint.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne sera pas mis à niveau ou installé sur SharePoint 2007. La mise à niveau est bloquée.  
  
## <a name="corrective-action"></a>Action corrective  
 Pour continuer la mise à niveau, vous devez désinstaller SharePoint 2007 ou procéder à la mise à niveau de SharePoint 2007 vers un produit SharePoint 2010. Une fois votre installation de SharePoint mise à jour, relancez le Conseiller de mise à niveau pour confirmer qu'il n'y a pas d'autre problèmes de mise à niveau.  
  
 Il n'est pas possible de mettre directement à niveau SharePoint 2007 vers SharePoint 2013. mais vous pouvez faire ce que l’on appelle une attachement de base de données « double saut » pour effectuer une mise à niveau d’Office SharePoint Server 2007 vers SharePoint Server 2010, puis de SharePoint Server 2010 vers SharePoint Server 2013.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau de Reporting Services &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
