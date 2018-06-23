---
title: Microsoft SQL Server Reporting Services Service partagé SharePoint est installé côte à côte (conseiller) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6ae1017e-129b-4702-9ea7-00ac9b024062
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 79f07ede92ee840ed50631c10d22bf4b015cf29b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043078"
---
# <a name="microsoft-sql-server-reporting-services-sharepoint-shared-service-is-installed-side-by-side-upgrade-advisor"></a>Le service partagé SharePoint Microsoft SQL Server Reporting Services est installé côte à côte (Conseiller de mise à niveau)
  A détecté le Conseiller de mise à niveau [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service partagé SharePoint est installé côte à côte avec une version antérieure de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Mode SharePoint.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 A détecté le Conseiller de mise à niveau [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service partagé SharePoint est installé côte à côte avec une version antérieure de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui n’est pas basé sur l’architecture de service partagé SharePoint. Parce que des technologies [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint anciennes et nouvelles sont installées côte à côte sur l'ordinateur, la mise à niveau est bloquée.  
  
## <a name="corrective-action"></a>Action corrective  
 Pour continuer la mise à niveau, vous devez désinstaller une des installations existantes de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Après avoir supprimé une des installations de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], relancez le Conseiller de mise à niveau pour confirmer qu'il n'y a pas d'autre problèmes de mise à niveau.  
  
  