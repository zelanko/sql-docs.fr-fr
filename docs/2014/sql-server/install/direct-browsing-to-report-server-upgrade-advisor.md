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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952213"
---
# <a name="direct-browsing-to-report-server-upgrade-advisor"></a>Accès direct au serveur de rapports (Conseiller de mise à niveau)
  Le conseiller de mise à niveau a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] détecté que votre installation actuelle de accède directement au répertoire virtuel du serveur de rapports.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Mode SharePoint.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Le conseiller de mise à niveau a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] détecté que votre installation actuelle de accède directement au répertoire virtuel du serveur de rapports, par exemple **http://\<Server Name>/ReportServer**. Non pris en charge dans les versions actuelles de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  Cette règle est un avertissement et la mise à jour n'est pas bloquée.  
  
## <a name="corrective-action"></a>Action corrective  
 Parcourez l’interface utilisateur SharePoint pour les bibliothèques de documents ou utilisez le **nom du serveur http://\<>>/SharePoint/_vti_bin/ReportServer**.  
  
  
