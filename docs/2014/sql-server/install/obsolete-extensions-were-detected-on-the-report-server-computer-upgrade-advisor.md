---
title: Extensions obsolètes ont été détectées sur le serveur de rapports (Conseiller de mise à niveau) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 40d245a2-0631-470e-81b3-1feb47e028cb
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: f1bbf0f40fd78f7372ee7b332e9eaa89fb97cff2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051851"
---
# <a name="obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor"></a>Des extensions obsolètes ont été détectées sur l'ordinateur serveur de rapports (Conseiller de mise à niveau)
  Le Conseiller de mise à niveau a détecté une ou plusieurs extensions de rendu qui ne sont plus disponibles dans la version actuelle.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Le serveur de rapports est configuré pour utiliser une ou plusieurs extensions qui ne sont plus disponibles dans cette version. Les extensions supprimées sont les suivantes :  
  
-   Extension de rendu HTML OWC  
  
-   Extension de rendu HTML 3.2  
  
 La mise à niveau peut continuer, mais les fonctionnalités non prises en charge ne seront plus disponibles sur le serveur de rapports mis à niveau.  
  
 Si vous avez besoin de ces extensions, n'effectuez pas de mise à niveau avant d'avoir trouvé une solution de remplacement répondant à vos besoins. Il vous faudra peut-être obtenir ou générer une extension de rendu personnalisée qui fournit des fonctionnalités identiques ou semblables.  
  
## <a name="corrective-action"></a>Action corrective  
 Évaluez le jeu de fonctionnalités actuel inclus dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour déterminer si les fonctionnalités prises en charge répondent à vos besoins.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Reporting Services &#40;le Conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  