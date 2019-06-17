---
title: Éléments de rapport personnalisés ont été détectées sur le serveur de rapports (Conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- custom report items, upgrading
ms.assetid: aee32006-65b2-4dfe-9570-d85a249d17b2
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 778f626e64bdacb3eff57f20f749d24628baaec2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66095930"
---
# <a name="custom-report-items-were-detected-on-the-report-server-upgrade-advisor"></a>Des éléments de rapport personnalisés ont été détectés sur le serveur de rapports (Conseiller de mise à niveau)
  Les éléments de rapport personnalisés qui ont été créés pour les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne sont pas compatibles avec [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. La mise à niveau peut continuer, mais les rapports qui utilisent des éléments de rapport personnalisés ne s'exécuteront pas comme prévu. Le Conseiller de mise à niveau a détecté des éléments de rapport personnalisés. La mise à niveau peut continuer, mais vous devez déplacer manuellement les fichiers des éléments de rapport personnalisés vers le nouveau dossier d'installation une fois la mise à niveau terminée.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Le Conseiller de mise à niveau a détecté des paramètres d'extension [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] personnalisés dans les fichiers de configuration, qui indiquent que votre installation inclut un ou plusieurs assemblys personnalisés pour les rapports.  
  
## <a name="corrective-action"></a>Action corrective  
 Une fois la mise à niveau terminée, déplacez manuellement les fichiers des éléments de rapport personnalisés vers le nouveau dossier d'installation.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Reporting Services &#40;Conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
