---
title: Éléments de rapport personnalisés ont été détectées sur le serveur de rapports (Conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- custom report items, upgrading
ms.assetid: aee32006-65b2-4dfe-9570-d85a249d17b2
caps.latest.revision: 14
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2f7548a78ebbb4d7d01f8bfb9e796d32a9b3b28d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261905"
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
  
  
