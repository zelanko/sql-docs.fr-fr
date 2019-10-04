---
title: Microsoft SQL Server Reporting Services service partagé SharePoint est installé côte à côte (conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6ae1017e-129b-4702-9ea7-00ac9b024062
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 529e07dc7beed8dc37741f6c9dab0b0b080d4898
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952692"
---
# <a name="microsoft-sql-server-reporting-services-sharepoint-shared-service-is-installed-side-by-side-upgrade-advisor"></a>Le service partagé SharePoint Microsoft SQL Server Reporting Services est installé côte à côte (Conseiller de mise à niveau)
  Le conseiller de mise à niveau a détecté [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] le service partagé SharePoint est installé côte à côte avec une version précédente de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mode SharePoint.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Le conseiller de mise à niveau a détecté [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] le service partagé SharePoint est installé côte à côte avec une version précédente de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui n’est pas basée sur l’architecture de service partagé SharePoint. Parce que des technologies [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint anciennes et nouvelles sont installées côte à côte sur l'ordinateur, la mise à niveau est bloquée.  
  
## <a name="corrective-action"></a>Action corrective  
 Pour continuer la mise à niveau, vous devez désinstaller une des installations existantes de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Après avoir supprimé une des installations de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], relancez le Conseiller de mise à niveau pour confirmer qu'il n'y a pas d'autre problèmes de mise à niveau.  
  
  
