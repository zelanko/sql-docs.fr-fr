---
title: Navigation directe vers le serveur de rapports (conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3d2814a4-318a-45ed-b093-1e852fab561f
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 6945828b2eba829c32d717c13393c9fbda4fc43e
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952213"
---
# <a name="direct-browsing-to-report-server-upgrade-advisor"></a>Accès direct au serveur de rapports (Conseiller de mise à niveau)
  Le conseiller de mise à niveau a détecté votre installation actuelle de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] accède directement au répertoire virtuel du serveur de rapports.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mode SharePoint.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Le conseiller de mise à niveau a détecté votre installation actuelle de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] accède directement au répertoire virtuel du serveur de rapports, par exemple **http://\<server nom >/ReportServer**. Non pris en charge dans les versions actuelles de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  Cette règle est un avertissement et la mise à jour n'est pas bloquée.  
  
## <a name="corrective-action"></a>Action corrective  
 Parcourez l’interface utilisateur SharePoint pour les bibliothèques de documents ou utilisez **http://\<server name >/SharePoint site >/_vti_bin/ReportServer**.  
  
  
