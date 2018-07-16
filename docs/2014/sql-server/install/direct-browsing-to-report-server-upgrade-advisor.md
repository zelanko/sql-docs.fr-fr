---
title: Accès direct au serveur de rapports (Conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3d2814a4-318a-45ed-b093-1e852fab561f
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 482fc74e08a60ed7f4d81a450a680c43a9815d5a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196679"
---
# <a name="direct-browsing-to-report-server-upgrade-advisor"></a>Accès direct au serveur de rapports (Conseiller de mise à niveau)
  Conseiller de mise à niveau a détecté l’installation actuelle de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] accède directement au répertoire virtuel du serveur de rapports.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Mode SharePoint.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Conseiller de mise à niveau a détecté l’installation actuelle de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] accède directement au rapport répertoire virtuel du serveur, par exemple **http://\<nom du serveur > / ReportServer**. Non pris en charge dans les versions actuelles de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  Cette règle est un avertissement et la mise à jour n'est pas bloquée.  
  
## <a name="corrective-action"></a>Action corrective  
 Accédez à l’aide de l’interface utilisateur SharePoint pour les bibliothèques de documents ou utilisez **http://\<nom du serveur > / site sharepoint >/_vti_bin/reportserver**.  
  
  
